### ETTh1, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3881 ± 0.0006 | 0.4058 ± 0.0006 | 3 | – | – |
| add | 0.3879 ± 0.0006 | 0.4057 ± 0.0006 | 3 | -0.05% (3/3 better) | marginal |
| add-lr10x | 0.3872 ± 0.0005 | 0.4055 ± 0.0004 | 3 | -0.22% (3/3 better) | marginal |

### ETTh1, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3870 ± 0.0015 | 0.4061 ± 0.0007 | 3 | – | – |
| add | 0.3870 ± 0.0015 | 0.4060 ± 0.0007 | 3 | +0.00% (2/3 better) | unclear |
| add-lr10x | 0.3871 ± 0.0014 | 0.4057 ± 0.0008 | 3 | +0.04% (1/3 better) | unclear |

### ETTh1, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4434 ± 0.0040 | 0.4374 ± 0.0026 | 3 | – | – |
| add | 0.4433 ± 0.0039 | 0.4373 ± 0.0026 | 3 | -0.03% (3/3 better) | marginal |
| add-lr10x | 0.4425 ± 0.0035 | 0.4367 ± 0.0018 | 3 | -0.20% (3/3 better) | marginal |

### ETTh1, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4422 ± 0.0006 | 0.4390 ± 0.0002 | 3 | – | – |
| add | 0.4423 ± 0.0006 | 0.4389 ± 0.0002 | 3 | +0.01% (0/3 better) | worse |
| add-lr10x | 0.4422 ± 0.0003 | 0.4383 ± 0.0002 | 3 | -0.00% (1/3 better) | unclear |

### ETTh1, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4831 ± 0.0019 | 0.4584 ± 0.0014 | 3 | – | – |
| add | 0.4844 ± 0.0026 | 0.4590 ± 0.0022 | 3 | +0.28% (1/3 better) | unclear |
| add-lr10x | 0.4843 ± 0.0021 | 0.4576 ± 0.0012 | 3 | +0.25% (2/3 better) | unclear |

### ETTh1, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4960 ± 0.0007 | 0.4707 ± 0.0008 | 3 | – | – |
| add | 0.4963 ± 0.0008 | 0.4707 ± 0.0009 | 3 | +0.05% (0/3 better) | worse |
| add-lr10x | 0.4979 ± 0.0012 | 0.4708 ± 0.0013 | 3 | +0.37% (0/3 better) | worse |

### ETTh1, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4958 ± 0.0032 | 0.4871 ± 0.0020 | 3 | – | – |
| add | 0.4927 ± 0.0037 | 0.4849 ± 0.0031 | 3 | -0.63% (2/3 better) | unclear |
| add-lr10x | 0.4933 ± 0.0094 | 0.4833 ± 0.0053 | 3 | -0.50% (1/3 better) | unclear |

### ETTh1, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.5161 ± 0.0046 | 0.5019 ± 0.0021 | 3 | – | – |
| add | 0.5155 ± 0.0048 | 0.5012 ± 0.0021 | 3 | -0.11% (3/3 better) | marginal |
| add-lr10x | 0.5091 ± 0.0047 | 0.4958 ± 0.0026 | 3 | -1.36% (2/3 better) | unclear |

### ETTh2, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2997 ± 0.0004 | 0.3498 ± 0.0002 | 3 | – | – |
| add | 0.2994 ± 0.0001 | 0.3497 ± 0.0003 | 3 | -0.11% (2/3 better) | unclear |
| add-lr10x | 0.2989 ± 0.0020 | 0.3501 ± 0.0010 | 3 | -0.28% (2/3 better) | unclear |

### ETTh2, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3004 ± 0.0061 | 0.3515 ± 0.0042 | 3 | – | – |
| add | 0.3000 ± 0.0063 | 0.3514 ± 0.0043 | 3 | -0.13% (3/3 better) | marginal |
| add-lr10x | 0.3010 ± 0.0067 | 0.3519 ± 0.0046 | 3 | +0.22% (2/3 better) | unclear |

### ETTh2, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3793 ± 0.0016 | 0.3983 ± 0.0009 | 3 | – | – |
| add | 0.3788 ± 0.0017 | 0.3982 ± 0.0009 | 3 | -0.11% (3/3 better) | marginal |
| add-lr10x | 0.3800 ± 0.0016 | 0.4006 ± 0.0015 | 3 | +0.20% (1/3 better) | unclear |

