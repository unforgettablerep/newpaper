# 新研究方向检索（2026-10-31）

身份嵌入方向的核心已被发表（见 [`related_work.md`](related_work.md)），这里检索新的方向。思路是从我们实验中发现、但文献中还没有覆盖的现象出发，逐个检查是否已有人做过。细节来自论文全文或检索摘要，引用前请再核对原文。

## 已经比较拥挤、不建议作为主线的方向

| 方向 | 代表工作 |
|---|---|
| 测试时适应（TTA） | TAFAS（AAAI 2025）、PETSA（2025）、DynaTTA、COSA、ADAPT-Z、*Towards Principled TTA*（2026-05）、*Training on the Future: A Delay-Aware Audit of TTA*（2026-10） |
| 基准与评测可靠性 | *There are no Champions in Supervised LTSF*（TMLR 2026）、fev-bench（2025）、*It's TIME*（2026）、*Are We Winning the Wrong Game?*（2026-03）、ICML 2026 立场论文 *Current Benchmarking Hinders Real Progress*、TFB（VLDB 2024） |
| 高维（数千变量）预测 | Unicorn（2026）、STHD（2024）、WWW 2026 的高维预测工作；数据集 LargeST（NeurIPS 2023，8600 个传感器） |
| 变量顺序与 Mamba | MambaTS、SOR-Mamba、CRS-Mamba、CPiRi（ICLR 2026）、Graph-Mamba |
| 时间序列基础模型的多变量处理 | Chronos-2（2025，group attention）、Moirai、Timer-XL |

## 候选方向

### 方向 1（推荐）：变量级分布漂移下的无标签逐变量路由

**来自我们的发现**：Traffic 上身份嵌入在 86%–91% 的传感器上有帮助，但少数测试期读数严重漂移的传感器主导了 MSE，单个传感器就占 15%–16%（实验 5）。也就是说，"变量特有的知识"（身份、跨变量混合）只对行为稳定的变量有益；对正在漂移的变量，应该退回更保守的预测。

**想法**：推理时为每个变量计算一个**不需要标签**的漂移分数（输入窗口相对训练期的统计偏移，或基于表示的 OOD 分数）。对分数高的变量，关闭或减弱其变量特有的部分（身份嵌入、跨变量混合），退回到通用预测。模型用身份 dropout（或混合 dropout）训练，使同一个模型在两种模式下都能工作；路由阈值在验证集上选定。

**检索结果**：
- TAFAS 有逐变量的门控，但门控是学到的固定向量，而且属于需要真实值的测试时适应；PETSA 等类似。
- Han 等（2023）指出通道依赖模型容量大但对漂移不鲁棒、通道独立模型更鲁棒，但没有在推理时按变量切换。
- JointPGM（TNNLS 2025）建模序列内与序列间的漂移；2026 年 Neural Networks 的一篇论文用单变量框架加事后校准应对单个变量的漂移。
- 双重拒绝（arXiv 2503.19656）是样本级的 OOD 拒绝与弃权，不是逐变量路由；FOIL（ICML 2024）、VLBM（2026）是训练阶段的 OOD 鲁棒方法。
- Exogenous Dropout（2026）用 dropout 提高对协变量损坏的鲁棒性；Butera 等发现嵌入 dropout 能提升鲁棒性和迁移。
- **没有找到"推理时无标签检测漂移变量并按变量路由"的工作。**

**先导结果**（用已有的 `traffic.jsonl` 逐变量结果，预测 96 步，3 个种子；脚本为 newpapercode 的 `tools/drift_gate_pilot.py`）：
- 漂移分数：变量在测试段输入上的均值偏移和尺度偏移（以训练段统计量为单位）。
- 路由：分数最高的一部分变量用无身份模型的预测，其余用有身份模型的预测。这个比例在验证集上选定（用验证段的漂移和验证误差），每次都选中了 1%。

| 模型 | 全部用有身份 | 路由后 | 每个变量都选对时（上限） |
|---|---|---|---|
| iTransformer `add` | +1.53% | **−3.52%** | −4.46% |
| S-Mamba `add` | +0.71% | **−4.61%** | −5.66% |
| iTransformer `add` + dropout 0.3 | −2.35% | **−3.00%** | −3.40% |
| S-Mamba `add` + dropout 0.1 | −0.75% | **−4.87%** | −5.69% |

（相对无身份模型的 MSE 变化。）

**先导结果的局限**：
- 漂移分数用的是整个测试段的输入统计量，而不是逐窗口在线计算的；
- 路由是在两个分别训练的模型之间切换，而不是同一个模型内部的门控；
- 只做了 Traffic、预测 96 步。

**需要验证的问题**：
1. 逐窗口、在线计算的漂移分数还能保留多少收益；
2. 用身份 dropout 训练的单个模型，对被路由的变量把身份置零，能否达到两模型切换的效果；
3. 在其他有漂移变量的数据集上是否成立（PEMS、Electricity、LargeST 子集），以及在人为注入漂移的受控实验中（只让部分变量漂移）收益随漂移程度的变化；
4. 与 TAFAS、PETSA、RevIN 和通道独立模型对比。

**可行性**：高。现有代码已有身份 dropout、逐变量误差记录和漂移统计量；需要加逐窗口漂移分数和推理时门控。

### 方向 2：通道混合中的"污染"传播与鲁棒混合

**问题**：一个漂移或异常的变量，是否会通过注意力或 Mamba 混合把误差传给其他变量？注意力（加权求和）和 Mamba（递归扫描）的传播方式不同，是否一个更脆弱？

