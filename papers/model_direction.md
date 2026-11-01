# 模型改进方案：可靠性门控的节点知识（2026-11-01）

> 第一版实现与沙盒结果（合成数据、FeederBW 40 条馈线）见 [`model_sandbox.md`](model_sandbox.md)：KCD 是最强、最稳的模块；门控在合成数据上接近 oracle，在真实数据上没有代价；NKE 的收益取决于身份缺口。

背景：只在一个数据集上做预测不足以支撑论文，需要模型层面的改进。本文件把已有发现（身份嵌入、Traffic 漂移传感器、FeederBW 台账先导）归纳成一个跨数据集的问题，提出由三个模块组成的模型，并逐个模块查重，给出多数据集、多骨干的实验设计。数据与先导实验见 [`application_direction.md`](application_direction.md)，推导见 [`theory.md`](theory.md)、[`theory_directions.md`](theory_directions.md)。文献细节来自全文（标注"全文"）或摘要（标注"摘要"），引用前请再核对原文。

## 结论

**问题**：多节点预测（馈线、建筑、用户、交通传感器）中，模型对"某一个节点"的知识能显著降低误差，但这些知识**会过时**（节点发生变化时反而有害），而且**对新节点不可用**。

这里的节点知识包括：
- 学到的身份；
- 节点的描述信息（台账、元数据），可能随时间变化；
- 节点对协变量（天气、日历）的敏感度。

现有模型处在两个极端：
- **一直相信**：STID、STAEformer、通道归一化 CN、CycleNet，以及我们的身份嵌入；
- **从不使用**：通道独立模型、时间序列基础模型、CPiRi 这类置换不变的模型。

**模型**：在全局骨干上加三个模块（暂称"可靠性门控的节点知识"，Reliability-gated Node Knowledge，RNK）：
1. **归纳式节点知识编码器（NKE）**：由描述信息和节点自身的近期画像生成节点知识，再加一个零初始化的残差身份。新节点可用，节点变化后能随之更新。
2. **知识条件的协变量一致分解（KCD）**：节点对天气、日历的响应 = 共享的响应基函数 × 由节点知识生成的系数。这一部分先从输入中扣除、预测后再加回，使骨干只学"去掉协变量影响后"的动态。
3. **知识可靠性门控（KRG）**：对每个节点、每个窗口计算无标签的可靠性后验 $q_i(t)$，把节点知识按 $q$ 向总体平均收缩。阈值按误报率取 $\chi^2$ 分位数，不在验证集上调；训练时随机丢弃节点知识，使退路可用。

**为什么是模型贡献，而不是数据集上的应用**：
- 问题在多类数据中都出现（第 1 节）；
- 三个模块可以接到不同骨干上（全局 Transformer、PatchTST、iTransformer、STID），在 4 个负荷数据集、1 个交通数据集和 3 个通用基准上验证；
- "一直相信"和"从不使用"都是这个模型 $q\equiv1$、$q\equiv0$ 的特例，定理 A1 给出两者之间最优门控的形式和收益。

**论文主线（一句话）**："什么时候该相信模型对一个节点的了解？"

---

## 1. 动机：同一现象出现在多类数据中

| 现象 | 数据 | 已有证据 |
|---|---|---|
| 节点知识有用 | Weather、Electricity（iTransformer） | 身份嵌入在所有预测长度上有效：Weather −2.4% 至 −5.2%，Electricity −4.2% 至 −7.7%（实验 4） |
| | FeederBW（40 条馈线） | 随时间变化的台账：MAE −5.5%，晴天中午 −9.1%（先导实验） |
| 节点变化时有害 | Traffic | 身份使 MSE 变差 1.5% 至 6.9%，原因是少数测试期严重漂移的传感器，一个传感器就占测试 MSE 的 15%–16%（实验 4、5） |
| | FeederBW | 登记光伏后 30 天内的晴天中午，直接使用台账 MAE +12%：登记早于投运 1–4 个月（先导实验） |
| 新节点不可用 | Electricity | 身份让未见变量变差 2.8% 至 4.9%（实验 3） |
| | FeederBW | 新馈线上，冻结的台账特征使 MAE +10.9%（先导实验） |
| 门控能挽回损失 | Traffic | 只把漂移最大的 1% 变量退回无身份模型：iTransformer +1.5% → −3.5%，S-Mamba +0.7% → −4.6%（先导分析） |
| | 合成数据 | 满足条件时比最好的单一模型低 6%–28%，条件不满足时代价 ≤ 0.3%（theory_directions A） |

