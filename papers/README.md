# papers

| 文件 | 内容 |
|---|---|
| [`related_work.md`](related_work.md) | 相关工作检索：身份嵌入的核心思路已有 ICML 2025 等工作，以及与本研究的逐项对照 |
| [`new_directions.md`](new_directions.md) | 第一轮方向检索：变量级漂移下的无标签逐变量路由（含 Traffic 先导分析） |
| [`new_directions_2.md`](new_directions_2.md) | 第二轮发散检索：13 个方向的拥挤程度与候选组合 A–F |
| [`theory.md`](theory.md) | 组合模型的理论推导：身份缺口、各模块的作用、偏差–方差、学习预算、漂移门控、扫描顺序 |
| [`theory_directions.md`](theory_directions.md) | 候选方向 A–F 的可行性：数学推导与沙盒模拟（结果在 `../results/sim/`） |
| [`application_direction.md`](application_direction.md) | 偏应用的方向：设备台账感知的低压馈线负荷预测（FeederBW），应用方向的拥挤程度、查重，以及台账统计与先导实验（结果在 `../results/feederbw_pilot/`） |
| [`model_direction.md`](model_direction.md) | 模型改进方案：可靠性门控的节点知识（归纳式节点知识编码器、知识条件的协变量一致分解、知识可靠性门控），逐模块查重与多数据集、多骨干的实验设计 |
| [`model_sandbox.md`](model_sandbox.md) | 上述模型的第一版实现（newpapercode `rnk/`）与 CPU 沙盒结果：合成数据 12 个变体 × 3 个种子，FeederBW 40 条馈线的两种划分（结果在 `../results/rnk_sandbox/`） |

参考文献 PDF 放在 `references/`，论文稿（LaTeX 源文件或导出的 PDF）放在 `manuscript/`。前期整理的参考论文（S-Mamba、GPS-Mamba、DyTimeNet、MPGTimer 等 10 篇）在 [`unforgettablerep/paperlib`](https://github.com/unforgettablerep/paperlib)。
