# 发散检索：更多可做的方向（2026-10-31）

目标：寻找**新的组合、新的工作**，不局限于某一个基线模型。检索覆盖了 13 个方向，每个方向记录：是否拥挤、与我们已有发现的关系、可行性。细节来自检索摘要，引用前请核对原文。

## 已经拥挤、不建议作为主线

| 方向 | 代表工作（2025–2026） |
|---|---|
| 检索增强预测 | CRAFT（ICASSP 2026，逐通道检索）、SpecReTF、SERAF、SARAF、Tire 等（AISTATS 2026） |
| 频域 + Mamba | KARMA、SpectroMamba、AdaMamba、FLDmamba、MamNet、Affrm |
| 缺失传感器、免插补预测 | ChannelTokenFormer（ICLR 2026）、CRIB、MissTSM（TMLR 2026） |
| 由节点嵌入学习图结构 | GraFT（AAAI 2026）、Lite-STGNN、Time Tracker、MTGNN、ForecastGrapher |
| 测试时适应 / 测试时扩展 | TAFAS、PETSA、Chroma（模型组合）、*Diversified Scaling Inference in TSFMs*、SCALER（LLM） |
| 通道聚类 / 混合专家 | DUET（KDD 2025）、CCM（NeurIPS 2024） |
| 通道独立 / 依赖按变量切换 | DiAG、Adapformer、xCPD（ICLR 2026） |
| 变量顺序与 Mamba | MambaTS、SOR-Mamba、CRS-Mamba、CPiRi |

## 候选方向（按推荐程度排序）

### A. 可靠性门控的"全局–局部"组合（点预测）

- **组合**：把全局模型 G（通道独立模型，或预训练基础模型）和局部专家 L（变量 token 模型 + 身份 / CN / 周期）组合起来，权重为 $w_i(t)=q_i(t)\,w_i^{\mathrm{BG}}$：
  - $w_i^{\mathrm{BG}}$：在验证集上按变量估计的 Bates–Granger 权重；
  - $q_i(t)$：无标签的状态持续后验（theory §6）。
- **依据**：theory §4、§6；Traffic 先导结果为 +1.5% → −3.5%（iTransformer），+0.7% → −4.6%（S-Mamba）。
- **查重**：全局–局部组合已有静态权重的工作（Montero-Manso & Hyndman；Flexible global forecast combinations）；没有找到动态、按变量、不需要标签的权重。
- **可行性**：高，现有代码可直接扩展。

### B. 由同一个可靠性后验驱动的逐变量区间预测（与 A 组成一个统一框架）

- **组合**：A 中的 $q_i(t)$ 同时用于共形预测（conformal）的区间校准。变量处于持续状态时，用该变量自己的校准残差；后验低时，区间向全局或漂移后的校准分布加宽。也就是"状态条件化的逐变量共形预测"。
- **依据**：电网和交通调度需要区间预测；Traffic 上误差集中在少数漂移传感器，统一宽度的区间对它们覆盖不足，对其他变量又过宽。
- **查重**：2026 年自适应共形预测很活跃（SPACE、Gate-Localized CP、Drift-Aware Spectral CP、Bias-Corrected ACI），但没有找到"用逐变量、无标签的状态后验来调节多变量深度预测器区间"的工作。
- **可行性**：高。这是事后方法，不需要重新训练，只需记录逐窗口残差（小幅改代码）。
- **价值**：A + B 可以形成一篇完整的论文："可靠性感知的多变量预测：点预测与区间预测统一于同一个变量级状态后验"。

### C. 应用导向：跨电网层级的负荷预测（外生变量 + 基础模型 + 专家）

- **数据**：KIT 的负荷预测基准（arXiv 2607.15705）。它包括输电系统运营商控制区、低压馈线、单个用户三个层级，数据公开并有代码。论文报告 Transformer 类方法比传统方法误差低 6.6%–10.7%，**Chronos-2 零样本有竞争力，但抓不住特殊事件**。
- **组合**：Chronos-2（全局、稳健、可处理新节点）+ 数据集训练的专家（含天气 / 日历外生变量）+ 方向 A 的门控。门控在特殊事件（节假日、极端天气）时倾向专家，在节点漂移或新节点时倾向全局模型。
- **查重**：没有找到"基础模型 + 专家 + 按事件 / 漂移门控"用于负荷预测的工作。
- **可行性**：中。需要下载新数据、在代码中加入外生变量；Chronos-2 需要安装和下载权重。这些用户层级的数据不在基础模型的常见训练集中，泄露风险比 ETT、Electricity 小，但仍需核对。
- **价值**：应用故事最强，可以作为方向 A + B 的应用验证。

### D. 训练稳定性：权重平均 / 模型汤用于长期预测