### ETTh2, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3794 ± 0.0047 | 0.3995 ± 0.0013 | 3 | – | – |
| add | 0.3791 ± 0.0049 | 0.3996 ± 0.0013 | 3 | -0.08% (3/3 better) | marginal |
| add-lr10x | 0.3863 ± 0.0023 | 0.4032 ± 0.0024 | 3 | +1.82% (1/3 better) | unclear |

### ETTh2, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4225 ± 0.0021 | 0.4324 ± 0.0012 | 3 | – | – |
| add | 0.4223 ± 0.0020 | 0.4326 ± 0.0013 | 3 | -0.04% (3/3 better) | marginal |
| add-lr10x | 0.4247 ± 0.0040 | 0.4360 ± 0.0018 | 3 | +0.53% (1/3 better) | unclear |

### ETTh2, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4264 ± 0.0039 | 0.4358 ± 0.0032 | 3 | – | – |
| add | 0.4266 ± 0.0037 | 0.4361 ± 0.0029 | 3 | +0.04% (1/3 better) | unclear |
| add-lr10x | 0.4298 ± 0.0015 | 0.4389 ± 0.0017 | 3 | +0.81% (0/3 better) | worse |

### ETTh2, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4378 ± 0.0100 | 0.4514 ± 0.0055 | 3 | – | – |
| add | 0.4369 ± 0.0099 | 0.4513 ± 0.0055 | 3 | -0.19% (1/3 better) | unclear |
| add-lr10x | 0.4485 ± 0.0064 | 0.4585 ± 0.0023 | 3 | +2.47% (1/3 better) | unclear |

### ETTh2, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4319 ± 0.0043 | 0.4488 ± 0.0030 | 3 | – | – |
| add | 0.4323 ± 0.0041 | 0.4490 ± 0.0029 | 3 | +0.10% (1/3 better) | unclear |
| add-lr10x | 0.4407 ± 0.0031 | 0.4538 ± 0.0020 | 3 | +2.05% (0/3 better) | worse |

### ETTm1, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3415 ± 0.0007 | 0.3758 ± 0.0005 | 3 | – | – |
| add | 0.3357 ± 0.0022 | 0.3715 ± 0.0016 | 3 | -1.68% (3/3 better) | effective |
| add-lr10x | 0.3288 ± 0.0011 | 0.3655 ± 0.0008 | 3 | -3.72% (3/3 better) | effective |

### ETTm1, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3309 ± 0.0010 | 0.3668 ± 0.0006 | 3 | – | – |
| add | 0.3303 ± 0.0010 | 0.3662 ± 0.0006 | 3 | -0.16% (3/3 better) | marginal |
| add-lr10x | 0.3293 ± 0.0008 | 0.3651 ± 0.0006 | 3 | -0.47% (3/3 better) | marginal |

### ETTm1, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3815 ± 0.0006 | 0.3946 ± 0.0004 | 3 | – | – |
| add | 0.3790 ± 0.0009 | 0.3929 ± 0.0006 | 3 | -0.67% (3/3 better) | marginal |
| add-lr10x | 0.3714 ± 0.0022 | 0.3890 ± 0.0017 | 3 | -2.65% (3/3 better) | effective |

### ETTm1, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3770 ± 0.0006 | 0.3922 ± 0.0006 | 3 | – | – |
| add | 0.3768 ± 0.0005 | 0.3919 ± 0.0006 | 3 | -0.06% (3/3 better) | marginal |
| add-lr10x | 0.3777 ± 0.0012 | 0.3927 ± 0.0011 | 3 | +0.18% (1/3 better) | unclear |

### ETTm1, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4173 ± 0.0006 | 0.4179 ± 0.0007 | 3 | – | – |
| add | 0.4149 ± 0.0009 | 0.4164 ± 0.0006 | 3 | -0.58% (3/3 better) | marginal |
| add-lr10x | 0.4092 ± 0.0013 | 0.4145 ± 0.0005 | 3 | -1.92% (3/3 better) | effective |

### ETTm1, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4168 ± 0.0034 | 0.4188 ± 0.0016 | 3 | – | – |
| add | 0.4164 ± 0.0035 | 0.4185 ± 0.0017 | 3 | -0.10% (3/3 better) | marginal |
| add-lr10x | 0.4168 ± 0.0042 | 0.4191 ± 0.0022 | 3 | +0.00% (1/3 better) | unclear |

### ETTm1, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4903 ± 0.0017 | 0.4577 ± 0.0005 | 3 | – | – |
| add | 0.4877 ± 0.0015 | 0.4560 ± 0.0011 | 3 | -0.53% (3/3 better) | marginal |
| add-lr10x | 0.4856 ± 0.0022 | 0.4561 ± 0.0015 | 3 | -0.96% (3/3 better) | marginal |

