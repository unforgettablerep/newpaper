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

### ETTh1, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3853 ± 0.0010 | 0.4036 ± 0.0006 | 0.3818 ± 0.0003 | 0.3821 ± 0.0003 | 0.3818 ± 0.0002 | 3 | – | – |
| add | 0.3852 ± 0.0010 | 0.4033 ± 0.0006 | 0.3817 ± 0.0003 | 0.3820 ± 0.0003 | 0.3816 ± 0.0002 | 3 | -0.04% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh1, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4434 ± 0.0040 | 0.4374 ± 0.0026 | 3 | – | – |
| add | 0.4433 ± 0.0039 | 0.4373 ± 0.0026 | 3 | -0.03% (3/3 better) | marginal |

### ETTh1, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4422 ± 0.0006 | 0.4390 ± 0.0002 | 3 | – | – |
| add | 0.4423 ± 0.0006 | 0.4389 ± 0.0002 | 3 | +0.01% (0/3 better) | worse |

### ETTh1, H=192, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4388 ± 0.0009 | 0.4348 ± 0.0008 | 0.4330 ± 0.0005 | 0.4341 ± 0.0005 | 0.4337 ± 0.0003 | 3 | – | – |
| add | 0.4388 ± 0.0009 | 0.4345 ± 0.0008 | 0.4329 ± 0.0005 | 0.4340 ± 0.0005 | 0.4335 ± 0.0003 | 3 | -0.01% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh1, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4831 ± 0.0019 | 0.4584 ± 0.0014 | 3 | – | – |
| add | 0.4844 ± 0.0026 | 0.4590 ± 0.0022 | 3 | +0.28% (1/3 better) | unclear |

### ETTh1, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4960 ± 0.0007 | 0.4707 ± 0.0008 | 3 | – | – |
| add | 0.4963 ± 0.0008 | 0.4707 ± 0.0009 | 3 | +0.05% (0/3 better) | worse |

### ETTh1, H=336, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4839 ± 0.0014 | 0.4608 ± 0.0008 | 0.4748 ± 0.0007 | 0.4777 ± 0.0007 | 0.4774 ± 0.0008 | 3 | – | – |
| add | 0.4836 ± 0.0020 | 0.4603 ± 0.0014 | 0.4746 ± 0.0009 | 0.4774 ± 0.0011 | 0.4770 ± 0.0012 | 3 | -0.06% (1/3 better) | unclear |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh1, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4958 ± 0.0032 | 0.4871 ± 0.0020 | 3 | – | – |
| add | 0.4927 ± 0.0037 | 0.4849 ± 0.0031 | 3 | -0.63% (2/3 better) | unclear |

### ETTh1, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.5161 ± 0.0046 | 0.5019 ± 0.0021 | 3 | – | – |
| add | 0.5155 ± 0.0048 | 0.5012 ± 0.0021 | 3 | -0.11% (3/3 better) | marginal |

### ETTh1, H=720, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4966 ± 0.0041 | 0.4906 ± 0.0025 | 0.4816 ± 0.0043 | 0.4886 ± 0.0045 | 0.4887 ± 0.0065 | 3 | – | – |
| add | 0.4964 ± 0.0039 | 0.4902 ± 0.0023 | 0.4810 ± 0.0041 | 0.4881 ± 0.0043 | 0.4879 ± 0.0062 | 3 | -0.04% (2/3 better) | unclear |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh2, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2997 ± 0.0004 | 0.3498 ± 0.0002 | 3 | – | – |
| add | 0.2994 ± 0.0001 | 0.3497 ± 0.0003 | 3 | -0.11% (2/3 better) | unclear |

### ETTh2, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3004 ± 0.0061 | 0.3515 ± 0.0042 | 3 | – | – |
| add | 0.3000 ± 0.0063 | 0.3514 ± 0.0043 | 3 | -0.13% (3/3 better) | marginal |

### ETTh2, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.2957 ± 0.0014 | 0.3482 ± 0.0013 | 0.2946 ± 0.0014 | 0.2949 ± 0.0015 | 0.2947 ± 0.0014 | 3 | – | – |
| add | 0.2953 ± 0.0014 | 0.3479 ± 0.0013 | 0.2943 ± 0.0015 | 0.2945 ± 0.0016 | 0.2943 ± 0.0014 | 3 | -0.13% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh2, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3793 ± 0.0016 | 0.3983 ± 0.0009 | 3 | – | – |
| add | 0.3788 ± 0.0017 | 0.3982 ± 0.0009 | 3 | -0.11% (3/3 better) | marginal |

