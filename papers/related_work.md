# 相关工作检索（2026-10-31）

检索目的：本研究的各项做法和发现是否已有论文做过。下文的细节来自论文全文（标注"全文"）或检索摘要（标注"摘要"）；引用前请再核对原文。

## 结论

**核心想法"给变量 token 加可学习的身份向量"已经被做过，而且做得比我们系统**：最接近的是 Lee、Park、Lee 的 *Channel Normalization for Time Series Channel Identification*（ICML 2025）。它在 iTransformer 和 S-Mamba 上把"可学习向量加到通道 token 上"（channel identifier）作为基线，并提出更强的逐通道归一化（CN / ACN / PCN）。所以"身份嵌入有效"本身不能作为论文的主要贡献。

仍可能是新的：(1) 用随机扫描顺序的对照实验证明并量化"S-Mamba 的扫描顺序就是隐式身份"；(2) 在 S-Mamba 上把显式身份与随机顺序训练、多顺序平均结合起来；(3) 在长期预测基准上分析身份嵌入的失败方式（Traffic 上少数漂移传感器主导 MSE、未见变量变差）以及身份 dropout 的修复效果。这三点的组成部分大多也已有人做过，新意在于组合和分析。

## 逐项对照

| 我们的做法 / 发现 | 已有工作 | 重叠程度 |
|---|---|---|
| 给每个变量的 token 加零初始化的可学习身份向量，理由是"历史相似的变量无法区分" | **CN**（ICML 2025，全文）：定义"通道可辨识性"（CID），指出 iTransformer 不具备 CID；以 channel identifier（加到通道 token 上的可学习向量）为基线，iTransformer 在 12 个数据集上平均 MSE 降低 9.8%；CN 为 11.3%，ACN 为 12.4%。**InjectTST**（2024，摘要）：在通道独立的 PatchTST 中加入可学习的 channel identifier。**EMAformer**（arXiv 2511.08396，2025-11，全文；检索摘要称被 AAAI 2026 接收）：iTransformer + 通道嵌入 + 相位嵌入 + 通道-相位联合嵌入。**IndexNet**（arXiv 2509.23813，2025，摘要）：MLP 模型中按变量索引分配可学习身份嵌入，"避免输入相近时预测同质化"。**C-LoRA**（CIKM 2024，摘要）：逐通道低秩适配器，用于 iTransformer 等。时空预测中更早：**STID**（CIKM 2022，摘要）提出"样本在空间维度上不可区分"并用空间身份嵌入解决；**STAEformer**（CIKM 2023，摘要）用自适应嵌入让普通 Transformer 达到交通预测 SOTA | **高**：做法和动机都已发表 |
| iTransformer 收益大、S-Mamba 收益小 | CN（全文）：iTransformer 被归为非 CID，S-Mamba 被归为 CID（"Mamba 结构有助于区分通道"）；CN 在 S-Mamba 上的平均收益为 4.0%，iTransformer 为 11.3% | **中**：现象和定性解释已有，但没有用对照实验检验 |
| 用随机扫描顺序证明并量化"固定扫描顺序 = 隐式身份"（不加身份时打乱顺序使 MSE 变差 3%–9%，加身份后收益与 iTransformer 相当） | 未检索到。MambaTS 讨论了顺序敏感性，但没有讨论顺序泄露变量身份（全文） | **低**：可能是新的分析 |
| 训练时随机打乱扫描顺序 | **MambaTS**（arXiv 2405.16440，全文）：Variable Permutation Training，每次迭代打乱变量顺序，解码前还原；推理时用 VAST 选一个顺序，"随机采样 100 个顺序"只是消融对照。**CPiRi**（ICLR 2026，摘要）：训练时打乱通道以实现置换不变，并能泛化到未见通道。**SOR-Mamba**（NeurIPS 2024 workshop，摘要）：用正反通道顺序嵌入之间的距离正则化，并去掉 1D 卷积，以减弱顺序偏差。**CRS-Mamba**（DASFAA 2025，摘要）：按变量相关图重排扫描顺序 | **高** |
| 测试时对多个随机顺序取平均 | **Graph-Mamba**（arXiv 2402.00789，全文）：训练时随机打乱节点顺序，推理时对 m 个排列的输出取平均（消融中 m=5）。理论上对应 **Janossy pooling**（ICLR 2019） | **高**：技术已有，用在变量 token 的时间序列 Mamba 上未检索到 |
| 显式身份 + 随机顺序 + 多顺序平均的组合 | 未检索到 | **低** |
| 身份是直推式的，未见变量变差；身份 dropout 减轻这种伤害 | **Cini 等**（NeurIPS 2023，摘要）：节点嵌入是"局部效应"，讨论可迁移性和正则化（变分、聚类）。**Butera 等**（arXiv 2410.14630，全文）：比较了 L1/L2、dropout、聚类、变分、遗忘（重置）等嵌入正则化；扰动类方法最好，dropout 在零样本迁移上提升最大（PEMS07 MAE 57.4 → 34.2），但只用了 RNN/STGNN 骨架和时空数据集。CN 的 PCN 用原型处理未见通道（全文）；CPiRi 也能泛化到未见通道（摘要） | **中到高**：结论在时空预测中已有，在 iTransformer / S-Mamba 和长期预测基准上未检索到 |
| Traffic 上身份使 MSE 变差：少数测试期严重漂移的传感器主导 MSE，单个传感器占 15%–16%；身份 dropout 可修复 | 未检索到。CN 没有用 Traffic，用的是 PEMS（全文）；EMAformer 对 Traffic 只报告了注意力熵（全文） | **低**：可能是新的发现 |
| 身份参数从 0 开始、官方学习率很小，需要单独放大身份学习率 | 未检索到专门讨论 | 小的工程发现 |

