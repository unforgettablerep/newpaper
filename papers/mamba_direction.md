# 方向调整：在 Mamba 上做改进（2026-11-01）

要求：论文的模型贡献落在 Mamba 本身的修改上。本文件以 S-Mamba 为基础，把已有发现转成 Mamba 内部的修改：
- 扫描顺序即隐式身份（实验 2、6、8）；
- Traffic 漂移传感器（实验 5）；
- 未见变量（实验 3）；
- RNK 沙盒的结论（[`model_sandbox.md`](model_sandbox.md)）。

文件还给出 Mamba 文献的查重和实验设计。应用场景不变：多节点电力负荷（馈线），另外用交通数据检验通用性。文献细节来自全文（标注"全文"）或摘要（标注"摘要"），引用前请再核对原文。

## 结论

**模型（暂名 RS-Mamba：可靠性感知的选择性扫描 Mamba）**：在 S-Mamba（变量 token + 双向 Mamba 跨变量扫描 + FFN）上做三处修改。

1. **可靠性感知的选择性扫描**（核心，Mamba 特有）：
   - 变量 $j$ 的选择性步长改为 $\Delta_j \leftarrow q_j\Delta_j$，两个扫描方向都用；它进入局部卷积的输入也乘以 $q_j$。$q_j\in[0,1]$ 是该变量"仍处于训练期状态"的后验。
   - $q_j=0$ 时，$\bar A_j=\exp(\Delta_jA)=I$、$\bar B_j=0$：该变量在扫描中"透明"，既不写入状态，也不衰减状态。没有局部卷积时，这严格等价于把它从扫描序列中删去（命题 M1）。
   - 漂移变量因此不会通过扫描污染其他变量（A2：污染随漂移比例平方增长）；它自己的预测仍经残差与 FFN 使用自身历史。
   - 训练时随机令部分变量 $q=0$（扫描跳过 dropout），测试时 $q$ 由无标签的 $\chi^2$ 后验给出，或用延迟误差给出（沙盒中已实现）。
2. **与扫描顺序无关的归纳式变量身份**：
   - S-Mamba 的固定扫描顺序本身就是一种直推式身份（命题 2；打乱顺序使 Electricity 变差 3%–9%）。它在节点重排、新增节点、未见节点上都会失效。
   - 改为随机顺序训练，身份由台账描述和近期画像生成（新节点可用），另加带 dropout 的残差身份；测试时用一个随机顺序，或 2 个顺序平均。
3. **外生一致分解**（沙盒中的 KCD）：
   - 每个变量 token 在嵌入前扣除"每单位容量的响应 × 登记容量"等协变量部分，预测后加回；未来天气、日历拼接进该变量的 token 嵌入。
   - 沙盒中这是最强、最稳的模块：FeederBW 上 MSE −18%，在未训练的馈线上 −15%。

**为什么能成立**：
- **空白清楚**：没有检索到用外部、经过校准的可靠性去调节 Mamba 步长 $\Delta$ 的工作。已有的 $\Delta$ 修改都与时间间隔有关（不规则采样）；跳过 token 的工作只为加速（视觉 Mamba 的 token 剪枝）。PowerMamba（IEEE TPWRS）是电力领域的 Mamba，只把外部预报拼接进上下文，没有身份、台账、漂移处理和门控（全文）。
- **与已有工作直接衔接**：S-Mamba 的代码（含纯 PyTorch 的 Mamba 实现和 CUDA 路径）、8 个数据集 × 4 个长度的官方设置基线、随机顺序与身份的结果、Traffic 逐传感器分析、未见变量协议、RNK 沙盒的门控与分解代码，都可以直接复用。
- **有理论支撑**：命题 2（顺序即身份）、A2（消息污染与可靠性加权）、定理 A1（输出门控）、命题 K1（窗口污染），新增的命题 M1 把门控落到 Mamba 的离散化上。

---

## 1. 每处修改对应的证据

| 修改 | 问题 | 已有证据 |
|---|---|---|
| 可靠性感知的扫描 | 漂移变量经跨变量混合影响其他变量 | A2 的推导与模拟：污染 ∝ 漂移比例²；可靠性加权 + 自身输出门控在合成数据上 −1.3% 至 −2.5%（theory_directions A2）。RNK 沙盒：门控在未记录变化后接近 oracle，稳定时段代价 ≤ 0.3%。**尚缺**：S-Mamba 中跨变量污染的实测；Traffic 上的损失主要来自漂移传感器自身（实验 5），跨变量部分有多大还不知道 |
| 归纳式身份 + 随机顺序 | 固定顺序 = 直推式身份；新节点、重排失效 | 实验 2、8：打乱顺序、不加身份时 Electricity +3%–9%、Weather +1.5%–5.8%；随机顺序 + 身份 + 2 顺序平均：29 组平均 −1.05%，Electricity −4.7%，ETTh1 −2.3%（官方设置）；实验 3：身份使未见变量变差 2.8%–4.9%，身份 dropout 减轻到 0.7%–1.2% |
| 外生一致分解 | Mamba 变体普遍不处理节点特有的协变量响应和台账变化 | RNK 沙盒：FeederBW MSE −18%、MAE −7.6%，晴天中午 −25%，未训练馈线 −15% |