### ETTh2, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3794 ± 0.0047 | 0.3995 ± 0.0013 | 3 | – | – |
| add | 0.3791 ± 0.0049 | 0.3996 ± 0.0013 | 3 | -0.08% (3/3 better) | marginal |

### ETTh2, H=192, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3752 ± 0.0021 | 0.3975 ± 0.0015 | 0.3736 ± 0.0022 | 0.3737 ± 0.0023 | 0.3736 ± 0.0022 | 3 | – | – |
| add | 0.3747 ± 0.0022 | 0.3974 ± 0.0015 | 0.3731 ± 0.0022 | 0.3733 ± 0.0023 | 0.3731 ± 0.0022 | 3 | -0.13% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh2, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4225 ± 0.0021 | 0.4324 ± 0.0012 | 3 | – | – |
| add | 0.4223 ± 0.0020 | 0.4326 ± 0.0013 | 3 | -0.04% (3/3 better) | marginal |

### ETTh2, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4264 ± 0.0039 | 0.4358 ± 0.0032 | 3 | – | – |
| add | 0.4266 ± 0.0037 | 0.4361 ± 0.0029 | 3 | +0.04% (1/3 better) | unclear |

### ETTh2, H=336, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4245 ± 0.0021 | 0.4347 ± 0.0015 | 0.4223 ± 0.0009 | 0.4221 ± 0.0011 | 0.4219 ± 0.0011 | 3 | – | – |
| add | 0.4246 ± 0.0021 | 0.4349 ± 0.0014 | 0.4224 ± 0.0009 | 0.4222 ± 0.0011 | 0.4220 ± 0.0012 | 3 | +0.01% (1/3 better) | unclear |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh2, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4378 ± 0.0100 | 0.4514 ± 0.0055 | 3 | – | – |
| add | 0.4369 ± 0.0099 | 0.4513 ± 0.0055 | 3 | -0.19% (1/3 better) | unclear |

### ETTh2, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4319 ± 0.0043 | 0.4488 ± 0.0030 | 3 | – | – |
| add | 0.4323 ± 0.0041 | 0.4490 ± 0.0029 | 3 | +0.10% (1/3 better) | unclear |

### ETTh2, H=720, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4350 ± 0.0038 | 0.4498 ± 0.0013 | 0.4315 ± 0.0020 | 0.4320 ± 0.0023 | 0.4313 ± 0.0018 | 3 | – | – |
| add | 0.4365 ± 0.0037 | 0.4508 ± 0.0013 | 0.4331 ± 0.0021 | 0.4336 ± 0.0024 | 0.4329 ± 0.0018 | 3 | +0.34% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm1, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3415 ± 0.0007 | 0.3758 ± 0.0005 | 3 | – | – |
| add | 0.3357 ± 0.0022 | 0.3715 ± 0.0016 | 3 | -1.68% (3/3 better) | effective |

### ETTm1, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3309 ± 0.0010 | 0.3668 ± 0.0006 | 3 | – | – |
| add | 0.3303 ± 0.0010 | 0.3662 ± 0.0006 | 3 | -0.16% (3/3 better) | marginal |

### ETTm1, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3356 ± 0.0002 | 0.3720 ± 0.0006 | 0.3299 ± 0.0015 | 0.3303 ± 0.0014 | 0.3296 ± 0.0011 | 3 | – | – |
| add | 0.3329 ± 0.0006 | 0.3695 ± 0.0007 | 0.3279 ± 0.0022 | 0.3282 ± 0.0021 | 0.3271 ± 0.0018 | 3 | -0.82% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm1, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3815 ± 0.0006 | 0.3946 ± 0.0004 | 3 | – | – |
| add | 0.3790 ± 0.0009 | 0.3929 ± 0.0006 | 3 | -0.67% (3/3 better) | marginal |

### ETTm1, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3770 ± 0.0006 | 0.3922 ± 0.0006 | 3 | – | – |
| add | 0.3768 ± 0.0005 | 0.3919 ± 0.0006 | 3 | -0.06% (3/3 better) | marginal |