---

## 2. 模型

### 2.1 设定

节点 $i=1..N$，时刻 $t$：
- 回看窗口 $x_i\in\mathbb R^L$；
- 过去与未来的协变量 $w_i$（天气、日历；未来天气为预报或事后值）；
- 可选的描述信息 $d_i(t)$（静态或随时间变化，例如装机容量、建筑用途、车道数）。

节点集合可以变化（新节点），节点行为可以变化（漂移）。骨干网络 $F$ 是任意的全局预测器。

### 2.2 归纳式节点知识编码器（NKE）

$$
k_i(t)=g_d\big(d_i(t)\big)+g_p\big(\pi_i(t)\big)+\delta_i .
$$

- $g_d$：描述信息编码器（容量取 $\log(1+\cdot)$，类别量用嵌入）。没有描述信息的数据集省略这一项。
- $\pi_i(t)$：节点的**近期画像**，由 $[t-R,t]$ 的历史计算（例如过去 4 周按"星期 × 小时"的中位数曲线、水平和尺度），$R\gg L$。它是归纳的（新节点积累 $R$ 步历史后即可用），而且会随节点变化缓慢更新。$g_p$ 是小网络。它补上了回看窗口看不到的周周期，即 theory §2 的身份缺口。
- $\delta_i$：零初始化的残差身份，配合身份 dropout 和按学习预算设定的学习率（theory §4、§5）。只对训练时见过的节点存在，新节点取 0。

### 2.3 知识条件的协变量一致分解（KCD）

$$
u_{i,t}=\sum_{r=1}^{R_b}\beta_{i,r}(t)\,s_r(w_{i,t},c_t),\qquad \beta_i(t)=B\big(k_i(t)\big).
$$

- $s_r$：共享的响应基函数，由协变量和日历计算，可以加单调约束，例如净负荷对辐照不增。
- $\beta_i$：由节点知识生成的节点系数。若描述信息中有容量（例如光伏 kW），对应的系数取 $\rho_{i}(t)\cdot\mathrm{cap}_i(t)\cdot a$，其中 $\rho_i$ 为投运后验（见 2.4）。
- **一致分解**：输入用 $\tilde x_i=x_i-u_i^{\text{past}}$，骨干预测基础部分 $\hat b_i=F(\tilde x_i,w_i,k_i)$，输出 $\hat y_i=\hat b_i+u_i^{\text{future}}$。
- 只有日历时，$u$ 退化为由节点知识生成的周期，相当于归纳式的 CycleNet / 残差周期（RCF）。

### 2.4 知识可靠性门控（KRG）

- **可靠性统计量**：最近 $D$ 天的分解残差 $x_i-u_i$ 的摘要 $r_i(t)$，例如均值、对数标准差、对主要协变量的斜率。它相对该节点训练期分布 $\mathcal N(\mu_i,\Sigma_i)$ 的马氏距离为 $D_i^2(t)$。
- **后验**：$q_i(t)=\sigma\big(a-\tfrac12D_i^2(t)\big)$，$a$ 由误报率 $\alpha$ 对应的 $\chi^2_{\dim r}$ 分位数确定（推论 A2），不在验证集上选。
- **门控**：
  - $k_i^{\text{eff}}=q_ik_i+(1-q_i)\bar k$，$\beta_i^{\text{eff}}=q_i\beta_i+(1-q_i)\bar\beta$，其中 $\bar k$、$\bar\beta$ 为总体平均；
  - 骨干若在节点间混合（iTransformer、图网络），来自节点 $j$ 的消息乘以 $q_j$（A2：消息门控必须与输出门控同时使用）。