---

## 2. 查重：Mamba 时序文献

| 工作 | 做法 | 与本方向的关系 |
|---|---|---|
| S-Mamba（Wang 等，2024） | 变量 token、双向 Mamba 跨变量扫描、FFN 处理时间 | 基础模型 |
| MambaTS（Pattern Recognition 2026，摘要） | 变量排列训练、按最短路径解码扫描顺序（VAST）、对选择性参数做 dropout、去掉因果卷积 | 随机顺序训练已有；它的 dropout 是随机正则化，不是按可靠性调节 $\Delta$；不处理未见变量、漂移、协变量 |
| SOR-Mamba、CRS-Mamba、GPS-Mamba（ESWA 2026，全文）、CPiRi（ICLR 2026） | 减弱顺序偏差、按相关图或拉普拉斯排序、置换不变与未见通道 | 顺序问题已拥挤；我们的角度是"顺序即身份"及其归纳式替代，需正面对比 |
| CMamba、TimePro、TimeMachine、ms-Mamba 等 | 通道混合、超状态、多尺度 | 结构改进，与可靠性无关 |
| ASGMamba（2026，摘要） | 按局部频谱能量对 patch 做噪声门控，加可学习的节点嵌入 | 门控在通道内部的频谱上，不判断整个通道是否可靠；节点嵌入是直推式的 |
| PowerMamba（IEEE TPWRS，全文） | 时间 + 变量双重 token、移动平均分解、RevIN，外部预报拼接进上下文；ERCOT GridSet 数据 | 电力领域最直接的对照；没有身份、台账、漂移处理、门控 |
| Reliable Grid Forecasting（2026 预印本） | S-Mamba、PowerMamba 用于 CAISO 负荷，尾部风险指标 | 应用评测 |
| Δt-Mamba3D（2025）、TIDES（2026） | $\Delta$ 按真实时间间隔缩放，或把输入依赖移到状态矩阵 | 修改 $\Delta$ 的先例，但针对不规则采样，不针对变量可靠性 |
| 视觉 Mamba 的 token 剪枝与合并（AMVim，NeurIPS 2025；MaMe；隐状态对齐 2409.18962） | 删去或合并 token 以加速，并处理扫描中断 | "跳过 token"的先例，目的是效率 |
| 时空 Mamba（STG-Mamba、SpoT-Mamba、ST-Mamba） | 图结构 + 选择性扫描 | 交通基线；未见处理传感器漂移 |
| CN（ICML 2025）、Butera 等（2024） | 通道身份、嵌入正则化与迁移 | 身份部分的对照 |

**结论**：
- 修改 1（按校准的可靠性调节 $\Delta$，使不可靠变量在扫描中透明）没有检索到，新意最清楚；
- 修改 2 与 MambaTS、CPiRi、CN/PCN 部分重叠，新意在"顺序即直推式身份"的分析和归纳式替代；
- 修改 3 在 Mamba 文献中没有检索到，PowerMamba 只拼接外部预报。

---

## 3. 模型

### 3.1 记号

S-Mamba 把变量 $j$ 的回看窗口嵌入成 token $e_j$，在 token 序列上做前向和反向两次选择性扫描：

$$
h_j=\bar A_jh_{j-1}+\bar B_ju_j,\qquad y_j=C_jh_j+Du_j,\qquad \bar A_j=\exp(\Delta_jA),\ \bar B_j\approx\Delta_jB_j,
$$

其中 $\Delta_j,B_j,C_j$ 由 $u_j$（$e_j$ 经投影和局部卷积）生成。

### 3.2 修改 1：可靠性感知的选择性扫描

$$
\Delta_j' = q_j\,\Delta_j,\qquad u_j' = \mathrm{conv}(q\odot u)_j .
$$

**命题 M1（透明性）**：
- 若 $q_j=0$，则 $\bar A_j=I$、$\bar B_j=0$，$h_j=h_{j-1}$：变量 $j$ 既不写入状态，也不改变状态。
- 没有局部卷积时（MambaTS 也去掉了因果卷积），其余变量的状态和输出与"从序列中删去变量 $j$"完全相同。$q\in\{0,1\}$ 时，扫描等价于只在可靠变量的子序列上扫描；软的 $q$ 在两者之间连续插值。
- 有宽度为 2 的因果卷积时（S-Mamba 默认），卷积输入乘以 $q$ 后，被跳过变量的下一个变量看到的邻居为零，而不是再前一个变量。与删去只差这一个邻居项，可以改用 $d_{\text{conv}}=1$ 消除。