### ETTm1, H=192, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3753 ± 0.0014 | 0.3909 ± 0.0006 | 0.3706 ± 0.0002 | 0.3712 ± 0.0002 | 0.3708 ± 0.0006 | 3 | – | – |
| add | 0.3728 ± 0.0019 | 0.3892 ± 0.0008 | 0.3691 ± 0.0004 | 0.3694 ± 0.0006 | 0.3689 ± 0.0010 | 3 | -0.67% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm1, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4173 ± 0.0006 | 0.4179 ± 0.0007 | 3 | – | – |
| add | 0.4149 ± 0.0009 | 0.4164 ± 0.0006 | 3 | -0.58% (3/3 better) | marginal |

### ETTm1, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4168 ± 0.0034 | 0.4188 ± 0.0016 | 3 | – | – |
| add | 0.4164 ± 0.0035 | 0.4185 ± 0.0017 | 3 | -0.10% (3/3 better) | marginal |

### ETTm1, H=336, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4109 ± 0.0015 | 0.4136 ± 0.0007 | 0.4062 ± 0.0003 | 0.4064 ± 0.0002 | 0.4058 ± 0.0006 | 3 | – | – |
| add | 0.4085 ± 0.0015 | 0.4120 ± 0.0007 | 0.4047 ± 0.0004 | 0.4047 ± 0.0004 | 0.4040 ± 0.0007 | 3 | -0.58% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm1, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4903 ± 0.0017 | 0.4577 ± 0.0005 | 3 | – | – |
| add | 0.4877 ± 0.0015 | 0.4560 ± 0.0011 | 3 | -0.53% (3/3 better) | marginal |

### ETTm1, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4880 ± 0.0043 | 0.4585 ± 0.0025 | 3 | – | – |
| add | 0.4918 ± 0.0050 | 0.4607 ± 0.0028 | 3 | +0.78% (1/3 better) | unclear |

### ETTm1, H=720, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4772 ± 0.0019 | 0.4506 ± 0.0014 | 0.4731 ± 0.0004 | 0.4731 ± 0.0004 | 0.4726 ± 0.0006 | 3 | – | – |
| add | 0.4755 ± 0.0017 | 0.4491 ± 0.0012 | 0.4720 ± 0.0003 | 0.4718 ± 0.0004 | 0.4713 ± 0.0006 | 3 | -0.36% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm2, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1847 ± 0.0009 | 0.2697 ± 0.0010 | 3 | – | – |
| add | 0.1846 ± 0.0008 | 0.2697 ± 0.0011 | 3 | -0.07% (2/3 better) | unclear |

### ETTm2, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1795 ± 0.0026 | 0.2637 ± 0.0028 | 3 | – | – |
| add | 0.1794 ± 0.0027 | 0.2636 ± 0.0029 | 3 | -0.09% (3/3 better) | marginal |

### ETTm2, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1805 ± 0.0005 | 0.2632 ± 0.0003 | 0.1790 ± 0.0006 | 0.1790 ± 0.0006 | 0.1790 ± 0.0006 | 3 | – | – |
| add | 0.1815 ± 0.0017 | 0.2645 ± 0.0028 | 0.1801 ± 0.0023 | 0.1801 ± 0.0023 | 0.1801 ± 0.0024 | 3 | +0.55% (2/3 better) | unclear |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm2, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2516 ± 0.0011 | 0.3123 ± 0.0011 | 3 | – | – |
| add | 0.2514 ± 0.0012 | 0.3123 ± 0.0012 | 3 | -0.06% (2/3 better) | unclear |

### ETTm2, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2498 ± 0.0018 | 0.3100 ± 0.0007 | 3 | – | – |
| add | 0.2507 ± 0.0020 | 0.3103 ± 0.0010 | 3 | +0.35% (1/3 better) | unclear |

### ETTm2, H=192, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.2460 ± 0.0011 | 0.3063 ± 0.0006 | 0.2450 ± 0.0007 | 0.2449 ± 0.0009 | 0.2449 ± 0.0009 | 3 | – | – |
| add | 0.2460 ± 0.0012 | 0.3063 ± 0.0006 | 0.2447 ± 0.0008 | 0.2447 ± 0.0010 | 0.2447 ± 0.0010 | 3 | +0.01% (1/3 better) | unclear |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm2, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3153 ± 0.0021 | 0.3516 ± 0.0010 | 3 | – | – |
| add | 0.3149 ± 0.0020 | 0.3514 ± 0.0010 | 3 | -0.10% (3/3 better) | marginal |