### ETTm1, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4880 ± 0.0043 | 0.4585 ± 0.0025 | 3 | – | – |
| add | 0.4918 ± 0.0050 | 0.4607 ± 0.0028 | 3 | +0.78% (1/3 better) | unclear |
| add-lr10x | 0.4899 ± 0.0047 | 0.4596 ± 0.0025 | 3 | +0.40% (1/3 better) | unclear |

### ETTm2, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1847 ± 0.0009 | 0.2697 ± 0.0010 | 3 | – | – |
| add | 0.1846 ± 0.0008 | 0.2697 ± 0.0011 | 3 | -0.07% (2/3 better) | unclear |
| add-lr10x | 0.1843 ± 0.0009 | 0.2705 ± 0.0010 | 3 | -0.21% (3/3 better) | marginal |

### ETTm2, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1795 ± 0.0026 | 0.2637 ± 0.0028 | 3 | – | – |
| add | 0.1794 ± 0.0027 | 0.2636 ± 0.0029 | 3 | -0.09% (3/3 better) | marginal |
| add-lr10x | 0.1783 ± 0.0029 | 0.2624 ± 0.0031 | 3 | -0.68% (3/3 better) | marginal |

### ETTm2, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2516 ± 0.0011 | 0.3123 ± 0.0011 | 3 | – | – |
| add | 0.2514 ± 0.0012 | 0.3123 ± 0.0012 | 3 | -0.06% (2/3 better) | unclear |
| add-lr10x | 0.2495 ± 0.0015 | 0.3107 ± 0.0019 | 3 | -0.84% (3/3 better) | marginal |

### ETTm2, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2498 ± 0.0018 | 0.3100 ± 0.0007 | 3 | – | – |
| add | 0.2507 ± 0.0020 | 0.3103 ± 0.0010 | 3 | +0.35% (1/3 better) | unclear |
| add-lr10x | 0.2516 ± 0.0027 | 0.3105 ± 0.0011 | 3 | +0.73% (1/3 better) | unclear |

### ETTm2, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3153 ± 0.0021 | 0.3516 ± 0.0010 | 3 | – | – |
| add | 0.3149 ± 0.0020 | 0.3514 ± 0.0010 | 3 | -0.10% (3/3 better) | marginal |
| add-lr10x | 0.3139 ± 0.0019 | 0.3508 ± 0.0014 | 3 | -0.42% (3/3 better) | marginal |

### ETTm2, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3109 ± 0.0010 | 0.3480 ± 0.0008 | 3 | – | – |
| add | 0.3112 ± 0.0012 | 0.3482 ± 0.0008 | 3 | +0.09% (0/3 better) | worse |
| add-lr10x | 0.3154 ± 0.0034 | 0.3501 ± 0.0009 | 3 | +1.44% (0/3 better) | worse |

### ETTm2, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4117 ± 0.0024 | 0.4059 ± 0.0021 | 3 | – | – |
| add | 0.4119 ± 0.0028 | 0.4058 ± 0.0018 | 3 | +0.04% (2/3 better) | unclear |
| add-lr10x | 0.4116 ± 0.0018 | 0.4060 ± 0.0013 | 3 | -0.03% (2/3 better) | unclear |

### ETTm2, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4103 ± 0.0022 | 0.4045 ± 0.0016 | 3 | – | – |
| add | 0.4107 ± 0.0025 | 0.4047 ± 0.0017 | 3 | +0.10% (0/3 better) | worse |
| add-lr10x | 0.4205 ± 0.0068 | 0.4079 ± 0.0019 | 3 | +2.48% (0/3 better) | worse |

### Electricity, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1482 ± 0.0003 | 0.2398 ± 0.0001 | 3 | – | – |
| add | 0.1368 ± 0.0004 | 0.2326 ± 0.0003 | 3 | -7.74% (3/3 better) | effective |

### Electricity, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1391 ± 0.0006 | 0.2360 ± 0.0008 | 3 | – | – |
| add | 0.1365 ± 0.0013 | 0.2342 ± 0.0014 | 3 | -1.90% (3/3 better) | effective |

### Electricity, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1649 ± 0.0004 | 0.2562 ± 0.0003 | 3 | – | – |
| add | 0.1565 ± 0.0019 | 0.2512 ± 0.0019 | 3 | -5.11% (3/3 better) | effective |

### Electricity, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1606 ± 0.0023 | 0.2579 ± 0.0026 | 3 | – | – |
| add | 0.1595 ± 0.0005 | 0.2568 ± 0.0005 | 3 | -0.67% (2/3 better) | unclear |

