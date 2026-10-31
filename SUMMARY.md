# 研究总览（截至 2026-10-31）

本文件汇总已完成工作的要点和当前状态。详细过程和全部数字见 [`README.md`](README.md)（按时间顺序记录的实验日志）和 [`papers/`](papers/)。代码在 [`unforgettablerep/newpapercode`](https://github.com/unforgettablerep/newpapercode)。

## 1. 研究历程

| 阶段 | 内容 | 主要文件 |
|---|---|---|
| 一 | 变量身份嵌入：给 iTransformer / S-Mamba 的变量 token 加零初始化的可学习身份；快速实验、扫描顺序假设、消融与未见变量、8 个数据集 × 4 个预测长度的主表（实验 1–4） | README 实验 1–4；`results/4090/{quick_T96,order,ablation,newablation,main}.jsonl` |
| 二 | 诊断与扩展：Traffic 逐传感器分析、列顺序、身份学习率、全部数据集上的随机扫描顺序（实验 5–8） | README 实验 5–8；`results/4090/{traffic,perm,idlr,shuffle_main}.jsonl` |
| 三 | 超参数逐个预测长度核对官方脚本，发现 25 个组合与官方不同并重跑；身份 dropout（实验 9–10） | README 实验 9–10、"超参数核对"；`results/4090/{official,dropout}.jsonl` |
| 四 | 查重：身份嵌入的核心已有 ICML 2025 等工作，转向"有理论依据的新组合"；理论推导；方向检索 | `papers/related_work.md`、`papers/theory.md`、`papers/new_directions.md`、`papers/new_directions_2.md` |
| 五 | 各候选方向的可行性：数学推导 + 沙盒模拟 | `papers/theory_directions.md`；`results/sim/*.json` |

## 2. 已确立的结论

**实验结论（RTX 4090，3 个种子）**

1. **基线复现可信。** 官方设置下的基线与论文的差距：S-Mamba 30/30 组、iTransformer 31/32 组在 ±3% 以内。
2. **身份嵌入对 iTransformer 有效**，在变量多、差异大的数据集上：
   - Weather：所有长度都有效，−2.4% 至 −5.2%；身份学习率 ×10 后为 −1.6% 至 −8.7%；
   - Electricity：−4.2% 至 −7.7%。
   - 在 ETT、Exchange 上几乎没有作用。
3. **S-Mamba 的固定扫描顺序本身就是部分身份。**
   - 打乱顺序、不加身份时，Electricity 变差 3%–9%，Weather 变差 1.5%–5.8%；
   - 打乱后再加身份，收益分别为 −6.3% 至 −11.1% 和 −2.1% 至 −4.6%，与 iTransformer 相当（所有预测长度）。
4. **Traffic 上身份使 MSE 变差，原因是少数漂移传感器。**
   - 传感器 840 一个就占测试 MSE 的 15%–16%；
   - 在 86%–91% 的传感器上身份有帮助，MAE 也改善；
   - 身份 dropout 0.3 使 iTransformer 在所有长度上都不再变差。
5. **身份是直推式的**：它让未见变量变差 2.8%–4.9%（Electricity）；身份 dropout 可减轻到 0.7%–1.2%。
6. **学习预算决定了从零开始的参数能否被学到**（theory §5）。ETTh1、ETTh2、Exchange 上预算 B≈0.03–0.07，身份根本没有被学到。
7. **重跑一致性。**
   - ETT、Weather 重跑几乎完全确定（差异 ≤ 0.0014%）；
   - Electricity、Traffic 上的 S-Mamba 单个种子最大差 2.7%–3.6%，这两个数据集上 3% 以内的 S-Mamba 差异需要更多种子。

**理论与模拟结论**（`papers/theory.md`、`papers/theory_directions.md`）

1. **身份缺口**：置换等变模型的超额风险 = 给定视图后，不同变量条件均值的方差。实例归一化会放大这一缺口。
2. **动态组合的收益**：可靠性门控的全局–局部组合，收益 = 局部知识的价值 × 检测器的信息量（定理 A1 / 推论 A1）。合成数据验证：
   - 变量特有结构在窗口中不可见、且有漂移时，比最好的单一模型低 6%–28%，达到上限的 73%–98%；
   - 条件不满足时收益≈0，代价 ≤ 0.3%。
3. **门控阈值应按误报率（χ² 分位数）设定**，不能在验证集上选：验证期没有漂移时，验证集几乎总是选"不门控"。
4. **跨变量消息的可靠性加权必须与输出门控同时使用**：联合后合成数据上 −1.3% 至 −2.5%。
5. **区间预测**：按漂移分数分组的共形预测，在漂移反复出现时可以恢复覆盖率（0.70–0.77 → 0.86–0.90）；对新颖漂移需要在线校正。
6. **训练稳定性**：
   - 输出集成的收益恒等于模型间方差；
   - 权重平均只在共同起点下有效（模型汤 −1.1%），从头平均失败；
   - 在平均 MSE 下，重新加权损失不可能优于 ERM。

## 3. 被推翻或修正的结论

- "随机扫描顺序在 ETT 上普遍有效"：主要是旧超参数表下的正则化效应；官方设置下只在 ETTh1 上仍然有效。
- "ETT / Exchange 上身份没有作用，说明不需要身份"：主要原因是学习预算不足，身份没被学到。
- "变量越多身份越有用"：不成立（Traffic 是反例）。
- 原先直接堆叠模块的方案（`run_combo.sh`）已删除；身份嵌入、CN、CycleNet、随机顺序训练都已有人发表，只能作为基线。

## 4. 当前方向与下一步

**推荐主线**（`papers/theory_directions.md`）：

- 可靠性感知的多变量预测：
  - A：全局模型 + 局部专家，权重 = 无标签的状态后验 × 逐变量的 Bates–Granger 可靠性；
  - A2：同一后验对跨变量消息加权；
  - B：同一后验驱动的逐变量区间预测。
- 应用验证：跨电网层级的负荷数据（KIT 基准）+ 基础模型（方向 C）。
- 工程组件：模型汤 / EMA（方向 D）。

**待决定或待运行**：

| 事项 | 状态 |
|---|---|
| 按方向 A + A2 + B 实现真实模型（门控阈值改为固定 χ² 分位数；消息门控与输出门控联合；区间加在线校正） | 待开始 |
| `scripts/run_theory.sh`（检验 theory.md 的预测 P2–P6） | 已实现，未运行；其中的基线和局部专家运行在新主线中仍然有用 |
| `run_official.sh` 中 Traffic 上 S-Mamba 192–720 步的 35 次 | 未补齐（可选） |
| PEMS、KIT 负荷数据 | 需要获取数据 |
| 最终表格用 5 个种子 | 待做 |

## 5. 文件索引

**结果文件**（`results/4090/`，RTX 4090）

| 文件 | 实验 | 代码版本 | 汇总 |
|---|---|---|---|
| `quick_T96.jsonl` | 1 快速实验 | `ac1a2e5` | `quick_T96_summary.md` |
| `order.jsonl` | 2 扫描顺序 | `d668c79` | `order_summary.md` |
| `ablation.jsonl`、`newablation.jsonl` | 3 消融（两次） | `ac1a2e5` / `d668c79` | `ablation_summary.md`、`ablation_rerun_summary.md` |
| `main.jsonl`、`main_rerun_partial.jsonl` | 4 主表及部分重跑 | `ac1a2e5` / `a48f354` | `main_summary.md` |
| `traffic.jsonl` | 5 Traffic 诊断 | `a48f354` | `traffic_summary.md` |
| `perm.jsonl` | 6 列顺序 | `a48f354` | `perm_summary.md` |
| `idlr.jsonl` | 7 身份学习率 ×10 | `a48f354` | `idlr_summary.md` |
| `shuffle_main.jsonl` | 8 随机顺序主表 | `a48f354` | `shuffle_main_summary.md` |
| `official.jsonl` | 9 官方超参数重跑 | `13944c9` | `official_summary.md` |
| `dropout.jsonl` | 10 身份 dropout | `13944c9` | `dropout_summary.md` |

**模拟结果**：`results/sim/sim_{A,A2,B,D,E}.json`（newpapercode `e11261a`，`experiments_sim/`）。

**文档**（`papers/`）

| 文件 | 内容 |
|---|---|
| `related_work.md` | 与已有工作的逐项对照 |
| `new_directions.md`、`new_directions_2.md` | 方向检索 |
| `theory.md` | 组合模型的理论推导，以及身份、学习预算、门控、顺序的分析 |
| `theory_directions.md` | 各方向的可行性推导与沙盒模拟 |

**分析代码**：newpapercode `analysis/`（README 中数字的出处）、`tools/`（汇总、逐变量分析、漂移路由先导）。