### ETTm2, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3109 ± 0.0010 | 0.3480 ± 0.0008 | 3 | – | – |
| add | 0.3112 ± 0.0012 | 0.3482 ± 0.0008 | 3 | +0.09% (0/3 better) | worse |

### ETTm2, H=336, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3094 ± 0.0012 | 0.3466 ± 0.0015 | 0.3092 ± 0.0013 | 0.3091 ± 0.0013 | 0.3088 ± 0.0016 | 3 | – | – |
| add | 0.3094 ± 0.0012 | 0.3467 ± 0.0014 | 0.3092 ± 0.0012 | 0.3091 ± 0.0012 | 0.3088 ± 0.0016 | 3 | +0.01% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm2, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4117 ± 0.0024 | 0.4059 ± 0.0021 | 3 | – | – |
| add | 0.4119 ± 0.0028 | 0.4058 ± 0.0018 | 3 | +0.04% (2/3 better) | unclear |

### ETTm2, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4103 ± 0.0022 | 0.4045 ± 0.0016 | 3 | – | – |
| add | 0.4107 ± 0.0025 | 0.4047 ± 0.0017 | 3 | +0.10% (0/3 better) | worse |

### ETTm2, H=720, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4100 ± 0.0015 | 0.4039 ± 0.0010 | 0.4085 ± 0.0009 | 0.4086 ± 0.0010 | 0.4085 ± 0.0011 | 3 | – | – |
| add | 0.4100 ± 0.0016 | 0.4040 ± 0.0010 | 0.4085 ± 0.0010 | 0.4086 ± 0.0011 | 0.4085 ± 0.0011 | 3 | +0.01% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

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

### Electricity, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1520 ± 0.0006 | 0.2440 ± 0.0002 | 0.1435 ± 0.0007 | 0.1430 ± 0.0007 | 0.1428 ± 0.0006 | 3 | – | – |
| add | 0.1358 ± 0.0004 | 0.2319 ± 0.0004 | 0.1329 ± 0.0006 | 0.1323 ± 0.0006 | 0.1322 ± 0.0005 | 3 | -10.68% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

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

### Electricity, H=192, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1672 ± 0.0004 | 0.2586 ± 0.0009 | 0.1590 ± 0.0015 | 0.1586 ± 0.0015 | 0.1584 ± 0.0015 | 3 | – | – |
| add | 0.1567 ± 0.0010 | 0.2511 ± 0.0011 | 0.1545 ± 0.0020 | 0.1542 ± 0.0021 | 0.1540 ± 0.0021 | 3 | -6.32% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

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

### Electricity, H=336, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1831 ± 0.0013 | 0.2746 ± 0.0014 | 0.1769 ± 0.0010 | 0.1765 ± 0.0007 | 0.1761 ± 0.0008 | 3 | – | – |
| add | 0.1697 ± 0.0006 | 0.2659 ± 0.0000 | 0.1659 ± 0.0009 | 0.1656 ± 0.0009 | 0.1653 ± 0.0007 | 3 | -7.28% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

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

### Electricity, H=720, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.2190 ± 0.0100 | 0.3060 ± 0.0074 | 0.2169 ± 0.0045 | 0.2166 ± 0.0044 | 0.2156 ± 0.0049 | 3 | – | – |
| add | 0.1944 ± 0.0023 | 0.2904 ± 0.0032 | 0.1906 ± 0.0027 | 0.1911 ± 0.0030 | 0.1910 ± 0.0031 | 3 | -11.07% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Exchange, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.0874 ± 0.0006 | 0.2077 ± 0.0011 | 3 | – | – |
| add | 0.0875 ± 0.0005 | 0.2078 ± 0.0010 | 3 | +0.13% (0/3 better) | worse |

### Exchange, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.0865 ± 0.0003 | 0.2071 ± 0.0003 | 3 | – | – |
| add | 0.0866 ± 0.0002 | 0.2072 ± 0.0002 | 3 | +0.06% (1/3 better) | unclear |

