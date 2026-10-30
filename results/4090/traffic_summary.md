### Traffic, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3932 ± 0.0006 | 0.2686 ± 0.0005 | 3 | – | – |
| add | 0.3993 ± 0.0017 | 0.2668 ± 0.0003 | 3 | +1.53% (0/3 better) | worse |
| add-drop0.1 | 0.3882 ± 0.0026 | 0.2652 ± 0.0004 | 3 | -1.29% (3/3 better) | effective |
| add-drop0.3 | 0.3840 ± 0.0003 | 0.2650 ± 0.0002 | 3 | -2.35% (3/3 better) | effective |
| lowrank-r8 | 0.4056 ± 0.0018 | 0.2689 ± 0.0002 | 3 | +3.14% (0/3 better) | worse |

### Traffic, H=96, smamba, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3931 ± 0.0014 | 0.2651 ± 0.0016 | 3 | – | – |
| add | 0.3959 ± 0.0043 | 0.2613 ± 0.0016 | 3 | +0.71% (1/3 better) | unclear |
| add-drop0.1 | 0.3901 ± 0.0042 | 0.2598 ± 0.0007 | 3 | -0.75% (3/3 better) | marginal |
| add-drop0.3 | 0.3921 ± 0.0030 | 0.2618 ± 0.0009 | 3 | -0.26% (2/3 better) | unclear |
| lowrank-r8 | 0.4091 ± 0.0041 | 0.2641 ± 0.0022 | 3 | +4.09% (0/3 better) | worse |

### Traffic, H=96, smamba, tag `epochs10`, epochs=10

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3798 ± 0.0023 | 0.2582 ± 0.0006 | 3 | – | – |
| add | 0.3900 ± 0.0026 | 0.2568 ± 0.0011 | 3 | +2.68% (0/3 better) | worse |

### Traffic, H=96, smamba, scan order: shuffle, epochs=5

| variant | mse | mae | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.3975 ± 0.0016 | 0.2677 ± 0.0007 | 0.3902 ± 0.0015 | 0.3893 ± 0.0015 | 3 | – | – |
| add | 0.4082 ± 0.0046 | 0.2648 ± 0.0010 | 0.3984 ± 0.0034 | 0.3967 ± 0.0034 | 3 | +2.69% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Does the fixed scan order act as an identity? (S-Mamba, identity `add`)

| data | H | identity gain, fixed order | identity gain, shuffled order | shuffling cost without identity |
|---|---|---|---|---|
| Traffic | 96 | +0.71% (1/3) | +2.69% (0/3) | +1.13% (0/3) |


## Per-variable analysis (tools/per_variable.py)

### Traffic, H=96, itransformer, add, epochs 10, seeds [0, 1, 2], 862 variables

- test MSE change +1.53%; leaving out the most harmed 1% / 5% / 10%: -5.05% / -5.84% / -6.22%
- variables worse: 127 of 862; same variables harmed across seeds: Spearman +0.98
- Spearman of the per-variable test change with: val change +0.44; level shift +0.24; scale shift +0.23; val->test level shift +0.12
- most harmed (mean over seeds): 851 +243.9% (level -0.24, std 0.39), 800 +133.4% (level -0.04, std 0.72), 46 +121.8% (level -0.29, std 0.51), 282 +83.8% (level -0.01, std 0.35), 311 +81.9% (level -0.09, std 0.95), 472 +64.5% (level +1.34, std 1.92), 341 +56.6% (level +0.11, std 1.86), 518 +50.4% (level -0.08, std 0.86), 224 +47.7% (level -0.08, std 0.77), 44 +30.7% (level -0.83, std 0.31)

### Traffic, H=96, itransformer, add-drop0.1, epochs 10, seeds [0, 1, 2], 862 variables

- test MSE change -1.29%; leaving out the most harmed 1% / 5% / 10%: -4.90% / -5.48% / -5.73%
- variables worse: 106 of 862; same variables harmed across seeds: Spearman +0.96
- Spearman of the per-variable test change with: val change +0.44; level shift +0.22; scale shift +0.22; val->test level shift +0.11
- most harmed (mean over seeds): 851 +73.2% (level -0.24, std 0.39), 800 +63.7% (level -0.04, std 0.72), 472 +50.9% (level +1.34, std 1.92), 46 +47.7% (level -0.29, std 0.51), 311 +44.5% (level -0.09, std 0.95), 341 +35.6% (level +0.11, std 1.86), 518 +28.9% (level -0.08, std 0.86), 44 +21.2% (level -0.83, std 0.31), 224 +17.1% (level -0.08, std 0.77), 282 +16.9% (level -0.01, std 0.35)