- **有记录但时间不确定的变化**（例如台账登记）：对应项的权重用投运后验 $\rho$，先验为由全部事件估计的登记—投运时滞分布。
- **训练**：以概率 $p$ 把一部分节点的知识替换为 $\bar k$（知识 dropout），使骨干在"不用节点知识"时也能预测，即训练出退路（theory §4）。$\Sigma_i$ 由训练窗口估计（节点间收缩）。门控本身不需要额外学习参数。

### 2.5 区间（可选）

按 $q$ 分组的 Mondrian 共形 + ACI 在线校正（theory_directions B）。

### 2.6 与骨干的结合

| 骨干 | 节点知识的接入方式 | 用于 |
|---|---|---|
| 全局编码器–解码器 Transformer（KIT 在 FeederBW 上最好的模型） | $k$ 作为额外 token，或对每个 token 做 FiLM 调制 | 负荷数据集（带天气） |
| PatchTST（通道独立） | 同上 | 通用基准 |
| iTransformer / S-Mamba（变量 token） | $k$ 加到变量 token 上（即现有身份嵌入的归纳版），注意力消息乘以 $q_j$ | 通用基准、Traffic |
| STID（交通） | 替换其空间身份嵌入 | LargeST |
| Chronos-2（冻结） | 只用 KCD 与 KRG 的外层：先修正上下文，预测后加回 | 说明不依赖特定骨干 |

---

## 3. 理论依据与可检验的预测

| 结果 | 内容 | 对应模块 | 可检验的预测 |
|---|---|---|---|
| 命题 1（theory §2） | 置换等变 / 通道独立模型的超额风险 = 给定视图后各节点条件均值的方差 | NKE | 收益在"节点结构在窗口中看不见"的数据上大（Electricity、Traffic 的周周期，FeederBW 的光伏比例），在 ETT 上接近 0 |
| 命题 K1（新） | 节点 $i$ 的协变量敏感度在 $\tau$ 变化 $\Delta\beta$ 时：从窗口中推断敏感度的模型，在其后 $L$ 步内超额误差约为 $\|\Delta\beta\|^2\,\mathbb E\|s\|^2\cdot L/3$（窗口中变化前样本的比例线性下降）；用直推式节点参数的模型，每步超额误差约为 $\|\Delta\beta\|^2\,\mathbb E\|s\|^2$，直到重训；KCD 在 $\beta$ 正确更新时没有这一项 | KCD | 事件后误差曲线：上下文模型线性恢复、身份模型不恢复、KCD 持平 |
| 命题 K2（新） | 真实投运时刻 $T$ 未知、登记时刻 $\tau\le T$ 时，用权重 $\rho_t$ 的超额误差为 $\mathbb E[(\mathbb 1\{T\le t\}-\rho_t)^2]\,\|\Delta\beta\|^2\,\mathbb E\|s\|^2$，后验 $\rho_t=P(T\le t\mid\mathcal F_t)$ 最优；把登记当作投运的超额为 $P(\tau\le t<T)\,\|\Delta\beta\|^2\,\mathbb E\|s\|^2$ | KCD + KRG | FeederBW 登记后头一个月的损失被消除 |
| 定理 A1、推论 A1 | 最优权重 = 状态持续的后验 × 可靠性收缩；相对最优静态权重的收益 $=\kappa^2/\beta\cdot\operatorname{Var}(q)$ | KRG | "一直相信"（$q\equiv1$）与"从不使用"（$q\equiv0$）都是静态特例；收益集中在漂移节点上，无漂移时代价很小 |
| 推论 A2 | 阈值按误报率取 $\chi^2$ 分位数；验证期没有漂移时，验证集会选"不门控" | KRG | 固定 $\chi^2$ 阈值优于在验证集上选阈值 |
| theory §4 | 变量特有 dropout 不收缩偏移，而是训练出汇聚的退路 | 知识 dropout | 去掉知识 dropout 后，门控关闭时误差明显变大 |