### Exchange, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.0860 ± 0.0010 | 0.2055 ± 0.0012 | 0.0857 ± 0.0012 | 0.0858 ± 0.0011 | 0.0859 ± 0.0011 | 3 | – | – |
| add | 0.0863 ± 0.0010 | 0.2059 ± 0.0011 | 0.0859 ± 0.0011 | 0.0860 ± 0.0011 | 0.0861 ± 0.0011 | 3 | +0.24% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Exchange, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1797 ± 0.0013 | 0.3030 ± 0.0011 | 3 | – | – |
| add | 0.1804 ± 0.0013 | 0.3035 ± 0.0010 | 3 | +0.36% (0/3 better) | worse |

### Exchange, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1814 ± 0.0003 | 0.3033 ± 0.0001 | 3 | – | – |
| add | 0.1812 ± 0.0016 | 0.3031 ± 0.0015 | 3 | -0.14% (1/3 better) | unclear |

### Exchange, H=192, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1807 ± 0.0003 | 0.3025 ± 0.0003 | 0.1800 ± 0.0005 | 0.1801 ± 0.0004 | 0.1802 ± 0.0005 | 3 | – | – |
| add | 0.1816 ± 0.0001 | 0.3033 ± 0.0002 | 0.1809 ± 0.0006 | 0.1810 ± 0.0005 | 0.1811 ± 0.0005 | 3 | +0.51% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Exchange, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3339 ± 0.0033 | 0.4195 ± 0.0022 | 3 | – | – |
| add | 0.3343 ± 0.0014 | 0.4195 ± 0.0008 | 3 | +0.12% (1/3 better) | unclear |

### Exchange, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3304 ± 0.0014 | 0.4165 ± 0.0010 | 3 | – | – |
| add | 0.3324 ± 0.0015 | 0.4177 ± 0.0011 | 3 | +0.60% (0/3 better) | worse |

### Exchange, H=336, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3317 ± 0.0008 | 0.4179 ± 0.0006 | 0.3312 ± 0.0001 | 0.3312 ± 0.0001 | 0.3307 ± 0.0002 | 3 | – | – |
| add | 0.3341 ± 0.0012 | 0.4192 ± 0.0009 | 0.3336 ± 0.0004 | 0.3336 ± 0.0005 | 0.3331 ± 0.0002 | 3 | +0.71% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Exchange, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.8548 ± 0.0178 | 0.7002 ± 0.0107 | 3 | – | – |
| add | 0.8568 ± 0.0202 | 0.7015 ± 0.0117 | 3 | +0.23% (1/3 better) | unclear |

### Exchange, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.8580 ± 0.0013 | 0.6981 ± 0.0008 | 3 | – | – |
| add | 0.8622 ± 0.0013 | 0.6997 ± 0.0006 | 3 | +0.49% (0/3 better) | worse |

### Exchange, H=720, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.8518 ± 0.0016 | 0.6961 ± 0.0008 | 0.8508 ± 0.0021 | 0.8511 ± 0.0023 | 0.8508 ± 0.0023 | 3 | – | – |
| add | 0.8552 ± 0.0020 | 0.6976 ± 0.0010 | 0.8543 ± 0.0023 | 0.8545 ± 0.0026 | 0.8543 ± 0.0026 | 3 | +0.41% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

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

### Traffic, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3979 ± 0.0023 | 0.2678 ± 0.0010 | 0.3913 ± 0.0016 | 0.3904 ± 0.0015 | 0.3895 ± 0.0016 | 3 | – | – |
| add | 0.4071 ± 0.0054 | 0.2647 ± 0.0014 | 0.3966 ± 0.0036 | 0.3975 ± 0.0039 | 0.3958 ± 0.0039 | 3 | +2.31% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

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

### Traffic, H=192, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4178 ± 0.0008 | 0.2757 ± 0.0005 | 0.4118 ± 0.0006 | 0.4108 ± 0.0005 | 0.4099 ± 0.0005 | 3 | – | – |
| add | 0.4378 ± 0.0033 | 0.2768 ± 0.0002 | 0.4232 ± 0.0033 | 0.4241 ± 0.0032 | 0.4230 ± 0.0032 | 3 | +4.78% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

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