证明直接来自零阶保持离散化，写进正文时需要补全细节（含双向扫描）。

**推论**：A2 的消息污染分析可以直接套用。均匀混合时，漂移比例为 $\rho$ 的污染偏差约为 $\rho^2\sigma_f^2$；可靠性加权后消失。同时，漂移变量自己的变量特有部分（身份）也要按 $q_j$ 门控（定理 A1），否则漂移变量自身反而变差，这一点 A2 已经指出。

**$q$ 的来源**：
- 无标签：窗口统计量相对该变量训练期分布的马氏距离，$q=\sigma((c-D^2)/2)$，$c$ 取 $\chi^2$ 的 0.999 分位数。已有 `--drift-gate` 的实现，现在把 $q$ 送进 $\Delta$，而不是只做输出混合。
- 延迟误差（运行中每天到达的实测值）：用于输出门控。

**训练**：扫描跳过 dropout，以概率 $p$ 令随机变量的 $q=0$，使模型学会在缺少部分变量消息时预测。

### 3.3 修改 2：归纳式变量身份 + 随机顺序

- token：$e_j=\mathrm{Emb}(x_j)+g_d(d_j)+g_p(\pi_j)+q_j\,\delta_j$，其中 $\delta_j$ 带身份 dropout；
- 训练时每步随机扫描顺序（已有 `--scan-order shuffle`）；测试时一个随机顺序，或 2 个顺序平均。
- 理论 §7 的预测 P6：一个随机顺序就够。
- 可检验：
  - 测试时打乱、插入或删除变量，固定顺序的 S-Mamba 变差，本模型不变；
  - 在只用一半变量训练的协议下，本模型优于直推式身份和 CPiRi。

### 3.4 修改 3：外生一致分解

与沙盒 KCD 相同：

$$
\tilde x_j = x_j-u_j^{\text{past}},\qquad \hat y_j=\hat b_j+u_j^{\text{future}},\qquad u_j=\sum_r\beta_r(k_j)s_r(w,c)+\sum_k \mathrm{cap}_{j,k}(t)\,a_k(w,c).
$$

未来天气和日历拼接进变量 $j$ 的嵌入输入。台账容量的投运方式（登记即投运 / 后验）作为消融。

---

## 4. 实验设计

**数据集**：

| 数据集 | 用途 |
|---|---|
| FeederBW（200 条馈线） | 主应用：台账、外生分解、新馈线、登记事件 |
| ERCOT GridSet（PowerMamba 发布） | 电力领域与 PowerMamba 在其自身设置下对比（外部预报） |
| Electricity（321） | 身份缺口；未见变量协议（复用实验 3） |
| Traffic（862）、PEMS04/08 | 真实的漂移传感器；时空 Mamba 基线 |
| Weather、ETT | 检验"没有代价" |
| 半合成注入 | 在 Electricity、FeederBW 上，令比例 $\rho\in\{0,0.05,0.1,0.2,0.3\}$ 的变量在测试期漂移，检验 $\rho^2$ 规律 |

**基线**：
- Mamba 类：S-Mamba、MambaTS、SOR-Mamba、CMamba、GPS-Mamba、PowerMamba；S-Mamba + CN；
- 其他：iTransformer、TimeXer（外生变量）、CPiRi；FeederBW 上另加 Chronos-2。

**可检验的预测**：

| 编号 | 预测 | 检验 |
|---|---|---|
| T1 | 不门控时，稳定变量的误差随漂移比例 $\rho$ 约按 $\rho^2$ 增长；可靠性感知扫描使其基本不随 $\rho$ 变 | 半合成注入，按 $\rho$ 画曲线 |
| T2 | 只做扫描门控、不做自身输出门控时，漂移变量自身变差；两者同时用最好 | 消融 |
| T3 | 测试时重排或增删变量，固定顺序 S-Mamba 变差，本模型不变；未见变量上优于直推式身份 | 置换与半数变量协议 |
| T4 | 外生分解的收益集中在协变量主导的时段（晴天中午），并能迁移到新馈线 | FeederBW 两种划分 |
| P6 | 一个随机顺序 ≈ 多顺序平均 > 原顺序 | 同一次运行中评估 |

**消融**：三处修改各自去掉；$q$ 的来源（无标签 / 延迟误差 / oracle）；卷积输入是否乘 $q$；扫描跳过 dropout 的比例。

---

