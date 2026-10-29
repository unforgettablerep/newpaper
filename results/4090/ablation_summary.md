### ETTh1, H=96, smamba, trained on 40% of variables

| variant | mse | mae | mse_seen | mse_unseen | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.4022 ± 0.0054 | 0.4171 ± 0.0028 | 0.4587 ± 0.0865 | 0.3598 ± 0.0742 | 3 | – | – |
| add | 0.4021 ± 0.0056 | 0.4170 ± 0.0029 | 0.4587 ± 0.0861 | 0.3597 ± 0.0742 | 3 | -0.01% (2/3 better) | unclear |
| add-drop0.3 | 0.4024 ± 0.0064 | 0.4172 ± 0.0036 | 0.4592 ± 0.0857 | 0.3598 ± 0.0753 | 3 | +0.05% (2/3 better) | unclear |

### ETTh1, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3870 ± 0.0015 | 0.4061 ± 0.0007 | 3 | – | – |
| add | 0.3870 ± 0.0015 | 0.4060 ± 0.0007 | 3 | +0.00% (2/3 better) | unclear |
| add-drop0.1 | 0.3870 ± 0.0016 | 0.4060 ± 0.0008 | 3 | +0.00% (2/3 better) | unclear |
| add-every | 0.3870 ± 0.0015 | 0.4060 ± 0.0008 | 3 | +0.01% (1/3 better) | unclear |
| add-lr10x | 0.3871 ± 0.0014 | 0.4057 ± 0.0008 | 3 | +0.04% (1/3 better) | unclear |
| lowrank-r32 | 0.3870 ± 0.0014 | 0.4059 ± 0.0007 | 3 | +0.00% (1/3 better) | unclear |
| lowrank-r8 | 0.3870 ± 0.0015 | 0.4061 ± 0.0007 | 3 | +0.02% (0/3 better) | worse |

### Electricity, H=96, smamba, trained on 40% of variables

| variant | mse | mae | mse_seen | mse_unseen | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.1715 ± 0.0013 | 0.2619 ± 0.0017 | 0.1445 ± 0.0143 | 0.1894 ± 0.0086 | 3 | – | – |
| add | 0.1748 ± 0.0020 | 0.2639 ± 0.0016 | 0.1388 ± 0.0153 | 0.1987 ± 0.0072 | 3 | +1.94% (0/3 better) | worse |
| add-drop0.3 | 0.1708 ± 0.0023 | 0.2616 ± 0.0018 | 0.1392 ± 0.0151 | 0.1917 ± 0.0073 | 3 | -0.43% (2/3 better) | unclear |

### Electricity, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1389 ± 0.0009 | 0.2360 ± 0.0011 | 3 | – | – |
| add | 0.1378 ± 0.0007 | 0.2346 ± 0.0006 | 3 | -0.77% (3/3 better) | marginal |
| add-drop0.1 | 0.1362 ± 0.0007 | 0.2339 ± 0.0005 | 3 | -1.93% (3/3 better) | effective |
| add-every | 0.1365 ± 0.0016 | 0.2340 ± 0.0007 | 3 | -1.72% (3/3 better) | effective |
| add-lr10x | 0.1387 ± 0.0013 | 0.2357 ± 0.0012 | 3 | -0.12% (2/3 better) | unclear |
| lowrank-r32 | 0.1377 ± 0.0017 | 0.2350 ± 0.0009 | 3 | -0.87% (2/3 better) | unclear |
| lowrank-r8 | 0.1377 ± 0.0012 | 0.2354 ± 0.0006 | 3 | -0.87% (2/3 better) | unclear |

### Weather, H=96, smamba, trained on 40% of variables

| variant | mse | mae | mse_seen | mse_unseen | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.2054 ± 0.0220 | 0.2384 ± 0.0089 | 0.1460 ± 0.0400 | 0.2420 ± 0.0158 | 3 | – | – |
| add | 0.2041 ± 0.0219 | 0.2376 ± 0.0084 | 0.1434 ± 0.0411 | 0.2414 ± 0.0144 | 3 | -0.65% (2/3 better) | unclear |
| add-drop0.3 | 0.2050 ± 0.0242 | 0.2389 ± 0.0103 | 0.1456 ± 0.0430 | 0.2416 ± 0.0167 | 3 | -0.28% (2/3 better) | unclear |

### Weather, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1674 ± 0.0023 | 0.2104 ± 0.0016 | 3 | – | – |
| add | 0.1643 ± 0.0010 | 0.2087 ± 0.0010 | 3 | -1.84% (3/3 better) | effective |
| add-drop0.1 | 0.1636 ± 0.0010 | 0.2082 ± 0.0010 | 3 | -2.25% (3/3 better) | effective |
| add-every | 0.1632 ± 0.0011 | 0.2082 ± 0.0012 | 3 | -2.50% (3/3 better) | effective |
| add-lr10x | 0.1576 ± 0.0008 | 0.2038 ± 0.0007 | 3 | -5.88% (3/3 better) | effective |
| lowrank-r32 | 0.1627 ± 0.0009 | 0.2077 ± 0.0011 | 3 | -2.84% (3/3 better) | effective |
| lowrank-r8 | 0.1649 ± 0.0003 | 0.2090 ± 0.0005 | 3 | -1.50% (3/3 better) | effective |