### Electricity, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1792 ± 0.0016 | 0.2718 ± 0.0008 | 3 | – | – |
| add | 0.1717 ± 0.0019 | 0.2682 ± 0.0024 | 3 | -4.17% (3/3 better) | effective |

### Electricity, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1774 ± 0.0016 | 0.2745 ± 0.0021 | 3 | – | – |
| add | 0.1729 ± 0.0017 | 0.2712 ± 0.0018 | 3 | -2.55% (3/3 better) | effective |

### Electricity, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2146 ± 0.0096 | 0.3028 ± 0.0072 | 3 | – | – |
| add | 0.1992 ± 0.0025 | 0.2931 ± 0.0037 | 3 | -7.08% (3/3 better) | effective |

### Electricity, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2022 ± 0.0027 | 0.2974 ± 0.0016 | 3 | – | – |
| add | 0.1965 ± 0.0032 | 0.2916 ± 0.0006 | 3 | -2.81% (3/3 better) | effective |

### Exchange, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.0874 ± 0.0006 | 0.2077 ± 0.0011 | 3 | – | – |
| add | 0.0875 ± 0.0005 | 0.2078 ± 0.0010 | 3 | +0.13% (0/3 better) | worse |
| add-lr10x | 0.0879 ± 0.0005 | 0.2085 ± 0.0009 | 3 | +0.63% (0/3 better) | worse |

### Exchange, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.0865 ± 0.0003 | 0.2071 ± 0.0003 | 3 | – | – |
| add | 0.0866 ± 0.0002 | 0.2072 ± 0.0002 | 3 | +0.06% (1/3 better) | unclear |
| add-lr10x | 0.0872 ± 0.0001 | 0.2080 ± 0.0000 | 3 | +0.70% (0/3 better) | worse |

### Exchange, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1797 ± 0.0013 | 0.3030 ± 0.0011 | 3 | – | – |
| add | 0.1804 ± 0.0013 | 0.3035 ± 0.0010 | 3 | +0.36% (0/3 better) | worse |
| add-lr10x | 0.1832 ± 0.0013 | 0.3063 ± 0.0011 | 3 | +1.95% (0/3 better) | worse |

### Exchange, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1814 ± 0.0003 | 0.3033 ± 0.0001 | 3 | – | – |
| add | 0.1812 ± 0.0016 | 0.3031 ± 0.0015 | 3 | -0.14% (1/3 better) | unclear |
| add-lr10x | 0.1842 ± 0.0013 | 0.3061 ± 0.0013 | 3 | +1.53% (0/3 better) | worse |

### Exchange, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3339 ± 0.0033 | 0.4195 ± 0.0022 | 3 | – | – |
| add | 0.3343 ± 0.0014 | 0.4195 ± 0.0008 | 3 | +0.12% (1/3 better) | unclear |
| add-lr10x | 0.3432 ± 0.0065 | 0.4256 ± 0.0042 | 3 | +2.76% (0/3 better) | worse |

### Exchange, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3304 ± 0.0014 | 0.4165 ± 0.0010 | 3 | – | – |
| add | 0.3324 ± 0.0015 | 0.4177 ± 0.0011 | 3 | +0.60% (0/3 better) | worse |
| add-lr10x | 0.3400 ± 0.0010 | 0.4231 ± 0.0008 | 3 | +2.92% (0/3 better) | worse |

### Exchange, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.8548 ± 0.0178 | 0.7002 ± 0.0107 | 3 | – | – |
| add | 0.8568 ± 0.0202 | 0.7015 ± 0.0117 | 3 | +0.23% (1/3 better) | unclear |
| add-lr10x | 0.8699 ± 0.0048 | 0.7051 ± 0.0018 | 3 | +1.81% (1/3 better) | unclear |

### Exchange, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.8580 ± 0.0013 | 0.6981 ± 0.0008 | 3 | – | – |
| add | 0.8622 ± 0.0013 | 0.6997 ± 0.0006 | 3 | +0.49% (0/3 better) | worse |
| add-lr10x | 0.8915 ± 0.0054 | 0.7127 ± 0.0022 | 3 | +3.91% (0/3 better) | worse |

### Traffic, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3935 ± 0.0007 | 0.2688 ± 0.0007 | 3 | – | – |
| add | 0.3996 ± 0.0014 | 0.2667 ± 0.0003 | 3 | +1.54% (0/3 better) | worse |

### Traffic, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3897 ± 0.0058 | 0.2644 ± 0.0024 | 3 | – | – |
| add | 0.4000 ± 0.0055 | 0.2621 ± 0.0005 | 3 | +2.66% (0/3 better) | worse |