**检索结果**：Han 等（2023）给出通道依赖与通道独立在稳健性上的一般性权衡；Exogenous Dropout（2026）在协变量损坏下测了 iTransformer 等模型，误差比只用目标变量时高 32%–62%；ICLR 2026 的一篇论文（arXiv 2506.08660）处理缺失和异步通道；CPiRi 关注置换不变性和未见通道。**没有找到针对变量 token 模型、区分注意力与 Mamba、在推理时注入单变量损坏的传播分析。**

**可行性**：高，可以作为方向 1 的第二部分。用已有模型做受控注入实验，例如把一个变量替换成漂移或噪声序列，再测其他变量误差的变化。

### 方向 3：通道混合 SSM 中的位置泄露与顺序依赖

**问题**：把我们"扫描顺序就是隐式身份"的实验结论推进到理论层面，例如固定顺序的 S-Mamba 能表达哪些非置换等变的函数，顺序的局部性何时是有用的归纳偏置（Weather 的列顺序约有 1.3 个百分点的价值）。

**检索结果**：点云 Mamba 的工作观察到 Mamba 隐式使用输入顺序，使显式位置编码变得多余；有理论工作讨论选择性 SSM 的表达能力和衰减；还有预印本从卡尔曼滤波角度论证 SSM 天然依赖顺序。**没有找到针对通道维度混合的专门分析。**

**风险**：贡献可能偏小，更适合做成分析性短文或作为方向 1 的背景。

### 方向 4：验证期与测试期错配下的模型选择与早停

**来自我们的发现**：Exchange 上验证集偏好身份学习率 ×10，测试集却变差；Traffic 上验证误差改善、测试误差变差。

**检索结果**：Han 等（ICML 2024）提出在时间分布漂移下用自适应滚动窗口评估模型；TempusBench（2026）用滚动窗口调参；TFB 指出排名随数据划分而变。**没有找到在长期预测基准上系统比较"单一验证段"与"多窗口滚动验证"对早停和超参数选择影响的研究。**

**风险**：更像评测研究，难以形成方法贡献；与"基准可靠性"一类工作接近。

## 建议

以**方向 1** 为主线，**方向 2** 作为其中的分析部分。理由：
- 它直接建立在我们已有的独特发现上（逐变量误差分析、身份 dropout、隐式身份）；
- 检索没有发现同样的做法；
- 先导结果的提升明显，而且几乎达到了上限；
- 代码和数据大部分可以复用，4090 上的计算量不大。

可能的论文主线："多变量预测中，变量特有的知识（身份、跨变量混合）只在变量行为稳定时有益；我们提出无标签的逐变量漂移路由，在不访问测试真实值的前提下，把漂移变量退回到通用预测。"

## 下一步（建议）

1. 在 newpapercode 中加入：逐窗口、逐变量的漂移分数；推理时按变量把身份置零（以及可选地减弱跨变量混合）；记录逐窗口误差，以便分析。
2. 先在 Traffic 和 Electricity 上，用已训练过的配置复现先导结果的单模型版本。
3. 设计受控的漂移注入实验，并加入 PEMS 数据集。
4. 加入 TAFAS / PETSA 作为对照。

## 来源

- TAFAS: https://arxiv.org/abs/2501.04970
- PETSA: https://arxiv.org/abs/2506.23424
- Towards Principled Test-Time Adaptation for Time Series Forecasting: https://arxiv.org/abs/2605.17250
- Training on the Future (delay-aware audit of TTA): https://arxiv.org/abs/2610.12232
- There are no Champions in Supervised LTSF: https://arxiv.org/abs/2502.14045
- fev-bench: https://arxiv.org/abs/2509.26468
- It's TIME: https://arxiv.org/abs/2602.12147
- Are We Winning the Wrong Game?: https://arxiv.org/abs/2603.08156
- TFB: https://www.vldb.org/pvldb/vol17/p2363-hu.pdf
- LargeST: https://arxiv.org/abs/2306.08259
- Unicorn: https://arxiv.org/abs/2605.30376
- Scalable Transformer for High Dimensional MTS (STHD): https://arxiv.org/abs/2408.04245
- Chronos-2: https://arxiv.org/abs/2510.15821
- The Capacity and Robustness Trade-off: https://arxiv.org/abs/2304.05206
- Robust MTS Forecasting against Intra- and Inter-Series Transitional Shift (JointPGM): https://doi.org/10.1109/tnnls.2025.3593156
- Rethinking multivariate modeling … univariate framework with post-calibration: https://www.sciencedirect.com/science/article/abs/pii/S0893608026001723
- Towards Reliable Time Series Forecasting under … (dual rejection): https://arxiv.org/abs/2503.19656
- VLBM: https://arxiv.org/abs/2606.02138
- FOIL (ICML 2024): https://proceedings.mlr.press/v235/liu24ae.html
- Exogenous Dropout: https://arxiv.org/abs/2607.05452
- Towards Robust Real-World MTS Forecasting (dependency, asynchrony, missingness; ICLR 2026): https://arxiv.org/abs/2506.08660
- On the Regularization of Learnable Embeddings for Time Series Forecasting: https://arxiv.org/abs/2410.14630
- CPiRi: https://arxiv.org/abs/2601.20318
- Understanding Input Selectivity in Mamba (ICML 2025): https://proceedings.mlr.press/v267/huang25ab.html
- On the Expressivity of Selective State-Space Layers: https://arxiv.org/abs/2502.02209
- Model Assessment and Selection under Temporal Distribution Shift (ICML 2024): https://arxiv.org/abs/2402.08672
- TempusBench: https://arxiv.org/abs/2604.11529