命题 K1、K2 是一阶近似（线性化、协变量变化程度在窗口内均匀），推导需在正文中补全。

---

## 4. 查重

| 模块 / 做法 | 已有工作 | 区别 | 重叠 |
|---|---|---|---|
| 可学习的节点身份 | STID（CIKM 2022）、STAEformer（CIKM 2023）、CN / ACN（ICML 2025）、InjectTST、EMAformer（AAAI 2026）、C-LoRA（CIKM 2024）（见 [`related_work.md`](related_work.md)） | 都是直推式、一直信任 | 高（作为 $\delta_i$ 和基线） |
| 由节点属性生成节点参数 | ST-MetaNet（KDD 2019）；MAGCRN（ESWA 2025，生成节点特定的卷积核，摘要）；ST-GFSL（跨城市迁移） | 属性静态、一直信任、不处理漂移 | 中 |
| 未见节点 / 通道 | CPiRi（ICLR 2026，置换不变，训练一半通道即可泛化到未见通道，摘要）；CCM（NeurIPS 2024，用聚类信息代替单个通道的身份，可零样本预测，摘要）；CN 的 PCN（原型）；Cini 等（NeurIPS 2023）、Butera 等（2024）的嵌入迁移与正则化 | 它们放弃或固定节点知识；我们保留并按可靠性使用，而且描述信息可随时间变化 | 中 |
| 协变量处理 | TFT（静态协变量 + 已知未来输入）、TimeXer（NeurIPS 2024）、ChronosX（AISTATS 2025，给预训练模型加协变量模块）、LightGTS-Cov（2026）、Chronos-2；负荷领域经典的"天气敏感 / 不敏感"分解 | 未检索到"由节点知识生成敏感度、并在输入和输出上一致扣除和加回"的深度模型 | 低到中（需引用经典的动态回归和天气归一化） |
| 漂移下的门控 / 测试时适应 | TAFAS（AAAI 2025）、DynaTTA（ICML 2025）、PETSA、ADCSD（交通，2024，指出不同节点漂移速度不同）、AdapTS（2025）、Liu 等（2023，按近期误差组合全局与近期模型）；xCPD（ICLR 2026，按 patch 路由通道依赖） | 它们需要真实值做在线更新，或门控是全局 / 学到的固定量；我们按节点、按窗口、不需要标签，阈值由误报率决定 | 低到中 |
| 设备台账、登记—投运时滞 | 未检索到（见 application_direction 第 2 节） | | 低 |
| 建筑元数据 | BuildingsBench（NeurIPS 2023）把元数据的作用列为后续工作（摘要） | 我们直接在 BDG2 上检验 | 低 |

**结论**：单个组成部分（身份、属性生成参数、未见通道、协变量模块、测试时适应）都有人做过；"节点知识是会过时的，按无标签的后验决定信任多少"这一框架，以及由它推出的三个模块的组合，没有检索到。必须直接对比 CN / PCN、CPiRi、CCM、STID、CycleNet、TFT、TimeXer 和一种测试时适应方法。

---

## 5. 实验设计

### 5.1 数据集

| 数据集 | 节点 | 协变量 | 描述信息 | 变化 | 作用 |
|---|---|---|---|---|---|
| FeederBW | 200 条低压馈线 | 天气 | 台账，随时间变化 | 有记录（有时滞）+ 无记录 | 主应用：漂移、新馈线 |
| BDG2（Building Data Genome 2） | 约 1,600 栋非住宅建筑的电表，2016–2017，逐时 | 天气 | 用途、面积等（静态） | — | 新建筑（归纳） |
| Electricity-287（UCI，KIT 预处理） | 287 个用户 | ERA5 天气 | 无，只用近期画像 | 无记录 | 无描述信息的情形 |
| ENTSO-E 多国负荷（或 ISO-NE 8 个负荷区） | 约 30 国 / 8 区 | 气温 | 国家 / 区 | 2022 年欧洲需求下降等真实漂移 | 系统级、真实的无记录漂移 |
| LargeST（SD 716 / GBA 2,352 个传感器） | 交通流量 | 日历 | 车道数、方向、公路、经纬度 | 传感器漂移 | 跨领域通用性；新传感器 |
| ECL、Traffic、Weather | 321 / 862 / 21 | 日历 | 无 | Traffic 漂移传感器 | 与长期预测文献对比；复用已有基线 |