### Traffic, H=336, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4316 ± 0.0028 | 0.2821 ± 0.0007 | 0.4246 ± 0.0019 | 0.4236 ± 0.0023 | 0.4227 ± 0.0020 | 3 | – | – |
| add | 0.4592 ± 0.0072 | 0.2864 ± 0.0018 | 0.4428 ± 0.0027 | 0.4431 ± 0.0021 | 0.4412 ± 0.0024 | 3 | +6.38% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

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

### Traffic, H=720, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4645 ± 0.0003 | 0.3019 ± 0.0011 | 0.4594 ± 0.0005 | 0.4587 ± 0.0006 | 0.4576 ± 0.0006 | 3 | – | – |
| add | 0.5071 ± 0.0015 | 0.3051 ± 0.0008 | 0.4902 ± 0.0020 | 0.4903 ± 0.0021 | 0.4892 ± 0.0018 | 3 | +9.16% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Weather, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1741 ± 0.0007 | 0.2137 ± 0.0010 | 3 | – | – |
| add | 0.1651 ± 0.0009 | 0.2080 ± 0.0005 | 3 | -5.16% (3/3 better) | effective |

### Weather, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1674 ± 0.0023 | 0.2104 ± 0.0016 | 3 | – | – |
| add | 0.1643 ± 0.0010 | 0.2087 ± 0.0010 | 3 | -1.84% (3/3 better) | effective |

### Weather, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1771 ± 0.0019 | 0.2172 ± 0.0017 | 0.1782 ± 0.0022 | 0.1776 ± 0.0021 | 0.1774 ± 0.0021 | 3 | – | – |
| add | 0.1689 ± 0.0008 | 0.2114 ± 0.0004 | 0.1686 ± 0.0005 | 0.1686 ± 0.0005 | 0.1685 ± 0.0004 | 3 | -4.62% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Weather, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2249 ± 0.0005 | 0.2579 ± 0.0010 | 3 | – | – |
| add | 0.2132 ± 0.0009 | 0.2523 ± 0.0009 | 3 | -5.19% (3/3 better) | effective |

### Weather, H=192, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2153 ± 0.0005 | 0.2540 ± 0.0009 | 3 | – | – |
| add | 0.2129 ± 0.0011 | 0.2531 ± 0.0011 | 3 | -1.12% (3/3 better) | effective |

### Weather, H=192, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.2254 ± 0.0005 | 0.2577 ± 0.0006 | 0.2254 ± 0.0013 | 0.2245 ± 0.0013 | 0.2244 ± 0.0012 | 3 | – | – |
| add | 0.2161 ± 0.0004 | 0.2529 ± 0.0005 | 0.2153 ± 0.0002 | 0.2150 ± 0.0001 | 0.2148 ± 0.0000 | 3 | -4.11% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Weather, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2819 ± 0.0009 | 0.2995 ± 0.0012 | 3 | – | – |
| add | 0.2720 ± 0.0011 | 0.2954 ± 0.0007 | 3 | -3.51% (3/3 better) | effective |

### Weather, H=336, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2738 ± 0.0012 | 0.2966 ± 0.0008 | 3 | – | – |
| add | 0.2711 ± 0.0009 | 0.2951 ± 0.0004 | 3 | -0.97% (3/3 better) | marginal |

### Weather, H=336, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.2809 ± 0.0012 | 0.2979 ± 0.0010 | 0.2810 ± 0.0007 | 0.2804 ± 0.0008 | 0.2800 ± 0.0006 | 3 | – | – |
| add | 0.2735 ± 0.0003 | 0.2948 ± 0.0004 | 0.2723 ± 0.0001 | 0.2722 ± 0.0001 | 0.2720 ± 0.0001 | 3 | -2.65% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Weather, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3586 ± 0.0021 | 0.3501 ± 0.0022 | 3 | – | – |
| add | 0.3502 ± 0.0004 | 0.3464 ± 0.0002 | 3 | -2.35% (3/3 better) | effective |

### Weather, H=720, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3533 ± 0.0011 | 0.3492 ± 0.0010 | 3 | – | – |
| add | 0.3505 ± 0.0005 | 0.3480 ± 0.0004 | 3 | -0.80% (3/3 better) | marginal |

