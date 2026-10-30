### ETTh1, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3881 ± 0.0006 | 0.4058 ± 0.0006 | 3 | – | – |
| add | 0.3879 ± 0.0006 | 0.4057 ± 0.0006 | 3 | -0.05% (3/3 better) | marginal |

### ETTh1, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3870 ± 0.0015 | 0.4061 ± 0.0007 | 3 | – | – |
| add | 0.3870 ± 0.0015 | 0.4060 ± 0.0007 | 3 | +0.00% (2/3 better) | unclear |

### ETTh1, H=96, smamba, variables in random order 1

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3859 ± 0.0011 | 0.4048 ± 0.0008 | 3 | – | – |
| add | 0.3858 ± 0.0010 | 0.4047 ± 0.0008 | 3 | -0.02% (3/3 better) | marginal |

### ETTh1, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders | mae_orders | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.3853 ± 0.0010 | 0.4036 ± 0.0006 | 0.3821 ± 0.0003 | 0.4010 ± 0.0004 | 3 | – | – |
| add | 0.3852 ± 0.0010 | 0.4033 ± 0.0006 | 0.3820 ± 0.0003 | 0.4007 ± 0.0004 | 3 | -0.04% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Electricity, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1482 ± 0.0003 | 0.2398 ± 0.0001 | 3 | – | – |
| add | 0.1366 ± 0.0005 | 0.2325 ± 0.0004 | 3 | -7.82% (3/3 better) | effective |

### Electricity, H=96, smamba, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1389 ± 0.0008 | 0.2362 ± 0.0007 | 3 | – | – |
| add | 0.1370 ± 0.0017 | 0.2348 ± 0.0012 | 3 | -1.36% (3/3 better) | effective |

### Electricity, H=96, smamba, variables in random order 1, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1407 ± 0.0007 | 0.2366 ± 0.0011 | 3 | – | – |
| add | 0.1368 ± 0.0009 | 0.2333 ± 0.0008 | 3 | -2.77% (3/3 better) | effective |

### Electricity, H=96, smamba, scan order: shuffle, epochs=5

| variant | mse | mae | mse_orders | mae_orders | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.1527 ± 0.0003 | 0.2452 ± 0.0002 | 0.1425 ± 0.0003 | 0.2347 ± 0.0001 | 3 | – | – |
| add | 0.1364 ± 0.0007 | 0.2328 ± 0.0013 | 0.1332 ± 0.0011 | 0.2296 ± 0.0020 | 3 | -10.71% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Electricity, H=96, smamba, scan order: shuffle, tag `epochs10`, epochs=10

| variant | mse | mae | mse_orders | mae_orders | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.1532 ± 0.0013 | 0.2460 ± 0.0013 | 0.1418 ± 0.0005 | 0.2340 ± 0.0004 | 3 | – | – |
| add | 0.1358 ± 0.0019 | 0.2318 ± 0.0014 | 0.1326 ± 0.0006 | 0.2283 ± 0.0003 | 3 | -11.39% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Weather, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1741 ± 0.0007 | 0.2137 ± 0.0010 | 3 | – | – |
| add | 0.1651 ± 0.0009 | 0.2080 ± 0.0005 | 3 | -5.16% (3/3 better) | effective |

### Weather, H=96, smamba, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1674 ± 0.0023 | 0.2104 ± 0.0016 | 3 | – | – |
| add | 0.1643 ± 0.0010 | 0.2087 ± 0.0010 | 3 | -1.84% (3/3 better) | effective |

### Weather, H=96, smamba, variables in random order 1, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1706 ± 0.0014 | 0.2133 ± 0.0015 | 3 | – | – |
| add | 0.1664 ± 0.0008 | 0.2098 ± 0.0012 | 3 | -2.45% (3/3 better) | effective |

### Weather, H=96, smamba, scan order: shuffle, epochs=5

| variant | mse | mae | mse_orders | mae_orders | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.1771 ± 0.0019 | 0.2172 ± 0.0017 | 0.1776 ± 0.0021 | 0.2168 ± 0.0022 | 3 | – | – |
| add | 0.1689 ± 0.0008 | 0.2114 ± 0.0004 | 0.1686 ± 0.0005 | 0.2103 ± 0.0002 | 3 | -4.63% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Weather, H=96, smamba, scan order: shuffle, tag `epochs10`, epochs=10

| variant | mse | mae | mse_orders | mae_orders | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| none | 0.1767 ± 0.0016 | 0.2168 ± 0.0016 | 0.1772 ± 0.0023 | 0.2164 ± 0.0025 | 3 | – | – |
| add | 0.1681 ± 0.0006 | 0.2108 ± 0.0005 | 0.1678 ± 0.0003 | 0.2098 ± 0.0001 | 3 | -4.88% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Does the fixed scan order act as an identity? (S-Mamba, identity `add`)

| data | H | identity gain, fixed order | identity gain, shuffled order | shuffling cost without identity |
|---|---|---|---|---|
| ETTh1 | 96 | +0.00% (2/3) | -0.04% (3/3) | -0.42% (3/3) |
| Electricity | 96 | -1.36% (3/3) | -10.71% (3/3) | +9.93% (0/3) |
| Weather | 96 | -1.84% (3/3) | -4.63% (3/3) | +5.78% (0/3) |