许可需逐一核对：FeederBW、SSEN 为 CC BY 4.0；LargeST 为 CC BY-NC 4.0；BDG2 仓库标注为 other。

### 5.2 协议

1. **标准**：按时间划分，所有节点都见过。
2. **新节点**：一半节点训练，另一半测试（与 CPiRi 的设置一致）；FeederBW 用推荐的 1–160 / 161–200。
3. **漂移**：
   - 真实事件：FeederBW 台账事件（事件研究），Traffic / LargeST 中测试期严重漂移的传感器，ENTSO-E 2022；
   - 半合成：在测试期给一部分节点注入水平、画像或敏感度的变化，控制幅度和比例。
4. **区间**：总体、漂移组、峰值时段上的覆盖率、宽度和 pinball。

### 5.3 骨干、基线与消融

- **骨干**：全局 Transformer（带协变量）、PatchTST、iTransformer、STID；Chronos-2 外层。
- **基线**：
  - 各骨干单独，以及 + 身份（STID 式）、+ CN / ACN / PCN、+ CycleNet；
  - CPiRi、CCM、TFT、TimeXer；
  - Chronos-2（零样本 / 微调）、TabPFN-TS；
  - 一种带真实值的测试时适应方法（TAFAS 或 ADCSD），作为参考上限；
  - LightGBM + 描述信息。
- **消融**：
  - NKE 的三部分（$d$、$\pi$、$\delta$）；
  - KCD 有无一致扣除、敏感度共享还是由节点知识生成；
  - KRG：不门控 / 硬门控 / 后验门控，$\chi^2$ 阈值与验证集阈值，有无知识 dropout，有无消息门控。
- **指标**：MSE、MAE（负荷另报 nMAE），逐节点误差分布与最差 10% 节点，事件窗口误差，FeederBW 峰值 F1，区间指标；5 个种子。

### 5.4 预期结果（同时是可以被推翻的预测）

- 标准协议：NKE + KCD 在有身份缺口的数据上提升（参照：身份在 Weather / Electricity 上 −2% 至 −8%，FeederBW 台账 −5.5%），在 ETT 类数据上约为 0；KRG 的代价 ≤ 0.3%（与合成数据一致）。
- 新节点：直推式身份比骨干差；NKE 优于骨干，并与 CPiRi / PCN 相当或更好。
- 漂移：KRG 把"一直相信"的损失变为收益（参照 Traffic 先导：+1.5% → −3.5%）；FeederBW 登记后头一个月的损失被投运后验消除。

---

## 6. 与已有代码的对应

| 模块 | `idembed` 中已有的部分 | 需要新写的部分 |
|---|---|---|
| NKE | 身份嵌入、身份 dropout、按预算的学习率倍数（`--identity`、`--id-dropout`、`--id-lr-mult auto`） | 描述信息编码器、近期画像编码器 |
| KCD | 共享周期 + 逐变量偏移（`--rcf-shared`）、通道归一化（`--cn`） | 协变量响应基函数、由节点知识生成系数、带协变量的全局 Transformer 骨干 |
| KRG | 马氏距离后验门控与 $\chi^2$ 阈值（`--drift-gate`）、变量特有 dropout（`--vs-dropout`）、逐变量误差记录（`--per-var`） | 基于分解残差的统计量、知识层面的软门控、消息门控、投运后验 |
| 区间 | `experiments_sim/` 中的 Mondrian 共形 | 接入真实模型、ACI |

数据加载需要新增：FeederBW、BDG2、Electricity-287（ERA5）、ENTSO-E、LargeST。计算量：所有数据集在一张 4090 上均可完成，最大的是 LargeST GBA。

