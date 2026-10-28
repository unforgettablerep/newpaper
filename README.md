# 变量身份嵌入研究：实验结果与论文

本仓库存放这项研究的**实验结果、分析和论文**；代码在 [`unforgettablerep/newpapercode`](https://github.com/unforgettablerep/newpapercode)。

**研究问题**：iTransformer 和 S-Mamba 把每个变量的整段历史映射成一个 token，再在变量之间做混合。历史窗口相似的变量会得到相似的 token，模型无法区分"它们是谁"。我们给每个变量的 token 加一个从 0 开始学习的身份向量：

```
h_i = Linear(x_i) + e_i ,   i = 1..N
```

并检验它在官方规模的 S-Mamba / iTransformer 上是否有效、为什么有效、以及在什么条件下有效。前期在 CPU 上用缩小模型做的探索（稀疏变量混合、顺序鲁棒训练、身份嵌入等）见代码仓库的 [`experiments_cpu/`](https://github.com/unforgettablerep/newpapercode/tree/main/experiments_cpu)，其中只有身份嵌入在每个种子上都稳定有效。

## 仓库约定

| 位置 | 内容 |
|---|---|
| `results/<机器>/<实验>.jsonl` | `run.py` 的原始输出，每行一次运行，包含全部配置和指标 |
| `results/<机器>/<实验>_summary.md` | 用代码仓库的 `tools/summarize.py` 生成的汇总表（均值 ± 标准差，逐种子配对比较与判定） |
| `papers/` | 参考论文与论文稿 |
| `README.md`（本文件） | 每批实验的设置、结果与分析，按时间顺序追加 |

每批结果都注明生成它的代码版本（newpapercode 的提交号）。判定标准在实验前就已固定：每个种子上都比无身份版本好、且配对平均 MSE 改善至少 1%，记为"有效"（effective）；每个种子都更好但不足 1%，记为"微弱"（marginal）；每个种子都更差，记为"变差"（worse）；其余为"不确定"（unclear）。

---

## 实验 1：快速实验（RTX 4090，预测 96 步）

- **文件**：[`results/4090/quick_T96.jsonl`](results/4090/quick_T96.jsonl)（36 次运行），汇总表见 [`quick_T96_summary.md`](results/4090/quick_T96_summary.md)
- **代码版本**：newpapercode `ac1a2e5`，即 `scripts/run_quick.sh`
- **设置**：ETTh1 / Weather / Electricity × {S-Mamba, iTransformer} × {无身份, 满秩身份 `add`} × 种子 0/1/2；回看 96 步；开启 TF32；身份学习率与主学习率相同（`--id-lr-mult 1`）

| 数据集 | 模型 | d_model | 层数 | d_state | 学习率 | batch | 最多轮数 | 超参来源 |
|---|---|---|---|---|---|---|---|---|
| ETTh1 | S-Mamba | 256 | 2 | 2 | 7e-5 | 32 | 10 | 官方脚本 |
| Weather | S-Mamba | 512 | 3 | 2 | 5e-5 | 32 | 5 | 官方脚本 |
| Electricity | S-Mamba | 512 | 3 | 16 | 1e-3 | 16 | 5 | 官方脚本 |
| ETTh1 | iTransformer | 256 | 2 | – | 1e-4 | 32 | 10 | 未核对 |
| Weather | iTransformer | 512 | 3 | – | 1e-4 | 32 | 10 | 未核对 |
| Electricity | iTransformer | 512 | 3 | – | 5e-4 | 16 | 10 | 未核对 |

### 1.1 基线复现了论文数字

| 基线 | 论文 MSE / MAE | 本次（3 个种子平均） |
|---|---|---|
| S-Mamba，ETTh1 | 0.386 / 0.405 | 0.3870 / 0.4061 |
| S-Mamba，Weather | 0.165 / 0.210 | 0.1674 / 0.2104 |
| S-Mamba，Electricity | 0.139 / 0.235 | 0.1389 / 0.2362 |
| iTransformer，ETTh1 | 0.386 / 0.405 | 0.3881 / 0.4058 |
| iTransformer，Weather | 0.174 / 0.214 | 0.1741 / 0.2137 |
| iTransformer，Electricity | 0.148 / 0.240 | 0.1482 / 0.2398 |

结构和训练协议是忠实的；标为"未核对"的 iTransformer 超参也复现了论文结果。这批结果没有记录实际使用的 Mamba 实现（后续代码版本已加入 `mamba_backend` 字段）。从 Electricity 上 S-Mamba 的峰值显存约 1.8 GB、每步约 29 ms 推断，用的是 `mamba_ssm` 的 CUDA 内核。

### 1.2 身份嵌入的效果

| 数据集 | 模型 | MSE：无 → 有 | MSE 变化 | MAE 变化 | 逐种子 MSE 变化 | 判定 |
|---|---|---|---|---|---|---|
| Electricity | iTransformer | 0.1482 → **0.1366** | **−7.82%** | −3.06% | −7.9%、−7.4%、−8.1% | 有效 |
| Electricity | S-Mamba | 0.1389 → 0.1370 | −1.36% | −0.61% | −0.7%、−1.3%、−2.1% | 有效 |
| Weather | iTransformer | 0.1741 → **0.1651** | **−5.16%** | −2.66% | −5.4%、−5.2%、−4.9% | 有效 |
| Weather | S-Mamba | 0.1674 → 0.1643 | −1.84% | −0.82% | −0.6%、−1.7%、−3.3% | 有效 |
| ETTh1 | iTransformer | 0.3881 → 0.3879 | −0.05% | −0.03% | 3 个种子都约为 0 | 微弱 |
| ETTh1 | S-Mamba | 0.3870 → 0.3870 | 0.00% | −0.03% | 3 个种子都约为 0 | 不确定 |

额外开销很小：参数增加 N×D（Electricity 上约 16 万，占 2.4%–3.4%）；训练时间增加 4%–16%，其中一部分是因为加了身份后验证误差下降得更久、早停更晚；显存几乎不变。

### 1.3 分析

1. **在两个多变量数据集上，身份嵌入对两种骨架都有效，每个种子都更好。** 这与前期 CPU 研究的结论一致；在只有 7 个变量、相关性较弱的 ETTh1 上没有作用，也与前期结论一致。
2. **iTransformer 的收益（−5% 至 −8%）远大于 S-Mamba（−1.4% 至 −1.8%）。** 一个可能的解释是：注意力层对变量的排列是等变的，除数值内容外没有任何办法区分变量；而 S-Mamba 按固定顺序扫描变量，变量在扫描序列中的位置本身已经携带了一部分"它是谁"的信息。前期研究发现 S-Mamba 对变量顺序敏感（打乱顺序后 Electricity 变差 1.2%–1.5%），也与这个解释相符。**这只是推测，尚未验证**；实验 2 将直接检验它。
3. **加了身份嵌入的 iTransformer 在 Electricity 上（0.1366）超过了原版 S-Mamba（0.1389），与 S-Mamba 加身份（0.1370）持平；在 Weather 上（0.1651）也超过了原版 S-Mamba（0.1674）。** 也就是说，S-Mamba 相对 iTransformer 的优势，很大一部分可以由身份嵌入补上。
4. **S-Mamba 的提升可能受训练设置限制。** Electricity 上 S-Mamba 加身份的 3 个种子都在第 5 轮（即最大轮数）取得最佳验证误差，可能还没训练充分。Weather 上 S-Mamba 的学习率只有 5e-5，而身份参数从 0 开始，Adam 每步大约只移动一个学习率的幅度，可能学不充分。消融实验中的"身份学习率 ×10"可以检验后一点。
5. **局限**：只有预测 96 步、3 个数据集、每组 3 个种子；没有 Traffic（862 个变量，预计最能检验身份嵌入）和 PEMS；iTransformer 的超参虽然复现了论文，但尚未与官方脚本逐项核对。

---

## 下一步实验

在代码仓库（newpapercode `d668c79` 及以后）中运行，把 `results/` 下生成的 JSONL 文件放到本仓库的 `results/4090/`。

| 顺序 | 命令 | 回答的问题 | 运行次数 |
|---|---|---|---|
| 1 | `bash scripts/run_order.sh` | S-Mamba 的固定扫描顺序是否起到了隐式身份的作用：随机扫描顺序训练时，身份嵌入的收益是否接近 iTransformer 的水平？（固定顺序的对照复用实验 1） | 18 |
| 2 | `bash scripts/run_ablation.sh` | 身份的形式（满秩 / 低秩）、位置（输入 / 每层）、身份 dropout、身份学习率 ×10，以及只用 40% 变量训练时对未见变量的影响 | 90 |
| 3 | `bash scripts/run_main.sh` | 全部数据集（含 Traffic、ETTh2/ETTm1/ETTm2、Exchange，有数据时含 PEMS）× 全部预测长度上的主表 | 最多 576 |

汇总命令（在代码仓库目录下运行）：`python tools/summarize.py <newpaper>/results/4090/quick_T96.jsonl results/order.jsonl`。实验 1 与实验 2 的结果一起汇总时，会额外输出"固定顺序 vs 随机顺序下的身份收益"对比表。