### Traffic, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4122 ± 0.0007 | 0.2769 ± 0.0006 | 3 | – | – |
| add | 0.4287 ± 0.0020 | 0.2778 ± 0.0004 | 3 | +4.00% (0/3 better) | worse |

### Traffic, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4035 ± 0.0018 | 0.2732 ± 0.0013 | 3 | – | – |
| add | 0.4158 ± 0.0017 | 0.2718 ± 0.0009 | 3 | +3.06% (0/3 better) | worse |

### Traffic, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4237 ± 0.0011 | 0.2827 ± 0.0002 | 3 | – | – |
| add | 0.4447 ± 0.0021 | 0.2840 ± 0.0006 | 3 | +4.95% (0/3 better) | worse |

### Traffic, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4223 ± 0.0017 | 0.2799 ± 0.0009 | 3 | – | – |
| add | 0.4460 ± 0.0040 | 0.2809 ± 0.0018 | 3 | +5.60% (0/3 better) | worse |

### Traffic, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4579 ± 0.0010 | 0.3004 ± 0.0006 | 3 | – | – |
| add | 0.4864 ± 0.0013 | 0.3050 ± 0.0004 | 3 | +6.21% (0/3 better) | worse |

### Traffic, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4661 ± 0.0004 | 0.2994 ± 0.0006 | 3 | – | – |
| add | 0.4983 ± 0.0052 | 0.3020 ± 0.0014 | 3 | +6.90% (0/3 better) | worse |

### Weather, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1741 ± 0.0007 | 0.2137 ± 0.0010 | 3 | – | – |
| add | 0.1651 ± 0.0009 | 0.2080 ± 0.0005 | 3 | -5.16% (3/3 better) | effective |
| add-lr10x | 0.1589 ± 0.0008 | 0.2032 ± 0.0013 | 3 | -8.74% (3/3 better) | effective |

### Weather, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1674 ± 0.0023 | 0.2104 ± 0.0016 | 3 | – | – |
| add | 0.1643 ± 0.0010 | 0.2087 ± 0.0010 | 3 | -1.84% (3/3 better) | effective |
| add-lr10x | 0.1576 ± 0.0008 | 0.2038 ± 0.0007 | 3 | -5.88% (3/3 better) | effective |

### Weather, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2249 ± 0.0005 | 0.2579 ± 0.0010 | 3 | – | – |
| add | 0.2132 ± 0.0009 | 0.2523 ± 0.0009 | 3 | -5.19% (3/3 better) | effective |
| add-lr10x | 0.2093 ± 0.0005 | 0.2512 ± 0.0003 | 3 | -6.95% (3/3 better) | effective |

### Weather, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2153 ± 0.0005 | 0.2540 ± 0.0009 | 3 | – | – |
| add | 0.2129 ± 0.0011 | 0.2531 ± 0.0011 | 3 | -1.12% (3/3 better) | effective |
| add-lr10x | 0.2077 ± 0.0014 | 0.2506 ± 0.0008 | 3 | -3.54% (3/3 better) | effective |

### Weather, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2819 ± 0.0009 | 0.2995 ± 0.0012 | 3 | – | – |
| add | 0.2720 ± 0.0011 | 0.2954 ± 0.0007 | 3 | -3.51% (3/3 better) | effective |
| add-lr10x | 0.2671 ± 0.0013 | 0.2933 ± 0.0017 | 3 | -5.24% (3/3 better) | effective |

### Weather, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2738 ± 0.0012 | 0.2966 ± 0.0008 | 3 | – | – |
| add | 0.2711 ± 0.0009 | 0.2951 ± 0.0004 | 3 | -0.97% (3/3 better) | marginal |
| add-lr10x | 0.2686 ± 0.0024 | 0.2954 ± 0.0020 | 3 | -1.90% (3/3 better) | effective |

### Weather, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3586 ± 0.0021 | 0.3501 ± 0.0022 | 3 | – | – |
| add | 0.3502 ± 0.0004 | 0.3464 ± 0.0002 | 3 | -2.35% (3/3 better) | effective |
| add-lr10x | 0.3528 ± 0.0035 | 0.3484 ± 0.0037 | 3 | -1.63% (3/3 better) | effective |

### Weather, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3533 ± 0.0011 | 0.3492 ± 0.0010 | 3 | – | – |
| add | 0.3505 ± 0.0005 | 0.3480 ± 0.0004 | 3 | -0.80% (3/3 better) | marginal |
| add-lr10x | 0.3496 ± 0.0008 | 0.3475 ± 0.0001 | 3 | -1.05% (3/3 better) | effective |