## 5. 代码改动（newpapercode `idembed`，可复用 `rnk`）

| 位置 | 改动 |
|---|---|
| `idembed/mamba.py` | `MambaTorch.forward(x, q=None)`：卷积输入乘 $q$，`dt = softplus(...) * q`；CUDA 路径改用 `mamba_ssm` 的非融合实现，先算好 $\Delta$（乘 $q$），再调用 `selective_scan_fn(..., delta_bias=None, delta_softplus=False)` |
| `idembed/models.py` | `MambaLayer.forward(x, q)` 把 $q$ 传给前向和反向扫描（反向时翻转），与随机顺序的排列保持一致；变量 token 的身份部分乘 $q$ |
| `idembed/engine.py` | 扫描跳过 dropout；用现有马氏距离后验计算 $q$ 并送入扫描；半合成漂移注入 |
| 数据 | FeederBW 的变量 token 版本（200 条馈线 + 各自的天气），台账容量；ERCOT GridSet |
| 外生分解 | 从 `rnk/model.py` 的 `CovariateResponse` 移植为 S-Mamba 外层 |
| 测试 | 命题 M1：$q=0$ 的变量对其余变量的输出无影响，并等于在删去该变量的序列上扫描 |

---

## 6. 风险与对策

| 风险 | 对策 |
|---|---|
| 真实数据中跨变量污染不大（Traffic 的损失主要来自漂移传感器自身） | 先在 S-Mamba 上实测"其他传感器"的误差变化；用半合成注入给出污染何时重要（$\rho^2$）；论文同时报告自身输出门控 |
| 修改 2 与 MambaTS、CPiRi、CN/PCN 重叠 | 正面对比；主张放在"顺序即直推式身份"的分析与归纳式替代 |
| 修改 CUDA 路径带来速度下降 | 只替换选择性扫描的输入，仍用官方内核；报告训练与推理时间 |
| 标准基准上提升小 | 主张放在漂移、新节点、重排上的稳健性，以及电力应用上的收益；标准基准报告"不变差" |
| 天气为事后值 | 与 application_direction 相同，补充加噪实验；ERCOT 有外部预报 |

## 7. 下一步

1. 在 `idembed/mamba.py`、`models.py` 中实现可靠性感知扫描，并写命题 M1 的单元测试。
2. CPU 沙盒：小规模 S-Mamba 上的半合成污染实验（$\rho$ 扫描），检验 T1、T2。
3. GPU：Traffic、Electricity 上的漂移门控（$q$ 进入 $\Delta$）与半数变量协议；FeederBW 加外生分解。
4. 补齐基线（MambaTS、PowerMamba 等）和 ERCOT 数据；5 个种子。

## 来源

- S-Mamba（Is Mamba Effective for Time Series Forecasting?）：https://arxiv.org/abs/2403.11144
- MambaTS：https://arxiv.org/abs/2405.16440 （Pattern Recognition 2026）
- SOR-Mamba：https://arxiv.org/abs/2410.23356 ；CRS-Mamba：https://dasfaa2025.github.io/paper/research/research_617_paper.pdf ；CPiRi：https://arxiv.org/abs/2601.20318 ；GPS-Mamba：paperlib 第 10 篇（ESWA 2026）
- CMamba：https://arxiv.org/abs/2406.05316 ；TimePro：https://arxiv.org/abs/2505.20774 ；ms-Mamba：https://arxiv.org/abs/2504.07654
- ASGMamba：https://arxiv.org/abs/2602.01668
- PowerMamba：https://arxiv.org/abs/2412.06112 （IEEE TPWRS）
- Reliable Grid Forecasting: State Space Models for Safety-Critical Energy Systems：https://arxiv.org/abs/2601.01410
- Δt-Mamba3D：https://arxiv.org/abs/2510.19003 ；TIDES：https://arxiv.org/abs/2605.09742
- AMVim（Pruning-Robust Mamba, NeurIPS 2025）：https://proceedings.neurips.cc/paper_files/paper/2025/hash/a5e7816971fa6fee513b4980edbf254e-Abstract-Conference.html ；MaMe：https://arxiv.org/abs/2508.13599 ；Pruning-aware hidden-state alignment：https://arxiv.org/abs/2409.18962
- SpoT-Mamba：https://arxiv.org/abs/2406.11244
- Mamba for Time Series Analysis: A Contemporary Survey（2026 预印本）：https://www.preprints.org/manuscript/202605.0995
- Mamba time series forecasting with uncertainty quantification：https://arxiv.org/abs/2503.10873
- 其余（CN、Butera 等、FeederBW、KIT 基准）见 [`related_work.md`](related_work.md)、[`application_direction.md`](application_direction.md)、[`model_direction.md`](model_direction.md)