## 与 CN 论文结果的差异

CN 报告的 channel identifier 收益比我们大，而且在 ETT 上也有收益（iTransformer 上 CN 的收益：ETTh1 3.5%、Weather 5.0%、ECL 10.1%）。我们的身份嵌入在 ETT 上接近 0，在 Weather 上为 −2.4% 至 −5.2%、Electricity 上为 −4.2% 至 −7.7%。可能的原因：
- 它的 12 个数据集包括 PEMS03/04/07/08 和 Solar，平均值受这些数据集的影响很大；
- 它的超参数在验证集上调过；
- CN 除了逐通道的偏置，还有逐通道的缩放。

需要在同一协议下复现 CN / ACN 才能比较。

## 对论文的影响

1. 必须引用并对比：CN / ACN / PCN、channel identifier（InjectTST）、C-LoRA、EMAformer、STID / STAEformer；Mamba 方面要对比 MambaTS（VPT）、SOR-Mamba、CPiRi，并说明 Graph-Mamba 和 Janossy pooling 与多顺序平均的关系。
2. 论文的重心应从"提出身份嵌入"转向：
   - 机制：用对照实验说明注意力与 Mamba 在通道可辨识性上的差别，以及扫描顺序如何携带身份；
   - 不依赖顺序的 S-Mamba：显式身份 + 随机顺序 + 多顺序平均，并与 VPT、SOR-Mamba 对比；
   - 失败方式与正则化：分布漂移和未见变量，并与 Butera 等的嵌入正则化结论对照。
3. 实验上需要补充：在我们的代码中实现 CN / ACN 作为对照；加入 PEMS 和 Solar，使数据集覆盖与 CN 一致。

## 来源

- Channel Normalization for Time Series Channel Identification (ICML 2025): https://arxiv.org/abs/2506.00432
- InjectTST: https://arxiv.org/abs/2403.02814
- EMAformer: https://arxiv.org/abs/2511.08396
- IndexNet: https://arxiv.org/abs/2509.23813
- Channel-Aware Low-Rank Adaptation (C-LoRA): https://arxiv.org/abs/2407.17246
- STID: https://arxiv.org/abs/2208.05233
- STAEformer: https://arxiv.org/abs/2308.10425
- MambaTS: https://arxiv.org/abs/2405.16440
- SOR-Mamba: https://arxiv.org/abs/2410.23356
- CRS-Mamba (DASFAA 2025): https://dasfaa2025.github.io/paper/research/research_617_paper.pdf
- CPiRi (ICLR 2026): https://arxiv.org/abs/2601.20318
- Graph-Mamba: https://arxiv.org/abs/2402.00789
- Janossy Pooling: https://arxiv.org/abs/1811.01900
- Taming Local Effects in Graph-based Spatiotemporal Forecasting: https://arxiv.org/abs/2302.04071
- On the Regularization of Learnable Embeddings for Time Series Forecasting: https://arxiv.org/abs/2410.14630
- Exploring Progress in Multivariate Time Series Forecasting (BasicTS+): https://arxiv.org/abs/2310.06119
- Are Data Embeddings effective in time series forecasting?: https://arxiv.org/abs/2505.20716
- Timer-XL: https://arxiv.org/abs/2410.04803