- **依据**：我们测得 Electricity、Traffic 上 S-Mamba 的重跑差异最大达 3.6%，3 个种子下 1%–2% 的差异无法判断。
- **组合**：沿训练轨迹做 SWA / EMA；或者从同一个检查点出发、用不同数据顺序微调若干份后取权重平均（模型汤需要共同起点）。
- **查重**：没有找到针对时间序列预测的权重平均研究。
- **可行性**：很高，几十行代码。
- **局限**：新意偏工程，更适合作为 A 的稳定性组件，而不是单独成文。

### E. 变量级稳健训练（误差被少数变量主导）

- **依据**：Traffic 上单个传感器占测试 MSE 的 16%（实验 5），训练损失很可能也被这类变量主导。
- **组合**：跨变量的分组分布稳健优化（group DRO）或逐变量归一化损失，再结合方向 A 的可靠性。
- **查重**：没有找到逐通道损失再平衡的工作；但 2026 年已有按可靠性做变量级梯度手术的工作（*Not All Variables Agree*，arXiv 2609.08554），重叠度中等。
- **风险**：最终仍按 MSE 评价，再平衡可能损害总 MSE。

### F. Koopman + Mamba 处理非平稳

- **查重**：Koopa（NeurIPS 2023）、KNF；Mamba + Koopman 只有应用型的 PAKMamba（负荷预测）。没有找到面向通用长期预测基准的工作。
- **评价**：属于已有思路的组合，新意中等偏低。

## 建议

- **主线**：A + B，即"可靠性感知的点预测与区间预测"。两者共用同一个由理论推出的变量级状态后验，与我们已有的推导和实验结果衔接最紧，新意也最清楚。
- **应用验证**：用 C（跨电网层级负荷数据 + Chronos-2）做应用验证；这一步需要新的数据和外生变量支持。
- **工程组件**：把 D 作为提高稳定性的组件。
- **暂不做**：E、F 作为备选。

## 来源

- CRAFT（Channel-wise Retrieval）: https://arxiv.org/abs/2604.05543
- SARAF: https://arxiv.org/abs/2606.04135 ; SpecReTF: https://arxiv.org/abs/2606.19412 ; SERAF: https://arxiv.org/abs/2606.14941 ; Retrieval Augmented Time Series Forecasting (AISTATS 2026): https://proceedings.mlr.press/v300/tire26a.html
- KARMA: https://arxiv.org/abs/2506.08939 ; FLDmamba: https://arxiv.org/abs/2507.12803 ; AdaMamba: https://arxiv.org/abs/2604.23239
- ChannelTokenFormer: https://arxiv.org/abs/2506.08660 ; CRIB: https://arxiv.org/abs/2509.23494 ; MissTSM: https://arxiv.org/abs/2502.15785
- GraFT (AAAI 2026): https://ojs.aaai.org/index.php/AAAI/article/view/40029 ; Lite-STGNN: https://arxiv.org/abs/2512.17453 ; Time Tracker: https://arxiv.org/abs/2505.15151
- Chroma（Test-Time Efficient Pretrained Model Portfolios）: https://arxiv.org/abs/2510.06419 ; Diversified Scaling Inference in TSFMs: https://arxiv.org/abs/2601.17376 ; SCALER: https://arxiv.org/abs/2608.08675
- DUET (KDD 2025): https://arxiv.org/abs/2412.10859
- Montero-Manso & Hyndman: https://arxiv.org/abs/2008.00444 ; Flexible global forecast combinations: https://arxiv.org/abs/2207.07318
- SPACE: https://arxiv.org/abs/2608.17333 ; Gate-Localized Conformal Prediction: https://arxiv.org/abs/2607.23165 ; Drift-Aware Spectral Conformal Prediction: https://arxiv.org/abs/2606.15953 ; Bias-Corrected ACI: https://arxiv.org/abs/2604.13253
- Benchmark for Electrical Load Forecasting Across Grid Levels: https://arxiv.org/abs/2607.15705
- Hierarchical forecasting for energy: https://arxiv.org/abs/2501.16086 ; https://arxiv.org/abs/2302.03978
- Model soups: https://arxiv.org/abs/2203.05482 ; When, Where and Why to Average Weights?: https://arxiv.org/abs/2502.06761
- Not All Variables Agree (reliability-aware gradient surgery): https://arxiv.org/abs/2609.08554 ; DBLoss: https://arxiv.org/abs/2510.23672 ; Patch-wise Structural Loss: https://arxiv.org/abs/2503.00877
- Koopa: https://ise.thss.tsinghua.edu.cn/~mlong/doc/Koopa-nips23.pdf ; KNF: https://arxiv.org/abs/2210.03675 ; DMamba: https://arxiv.org/abs/2602.09081
- TimeXer: https://arxiv.org/abs/2402.19072