### Traffic, H=96, itransformer, add-drop0.3, epochs 10, seeds [0, 1, 2], 862 variables

- test MSE change -2.35%; leaving out the most harmed 1% / 5% / 10%: -4.13% / -4.47% / -4.66%
- variables worse: 90 of 862; same variables harmed across seeds: Spearman +0.95
- Spearman of the per-variable test change with: val change +0.49; level shift +0.21; scale shift +0.21; val->test level shift +0.09
- most harmed (mean over seeds): 800 +43.2% (level -0.04, std 0.72), 472 +35.4% (level +1.34, std 1.92), 341 +24.5% (level +0.11, std 1.86), 851 +21.5% (level -0.24, std 0.39), 46 +20.8% (level -0.29, std 0.51), 44 +19.0% (level -0.83, std 0.31), 311 +17.0% (level -0.09, std 0.95), 692 +12.9% (level -0.17, std 0.89), 850 +12.6% (level +0.14, std 1.25), 722 +10.7% (level +0.17, std 2.65)

### Traffic, H=96, itransformer, lowrank-r8, epochs 10, seeds [0, 1, 2], 862 variables

- test MSE change +3.14%; leaving out the most harmed 1% / 5% / 10%: -3.33% / -4.04% / -4.37%
- variables worse: 153 of 862; same variables harmed across seeds: Spearman +0.93
- Spearman of the per-variable test change with: val change +0.41; level shift +0.21; scale shift +0.21; val->test level shift +0.09
- most harmed (mean over seeds): 800 +326.8% (level -0.04, std 0.72), 851 +248.7% (level -0.24, std 0.39), 46 +166.3% (level -0.29, std 0.51), 282 +108.3% (level -0.01, std 0.35), 341 +58.5% (level +0.11, std 1.86), 518 +39.3% (level -0.08, std 0.86), 44 +34.0% (level -0.83, std 0.31), 300 +29.6% (level -0.01, std 0.87), 840 +29.6% (level +4.52, std 11.67), 567 +26.0% (level +1.44, std 3.53)

### Traffic, H=96, smamba, add, epochs 5, seeds [0, 1, 2], 862 variables

- test MSE change +0.71%; leaving out the most harmed 1% / 5% / 10%: -6.42% / -7.59% / -8.05%
- variables worse: 115 of 862; same variables harmed across seeds: Spearman +0.89
- Spearman of the per-variable test change with: val change +0.51; level shift +0.32; scale shift +0.29; val->test level shift +0.22
- most harmed (mean over seeds): 851 +216.8% (level -0.24, std 0.39), 311 +113.7% (level -0.09, std 0.95), 282 +83.4% (level -0.01, std 0.35), 224 +81.7% (level -0.08, std 0.77), 472 +74.7% (level +1.34, std 1.92), 800 +57.7% (level -0.04, std 0.72), 341 +51.3% (level +0.11, std 1.86), 692 +45.5% (level -0.17, std 0.89), 518 +39.1% (level -0.08, std 0.86), 668 +33.1% (level +1.07, std 2.34)

### Traffic, H=96, smamba, add-drop0.1, epochs 5, seeds [0, 1, 2], 862 variables

- test MSE change -0.75%; leaving out the most harmed 1% / 5% / 10%: -6.75% / -7.72% / -8.14%
- variables worse: 93 of 862; same variables harmed across seeds: Spearman +0.90
- Spearman of the per-variable test change with: val change +0.49; level shift +0.31; scale shift +0.30; val->test level shift +0.23
- most harmed (mean over seeds): 851 +183.0% (level -0.24, std 0.39), 282 +88.6% (level -0.01, std 0.35), 472 +64.2% (level +1.34, std 1.92), 800 +57.1% (level -0.04, std 0.72), 311 +50.0% (level -0.09, std 0.95), 341 +43.3% (level +0.11, std 1.86), 692 +42.0% (level -0.17, std 0.89), 46 +36.0% (level -0.29, std 0.51), 224 +33.9% (level -0.08, std 0.77), 518 +32.3% (level -0.08, std 0.86)