---

## 7. 风险与对策

| 风险 | 对策 |
|---|---|
| 三个模块使模型复杂，审稿人要求逐一证明 | 每个模块对应一个命题和一项预测；消融覆盖全部组合；最小版本先做 NKE + KRG |
| 与 CN / PCN、CPiRi、CCM 重叠 | 正面对比；强调"一直相信 / 从不使用"是本模型的特例，以及描述信息随时间变化、门控不需要标签 |
| 标准协议下部分数据集提升小 | 主张放在"不损失标准精度，同时在新节点和漂移上大幅改善"；报告逐节点和最差节点 |
| KCD 中骨干与 $u$ 可能互相抵消（不可辨识） | 单调约束、只让 $s_r$ 依赖协变量、对 $u$ 的幅度做正则、分阶段训练 |
| 部分数据的天气是事后值 | 明确说明；补充天气加噪实验 |
| 工作量大 | 分两步：先在 FeederBW、Electricity、Traffic 上完成 NKE + KRG（复用已有基线），再加 KCD 和其余数据集 |

## 8. 下一步

1. 在 newpapercode 中实现带协变量的全局 Transformer 骨干，并复现 KIT 在 FeederBW 上的数字。
2. 实现 NKE（$\delta$ + 近期画像 + 描述信息）和 KRG（残差统计量、$\chi^2$ 后验、知识 dropout），在 FeederBW、Electricity、Traffic 上跑三种协议。Electricity、Traffic 用 iTransformer 骨干，可复用已有的基线结果。
3. 实现 KCD，加入 BDG2、Electricity-287（ERA5）。
4. 加入 LargeST、ENTSO-E；补全基线；5 个种子。
5. 正文中补全命题 K1、K2 的推导。

## 来源

- CPiRi（ICLR 2026）：https://arxiv.org/abs/2601.20318
- CCM（From Similarity to Superiority: Channel Clustering for Time Series Forecasting，NeurIPS 2024）：https://arxiv.org/abs/2404.01340
- xCPD（ICLR 2026）：https://arxiv.org/abs/2603.13702
- MAGCRN（ESWA 2025）：https://scholars.cityu.edu.hk/en/publications/traffic-forecasting-with-meta-attentive-graph-convolutional-recur/
- Taming Local Effects in Graph-based Spatiotemporal Forecasting（Cini 等，NeurIPS 2023）：https://proceedings.neurips.cc/paper_files/paper/2023/file/ad58c61c71efd5436134a3ecc87da6ea-Paper-Conference.pdf
- FUNS（Forecasting Unobserved Node States）：https://arxiv.org/abs/2211.11596
- ChronosX（AISTATS 2025）：https://arxiv.org/abs/2503.12107 ；LightGTS-Cov：https://arxiv.org/abs/2602.10412
- ADCSD（Online Test-Time Adaptation of Spatial-Temporal Traffic Flow Forecasting）：https://arxiv.org/abs/2401.04148
- AdapTS：https://arxiv.org/abs/2502.12920 ；Handling Concept Drift in Global Time Series Forecasting（Liu 等）：https://arxiv.org/abs/2304.01512
- TAFAS：https://arxiv.org/abs/2501.04970 ；DynaTTA（ICML 2025）：https://icml.cc/virtual/2025/48077
- M2OE2-GL（大规模馈线的全局到局部概率预测）：https://arxiv.org/abs/2511.17623
- BuildingsBench：https://arxiv.org/abs/2307.00142 ；BDG2：https://arxiv.org/abs/2006.02273
- LargeST：https://arxiv.org/abs/2306.08259
- ISO-NE 负荷与需求报表：https://www.iso-ne.com/isoexpress/web/reports/load-and-demand/-/tree/zone-info
- 其余（CN、STID、STAEformer、InjectTST、EMAformer、C-LoRA、Butera 等、FeederBW、KIT 基准）见 [`related_work.md`](related_work.md) 和 [`application_direction.md`](application_direction.md)。