### Weather, H=720, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3587 ± 0.0004 | 0.3497 ± 0.0006 | 0.3594 ± 0.0004 | 0.3588 ± 0.0004 | 0.3584 ± 0.0004 | 3 | – | – |
| add | 0.3511 ± 0.0003 | 0.3465 ± 0.0004 | 0.3504 ± 0.0005 | 0.3502 ± 0.0006 | 0.3498 ± 0.0006 | 3 | -2.11% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Does the fixed scan order act as an identity? (S-Mamba, identity `add`)

| data | H | identity gain, fixed order | identity gain, shuffled order | shuffling cost without identity |
|---|---|---|---|---|
| ETTh1 | 96 | +0.00% (2/3) | -0.04% (3/3) | -0.42% (3/3) |
| ETTh1 | 192 | +0.01% (0/3) | -0.01% (3/3) | -0.77% (3/3) |
| ETTh1 | 336 | +0.05% (0/3) | -0.06% (1/3) | -2.45% (3/3) |
| ETTh1 | 720 | -0.11% (3/3) | -0.04% (2/3) | -3.79% (3/3) |
| ETTh2 | 96 | -0.13% (3/3) | -0.13% (3/3) | -1.54% (2/3) |
| ETTh2 | 192 | -0.08% (3/3) | -0.13% (3/3) | -1.09% (2/3) |
| ETTh2 | 336 | +0.04% (1/3) | +0.01% (1/3) | -0.43% (2/3) |
| ETTh2 | 720 | +0.10% (1/3) | +0.34% (0/3) | +0.74% (1/3) |
| ETTm1 | 96 | -0.16% (3/3) | -0.82% (3/3) | +1.44% (0/3) |
| ETTm1 | 192 | -0.06% (3/3) | -0.67% (3/3) | -0.46% (3/3) |
| ETTm1 | 336 | -0.10% (3/3) | -0.58% (3/3) | -1.42% (3/3) |
| ETTm1 | 720 | +0.78% (1/3) | -0.36% (3/3) | -2.21% (3/3) |
| ETTm2 | 96 | -0.09% (3/3) | +0.55% (2/3) | +0.56% (1/3) |
| ETTm2 | 192 | +0.35% (1/3) | +0.01% (1/3) | -1.52% (3/3) |
| ETTm2 | 336 | +0.09% (0/3) | +0.01% (0/3) | -0.49% (2/3) |
| ETTm2 | 720 | +0.10% (0/3) | +0.01% (0/3) | -0.08% (2/3) |
| Electricity | 96 | -1.90% (3/3) | -10.68% (3/3) | +9.26% (0/3) |
| Electricity | 192 | -0.67% (2/3) | -6.32% (3/3) | +4.14% (0/3) |
| Electricity | 336 | -2.55% (3/3) | -7.28% (3/3) | +3.22% (0/3) |
| Electricity | 720 | -2.81% (3/3) | -11.07% (3/3) | +8.29% (0/3) |
| Exchange | 96 | +0.06% (1/3) | +0.24% (0/3) | -0.58% (2/3) |
| Exchange | 192 | -0.14% (1/3) | +0.51% (0/3) | -0.41% (3/3) |
| Exchange | 336 | +0.60% (0/3) | +0.71% (0/3) | +0.40% (0/3) |
| Exchange | 720 | +0.49% (0/3) | +0.41% (0/3) | -0.72% (3/3) |
| Traffic | 96 | +2.66% (0/3) | +2.31% (0/3) | +2.11% (1/3) |
| Traffic | 192 | +3.06% (0/3) | +4.78% (0/3) | +3.57% (0/3) |
| Traffic | 336 | +5.60% (0/3) | +6.38% (0/3) | +2.21% (0/3) |
| Traffic | 720 | +6.90% (0/3) | +9.16% (0/3) | -0.34% (3/3) |
| Weather | 96 | -1.84% (3/3) | -4.62% (3/3) | +5.78% (0/3) |
| Weather | 192 | -1.12% (3/3) | -4.11% (3/3) | +4.69% (0/3) |
| Weather | 336 | -0.97% (3/3) | -2.65% (3/3) | +2.62% (0/3) |
| Weather | 720 | -0.80% (3/3) | -2.11% (3/3) | +1.52% (0/3) |