### Traffic, H=96, smamba, add-drop0.3, epochs 5, seeds [0, 1, 2], 862 variables

- test MSE change -0.26%; leaving out the most harmed 1% / 5% / 10%: -5.77% / -6.64% / -7.06%
- variables worse: 106 of 862; same variables harmed across seeds: Spearman +0.92
- Spearman of the per-variable test change with: val change +0.46; level shift +0.30; scale shift +0.29; val->test level shift +0.19
- most harmed (mean over seeds): 851 +158.0% (level -0.24, std 0.39), 800 +73.5% (level -0.04, std 0.72), 282 +67.9% (level -0.01, std 0.35), 341 +49.6% (level +0.11, std 1.86), 472 +44.9% (level +1.34, std 1.92), 46 +44.1% (level -0.29, std 0.51), 692 +35.8% (level -0.17, std 0.89), 567 +26.4% (level +1.44, std 3.53), 311 +24.7% (level -0.09, std 0.95), 518 +20.4% (level -0.08, std 0.86)

### Traffic, H=96, smamba, lowrank-r8, epochs 5, seeds [0, 1, 2], 862 variables

- test MSE change +4.09%; leaving out the most harmed 1% / 5% / 10%: -3.84% / -4.76% / -5.17%
- variables worse: 140 of 862; same variables harmed across seeds: Spearman +0.82
- Spearman of the per-variable test change with: val change +0.46; level shift +0.29; scale shift +0.28; val->test level shift +0.17
- most harmed (mean over seeds): 851 +431.2% (level -0.24, std 0.39), 282 +281.8% (level -0.01, std 0.35), 800 +99.7% (level -0.04, std 0.72), 46 +98.5% (level -0.29, std 0.51), 341 +55.9% (level +0.11, std 1.86), 840 +34.7% (level +4.52, std 11.67), 724 +33.9% (level +0.79, std 3.06), 692 +33.0% (level -0.17, std 0.89), 472 +31.9% (level +1.34, std 1.92), 518 +30.9% (level -0.08, std 0.86)

### Traffic, H=96, smamba, add, tag `epochs10`, epochs 10, seeds [0, 1, 2], 862 variables

- test MSE change +2.68%; leaving out the most harmed 1% / 5% / 10%: -4.66% / -5.89% / -6.45%
- variables worse: 172 of 862; same variables harmed across seeds: Spearman +0.92
- Spearman of the per-variable test change with: val change +0.52; level shift +0.29; scale shift +0.25; val->test level shift +0.20
- most harmed (mean over seeds): 851 +217.7% (level -0.24, std 0.39), 311 +128.9% (level -0.09, std 0.95), 282 +94.4% (level -0.01, std 0.35), 224 +89.2% (level -0.08, std 0.77), 472 +86.1% (level +1.34, std 1.92), 341 +58.2% (level +0.11, std 1.86), 800 +52.7% (level -0.04, std 0.72), 518 +49.7% (level -0.08, std 0.86), 668 +36.8% (level +1.07, std 2.34), 692 +34.9% (level -0.17, std 0.89)

### Traffic, H=96, smamba, add, scan shuffle, epochs 5, seeds [0, 1, 2], 862 variables

- test MSE change +2.69%; leaving out the most harmed 1% / 5% / 10%: -5.56% / -6.68% / -7.14%
- variables worse: 122 of 862; same variables harmed across seeds: Spearman +0.94
- Spearman of the per-variable test change with: val change +0.51; level shift +0.28; scale shift +0.26; val->test level shift +0.19
- most harmed (mean over seeds): 851 +220.0% (level -0.24, std 0.39), 311 +122.6% (level -0.09, std 0.95), 800 +98.6% (level -0.04, std 0.72), 224 +87.5% (level -0.08, std 0.77), 282 +83.1% (level -0.01, std 0.35), 472 +75.5% (level +1.34, std 1.92), 341 +51.1% (level +0.11, std 1.86), 518 +43.6% (level -0.08, std 0.86), 668 +37.4% (level +1.07, std 2.34), 840 +35.3% (level +4.52, std 11.67)

