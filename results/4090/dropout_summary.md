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

### ETTh1, H=336, itransformer, d_model=256, d_ff=256

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4831 ± 0.0019 | 0.4584 ± 0.0014 | 3 | – | – |
| add | 0.4844 ± 0.0026 | 0.4590 ± 0.0022 | 3 | +0.28% (1/3 better) | unclear |

### ETTh1, H=336, itransformer, d_model=512, d_ff=512

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4863 ± 0.0021 | 0.4581 ± 0.0010 | 3 | – | – |
| add | 0.4862 ± 0.0023 | 0.4579 ± 0.0012 | 3 | -0.02% (2/3 better) | unclear |
| add-lr10x | 0.4850 ± 0.0029 | 0.4565 ± 0.0019 | 3 | -0.27% (3/3 better) | marginal |

### ETTh1, H=336, smamba, lr=5e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4902 ± 0.0015 | 0.4659 ± 0.0010 | 3 | – | – |
| add | 0.4903 ± 0.0015 | 0.4659 ± 0.0011 | 3 | +0.03% (0/3 better) | worse |
| add-lr10x | 0.4898 ± 0.0012 | 0.4645 ± 0.0012 | 3 | -0.09% (2/3 better) | unclear |

### ETTh1, H=336, smamba, lr=7e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4960 ± 0.0007 | 0.4707 ± 0.0008 | 3 | – | – |
| add | 0.4963 ± 0.0008 | 0.4707 ± 0.0009 | 3 | +0.05% (0/3 better) | worse |

### ETTh1, H=336, smamba, scan order: shuffle, lr=5e-05

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4853 ± 0.0008 | 0.4603 ± 0.0005 | 0.4805 ± 0.0005 | 0.4821 ± 0.0006 | 0.4821 ± 0.0008 | 3 | – | – |
| add | 0.4851 ± 0.0008 | 0.4601 ± 0.0006 | 0.4803 ± 0.0005 | 0.4819 ± 0.0006 | 0.4818 ± 0.0008 | 3 | -0.03% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh1, H=720, itransformer, d_model=256, d_ff=256

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4958 ± 0.0032 | 0.4871 ± 0.0020 | 3 | – | – |
| add | 0.4927 ± 0.0037 | 0.4849 ± 0.0031 | 3 | -0.63% (2/3 better) | unclear |

### ETTh1, H=720, itransformer, d_model=512, d_ff=512

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.5109 ± 0.0079 | 0.4942 ± 0.0036 | 3 | – | – |
| add | 0.5098 ± 0.0092 | 0.4933 ± 0.0046 | 3 | -0.22% (3/3 better) | marginal |
| add-lr10x | 0.5100 ± 0.0037 | 0.4917 ± 0.0021 | 3 | -0.17% (1/3 better) | unclear |

### ETTh1, H=720, smamba, lr=5e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.5102 ± 0.0030 | 0.4986 ± 0.0016 | 3 | – | – |
| add | 0.5099 ± 0.0030 | 0.4983 ± 0.0016 | 3 | -0.06% (3/3 better) | marginal |
| add-lr10x | 0.5062 ± 0.0020 | 0.4951 ± 0.0010 | 3 | -0.78% (3/3 better) | marginal |

### ETTh1, H=720, smamba, lr=7e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.5161 ± 0.0046 | 0.5019 ± 0.0021 | 3 | – | – |
| add | 0.5155 ± 0.0048 | 0.5012 ± 0.0021 | 3 | -0.11% (3/3 better) | marginal |

### ETTh1, H=720, smamba, scan order: shuffle, lr=5e-05

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.5005 ± 0.0034 | 0.4917 ± 0.0023 | 0.4917 ± 0.0033 | 0.4956 ± 0.0033 | 0.4958 ± 0.0041 | 3 | – | – |
| add | 0.5001 ± 0.0033 | 0.4912 ± 0.0022 | 0.4913 ± 0.0032 | 0.4952 ± 0.0033 | 0.4953 ± 0.0040 | 3 | -0.08% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh2, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2997 ± 0.0004 | 0.3498 ± 0.0002 | 3 | – | – |
| add | 0.2994 ± 0.0001 | 0.3497 ± 0.0003 | 3 | -0.11% (2/3 better) | unclear |

### ETTh2, H=96, smamba, lr=4e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2958 ± 0.0004 | 0.3477 ± 0.0003 | 3 | – | – |
| add | 0.2955 ± 0.0004 | 0.3475 ± 0.0003 | 3 | -0.12% (3/3 better) | marginal |
| add-lr10x | 0.2954 ± 0.0000 | 0.3479 ± 0.0003 | 3 | -0.13% (3/3 better) | marginal |

### ETTh2, H=96, smamba, lr=7e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3004 ± 0.0061 | 0.3515 ± 0.0042 | 3 | – | – |
| add | 0.3000 ± 0.0063 | 0.3514 ± 0.0043 | 3 | -0.13% (3/3 better) | marginal |

### ETTh2, H=96, smamba, scan order: shuffle, lr=4e-05

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.2962 ± 0.0004 | 0.3486 ± 0.0002 | 0.2958 ± 0.0005 | 0.2959 ± 0.0004 | 0.2959 ± 0.0004 | 3 | – | – |
| add | 0.2959 ± 0.0004 | 0.3484 ± 0.0002 | 0.2955 ± 0.0005 | 0.2956 ± 0.0004 | 0.2956 ± 0.0004 | 3 | -0.10% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh2, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3793 ± 0.0016 | 0.3983 ± 0.0009 | 3 | – | – |
| add | 0.3788 ± 0.0017 | 0.3982 ± 0.0009 | 3 | -0.11% (3/3 better) | marginal |

### ETTh2, H=192, smamba, lr=4e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3785 ± 0.0010 | 0.3990 ± 0.0004 | 3 | – | – |
| add | 0.3782 ± 0.0011 | 0.3990 ± 0.0003 | 3 | -0.08% (3/3 better) | marginal |
| add-lr10x | 0.3816 ± 0.0007 | 0.4005 ± 0.0009 | 3 | +0.83% (0/3 better) | worse |

### ETTh2, H=192, smamba, lr=7e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3794 ± 0.0047 | 0.3995 ± 0.0013 | 3 | – | – |
| add | 0.3791 ± 0.0049 | 0.3996 ± 0.0013 | 3 | -0.08% (3/3 better) | marginal |

### ETTh2, H=192, smamba, scan order: shuffle, lr=4e-05

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3764 ± 0.0008 | 0.3981 ± 0.0003 | 0.3752 ± 0.0005 | 0.3754 ± 0.0007 | 0.3753 ± 0.0006 | 3 | – | – |
| add | 0.3761 ± 0.0008 | 0.3980 ± 0.0002 | 0.3749 ± 0.0006 | 0.3751 ± 0.0007 | 0.3750 ± 0.0006 | 3 | -0.08% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTh2, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4225 ± 0.0021 | 0.4324 ± 0.0012 | 3 | – | – |
| add | 0.4223 ± 0.0020 | 0.4326 ± 0.0013 | 3 | -0.04% (3/3 better) | marginal |

### ETTh2, H=336, smamba, lr=3e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4248 ± 0.0014 | 0.4349 ± 0.0005 | 3 | – | – |
| add | 0.4249 ± 0.0015 | 0.4351 ± 0.0005 | 3 | +0.02% (0/3 better) | worse |
| add-lr10x | 0.4262 ± 0.0017 | 0.4369 ± 0.0004 | 3 | +0.32% (0/3 better) | worse |

### ETTh2, H=336, smamba, lr=7e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4264 ± 0.0039 | 0.4358 ± 0.0032 | 3 | – | – |
| add | 0.4266 ± 0.0037 | 0.4361 ± 0.0029 | 3 | +0.04% (1/3 better) | unclear |

### ETTh2, H=336, smamba, scan order: shuffle, lr=3e-05

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4245 ± 0.0007 | 0.4347 ± 0.0004 | 0.4236 ± 0.0007 | 0.4237 ± 0.0007 | 0.4236 ± 0.0007 | 3 | – | – |
| add | 0.4246 ± 0.0007 | 0.4349 ± 0.0004 | 0.4237 ± 0.0007 | 0.4237 ± 0.0007 | 0.4237 ± 0.0007 | 3 | +0.01% (0/3 better) | worse |

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

### ETTm1, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3815 ± 0.0006 | 0.3946 ± 0.0004 | 3 | – | – |
| add | 0.3790 ± 0.0009 | 0.3929 ± 0.0006 | 3 | -0.67% (3/3 better) | marginal |

### ETTm1, H=192, smamba, d_model=128, d_ff=128

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3777 ± 0.0002 | 0.3931 ± 0.0007 | 3 | – | – |
| add | 0.3768 ± 0.0002 | 0.3924 ± 0.0007 | 3 | -0.24% (3/3 better) | marginal |
| add-lr10x | 0.3752 ± 0.0008 | 0.3921 ± 0.0006 | 3 | -0.65% (3/3 better) | marginal |

### ETTm1, H=192, smamba, d_model=256, d_ff=256

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3770 ± 0.0006 | 0.3922 ± 0.0006 | 3 | – | – |
| add | 0.3768 ± 0.0005 | 0.3919 ± 0.0006 | 3 | -0.06% (3/3 better) | marginal |

### ETTm1, H=192, smamba, scan order: shuffle, d_model=128, d_ff=128

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3799 ± 0.0013 | 0.3927 ± 0.0009 | 0.3750 ± 0.0002 | 0.3753 ± 0.0003 | 0.3752 ± 0.0002 | 3 | – | – |
| add | 0.3784 ± 0.0011 | 0.3914 ± 0.0009 | 0.3740 ± 0.0002 | 0.3741 ± 0.0001 | 0.3739 ± 0.0002 | 3 | -0.39% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm1, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4173 ± 0.0006 | 0.4179 ± 0.0007 | 3 | – | – |
| add | 0.4149 ± 0.0009 | 0.4164 ± 0.0006 | 3 | -0.58% (3/3 better) | marginal |

### ETTm1, H=336, smamba, d_model=128, d_ff=128

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4094 ± 0.0002 | 0.4138 ± 0.0002 | 3 | – | – |
| add | 0.4085 ± 0.0003 | 0.4132 ± 0.0003 | 3 | -0.22% (3/3 better) | marginal |
| add-lr10x | 0.4075 ± 0.0004 | 0.4137 ± 0.0004 | 3 | -0.48% (3/3 better) | marginal |

### ETTm1, H=336, smamba, d_model=256, d_ff=256

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4168 ± 0.0034 | 0.4188 ± 0.0016 | 3 | – | – |
| add | 0.4164 ± 0.0035 | 0.4185 ± 0.0017 | 3 | -0.10% (3/3 better) | marginal |

### ETTm1, H=336, smamba, scan order: shuffle, d_model=128, d_ff=128

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4136 ± 0.0006 | 0.4128 ± 0.0003 | 0.4103 ± 0.0006 | 0.4103 ± 0.0005 | 0.4103 ± 0.0005 | 3 | – | – |
| add | 0.4123 ± 0.0004 | 0.4115 ± 0.0001 | 0.4095 ± 0.0006 | 0.4093 ± 0.0005 | 0.4094 ± 0.0006 | 3 | -0.31% (3/3 better) | marginal |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm1, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4903 ± 0.0017 | 0.4577 ± 0.0005 | 3 | – | – |
| add | 0.4877 ± 0.0015 | 0.4560 ± 0.0011 | 3 | -0.53% (3/3 better) | marginal |

### ETTm1, H=720, smamba, d_model=128, d_ff=128

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4759 ± 0.0001 | 0.4519 ± 0.0003 | 3 | – | – |
| add | 0.4752 ± 0.0001 | 0.4513 ± 0.0003 | 3 | -0.15% (3/3 better) | marginal |
| add-lr10x | 0.4769 ± 0.0003 | 0.4528 ± 0.0003 | 3 | +0.22% (0/3 better) | worse |

### ETTm1, H=720, smamba, d_model=256, d_ff=256

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4880 ± 0.0043 | 0.4585 ± 0.0025 | 3 | – | – |
| add | 0.4918 ± 0.0050 | 0.4607 ± 0.0028 | 3 | +0.78% (1/3 better) | unclear |

### ETTm1, H=720, smamba, scan order: shuffle, d_model=128, d_ff=128

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4780 ± 0.0011 | 0.4491 ± 0.0010 | 0.4748 ± 0.0009 | 0.4750 ± 0.0008 | 0.4748 ± 0.0009 | 3 | – | – |
| add | 0.4774 ± 0.0014 | 0.4482 ± 0.0010 | 0.4743 ± 0.0011 | 0.4743 ± 0.0010 | 0.4741 ± 0.0012 | 3 | -0.13% (3/3 better) | marginal |

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

### ETTm2, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2516 ± 0.0011 | 0.3123 ± 0.0011 | 3 | – | – |
| add | 0.2514 ± 0.0012 | 0.3123 ± 0.0012 | 3 | -0.06% (2/3 better) | unclear |

### ETTm2, H=192, smamba, d_model=128, d_ff=128

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2501 ± 0.0011 | 0.3103 ± 0.0012 | 3 | – | – |
| add | 0.2504 ± 0.0011 | 0.3105 ± 0.0012 | 3 | +0.09% (0/3 better) | worse |
| add-lr10x | 0.2504 ± 0.0011 | 0.3105 ± 0.0012 | 3 | +0.12% (0/3 better) | worse |

### ETTm2, H=192, smamba, d_model=256, d_ff=256

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2498 ± 0.0018 | 0.3100 ± 0.0007 | 3 | – | – |
| add | 0.2507 ± 0.0020 | 0.3103 ± 0.0010 | 3 | +0.35% (1/3 better) | unclear |

### ETTm2, H=192, smamba, scan order: shuffle, d_model=128, d_ff=128

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.2488 ± 0.0008 | 0.3091 ± 0.0008 | 0.2478 ± 0.0005 | 0.2478 ± 0.0006 | 0.2477 ± 0.0007 | 3 | – | – |
| add | 0.2491 ± 0.0011 | 0.3093 ± 0.0010 | 0.2481 ± 0.0009 | 0.2480 ± 0.0010 | 0.2480 ± 0.0011 | 3 | +0.15% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm2, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3153 ± 0.0021 | 0.3516 ± 0.0010 | 3 | – | – |
| add | 0.3149 ± 0.0020 | 0.3514 ± 0.0010 | 3 | -0.10% (3/3 better) | marginal |

### ETTm2, H=336, smamba, d_model=128, d_ff=128, lr=3e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3122 ± 0.0006 | 0.3494 ± 0.0004 | 3 | – | – |
| add | 0.3124 ± 0.0006 | 0.3495 ± 0.0004 | 3 | +0.06% (0/3 better) | worse |
| add-lr10x | 0.3129 ± 0.0004 | 0.3500 ± 0.0002 | 3 | +0.21% (0/3 better) | worse |

### ETTm2, H=336, smamba, d_model=256, d_ff=256, lr=5e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3109 ± 0.0010 | 0.3480 ± 0.0008 | 3 | – | – |
| add | 0.3112 ± 0.0012 | 0.3482 ± 0.0008 | 3 | +0.09% (0/3 better) | worse |

### ETTm2, H=336, smamba, scan order: shuffle, d_model=128, d_ff=128, lr=3e-05

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3114 ± 0.0008 | 0.3488 ± 0.0004 | 0.3112 ± 0.0008 | 0.3112 ± 0.0008 | 0.3111 ± 0.0009 | 3 | – | – |
| add | 0.3115 ± 0.0008 | 0.3488 ± 0.0004 | 0.3112 ± 0.0008 | 0.3112 ± 0.0008 | 0.3111 ± 0.0008 | 3 | +0.02% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### ETTm2, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4117 ± 0.0024 | 0.4059 ± 0.0021 | 3 | – | – |
| add | 0.4119 ± 0.0028 | 0.4058 ± 0.0018 | 3 | +0.04% (2/3 better) | unclear |

### ETTm2, H=720, smamba, d_model=128, d_ff=128

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4127 ± 0.0004 | 0.4049 ± 0.0002 | 3 | – | – |
| add | 0.4127 ± 0.0004 | 0.4050 ± 0.0002 | 3 | +0.01% (1/3 better) | unclear |
| add-lr10x | 0.4130 ± 0.0004 | 0.4054 ± 0.0002 | 3 | +0.08% (0/3 better) | worse |

### ETTm2, H=720, smamba, d_model=256, d_ff=256

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4103 ± 0.0022 | 0.4045 ± 0.0016 | 3 | – | – |
| add | 0.4107 ± 0.0025 | 0.4047 ± 0.0017 | 3 | +0.10% (0/3 better) | worse |

### ETTm2, H=720, smamba, scan order: shuffle, d_model=128, d_ff=128

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.4116 ± 0.0010 | 0.4044 ± 0.0003 | 0.4110 ± 0.0020 | 0.4111 ± 0.0017 | 0.4111 ± 0.0017 | 3 | – | – |
| add | 0.4117 ± 0.0010 | 0.4044 ± 0.0003 | 0.4110 ± 0.0020 | 0.4112 ± 0.0017 | 0.4111 ± 0.0017 | 3 | +0.01% (1/3 better) | unclear |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Electricity, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1482 ± 0.0003 | 0.2398 ± 0.0001 | 3 | – | – |
| add | 0.1368 ± 0.0004 | 0.2326 ± 0.0003 | 3 | -7.74% (3/3 better) | effective |
| add-drop0.1 | 0.1359 ± 0.0005 | 0.2320 ± 0.0007 | 3 | -8.31% (3/3 better) | effective |
| add-drop0.3 | 0.1368 ± 0.0003 | 0.2327 ± 0.0004 | 3 | -7.69% (3/3 better) | effective |

### Electricity, H=96, smamba

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1391 ± 0.0006 | 0.2360 ± 0.0008 | 3 | – | – |
| add | 0.1365 ± 0.0013 | 0.2342 ± 0.0014 | 3 | -1.90% (3/3 better) | effective |
| add-drop0.1 | 0.1360 ± 0.0010 | 0.2342 ± 0.0013 | 3 | -2.21% (3/3 better) | effective |
| add-drop0.3 | 0.1360 ± 0.0004 | 0.2342 ± 0.0005 | 3 | -2.28% (3/3 better) | effective |

### Electricity, H=96, smamba, scan order: shuffle

| variant | mse | mae | mse_orders2 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| add-drop0.1 | 0.1359 ± 0.0006 | 0.2322 ± 0.0007 | 0.1335 ± 0.0011 | 0.1328 ± 0.0010 | 3 | – | – |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Electricity, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1649 ± 0.0004 | 0.2562 ± 0.0003 | 3 | – | – |
| add | 0.1565 ± 0.0019 | 0.2512 ± 0.0019 | 3 | -5.11% (3/3 better) | effective |
| add-drop0.1 | 0.1569 ± 0.0016 | 0.2516 ± 0.0012 | 3 | -4.86% (3/3 better) | effective |
| add-drop0.3 | 0.1587 ± 0.0026 | 0.2531 ± 0.0026 | 3 | -3.77% (3/3 better) | effective |

### Electricity, H=192, smamba, d_state=16, lr=0.001

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1606 ± 0.0023 | 0.2579 ± 0.0026 | 3 | – | – |
| add | 0.1595 ± 0.0005 | 0.2568 ± 0.0005 | 3 | -0.67% (2/3 better) | unclear |

### Electricity, H=192, smamba, d_state=32, lr=0.0005

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1604 ± 0.0027 | 0.2572 ± 0.0032 | 3 | – | – |
| add | 0.1588 ± 0.0007 | 0.2563 ± 0.0008 | 3 | -0.98% (2/3 better) | unclear |
| add-drop0.1 | 0.1597 ± 0.0018 | 0.2573 ± 0.0017 | 3 | -0.46% (2/3 better) | unclear |
| add-drop0.3 | 0.1593 ± 0.0020 | 0.2559 ± 0.0023 | 3 | -0.69% (2/3 better) | unclear |

### Electricity, H=192, smamba, scan order: shuffle, d_state=32, lr=0.0005

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1681 ± 0.0012 | 0.2587 ± 0.0009 | 0.1589 ± 0.0003 | 0.1585 ± 0.0003 | 0.1584 ± 0.0003 | 3 | – | – |
| add | 0.1558 ± 0.0008 | 0.2496 ± 0.0009 | 0.1509 ± 0.0010 | 0.1504 ± 0.0009 | 0.1502 ± 0.0008 | 3 | -7.30% (3/3 better) | effective |
| add-drop0.1 | 0.1564 ± 0.0005 | 0.2499 ± 0.0006 | 0.1513 ± 0.0001 | – | 0.1507 ± 0.0001 | 3 | -6.93% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Electricity, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1792 ± 0.0016 | 0.2718 ± 0.0008 | 3 | – | – |
| add | 0.1717 ± 0.0019 | 0.2682 ± 0.0024 | 3 | -4.17% (3/3 better) | effective |
| add-drop0.1 | 0.1706 ± 0.0017 | 0.2666 ± 0.0016 | 3 | -4.77% (3/3 better) | effective |
| add-drop0.3 | 0.1720 ± 0.0005 | 0.2676 ± 0.0008 | 3 | -4.00% (3/3 better) | effective |

### Electricity, H=336, smamba, d_state=16, lr=0.001

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1774 ± 0.0016 | 0.2745 ± 0.0021 | 3 | – | – |
| add | 0.1729 ± 0.0017 | 0.2712 ± 0.0018 | 3 | -2.55% (3/3 better) | effective |

### Electricity, H=336, smamba, d_state=32, lr=0.0005

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1806 ± 0.0030 | 0.2776 ± 0.0027 | 3 | – | – |
| add | 0.1740 ± 0.0012 | 0.2714 ± 0.0005 | 3 | -3.60% (3/3 better) | effective |
| add-drop0.1 | 0.1756 ± 0.0008 | 0.2724 ± 0.0008 | 3 | -2.75% (3/3 better) | effective |
| add-drop0.3 | 0.1813 ± 0.0027 | 0.2770 ± 0.0028 | 3 | +0.42% (2/3 better) | unclear |

### Electricity, H=336, smamba, scan order: shuffle, d_state=32, lr=0.0005

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1880 ± 0.0039 | 0.2796 ± 0.0042 | 0.1774 ± 0.0033 | 0.1770 ± 0.0034 | 0.1764 ± 0.0036 | 3 | – | – |
| add | 0.1746 ± 0.0021 | 0.2695 ± 0.0018 | 0.1687 ± 0.0031 | 0.1685 ± 0.0030 | 0.1682 ± 0.0031 | 3 | -7.11% (3/3 better) | effective |
| add-drop0.1 | 0.1747 ± 0.0007 | 0.2693 ± 0.0003 | 0.1675 ± 0.0013 | – | 0.1669 ± 0.0013 | 3 | -7.10% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Electricity, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2146 ± 0.0096 | 0.3028 ± 0.0072 | 3 | – | – |
| add | 0.1992 ± 0.0025 | 0.2931 ± 0.0037 | 3 | -7.08% (3/3 better) | effective |
| add-drop0.1 | 0.1974 ± 0.0021 | 0.2910 ± 0.0017 | 3 | -7.91% (3/3 better) | effective |
| add-drop0.3 | 0.1980 ± 0.0011 | 0.2918 ± 0.0012 | 3 | -7.63% (3/3 better) | effective |

### Electricity, H=720, smamba, d_state=16, lr=0.001

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2022 ± 0.0027 | 0.2974 ± 0.0016 | 3 | – | – |
| add | 0.1965 ± 0.0032 | 0.2916 ± 0.0006 | 3 | -2.81% (3/3 better) | effective |

### Electricity, H=720, smamba, d_state=32, lr=0.0005

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.2063 ± 0.0048 | 0.3003 ± 0.0046 | 3 | – | – |
| add | 0.1917 ± 0.0013 | 0.2891 ± 0.0009 | 3 | -7.04% (3/3 better) | effective |
| add-drop0.1 | 0.1941 ± 0.0018 | 0.2913 ± 0.0016 | 3 | -5.88% (3/3 better) | effective |
| add-drop0.3 | 0.1977 ± 0.0016 | 0.2944 ± 0.0018 | 3 | -4.15% (3/3 better) | effective |

### Electricity, H=720, smamba, scan order: shuffle, d_state=32, lr=0.0005

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.2334 ± 0.0011 | 0.3170 ± 0.0011 | 0.2223 ± 0.0018 | 0.2217 ± 0.0017 | 0.2213 ± 0.0017 | 3 | – | – |
| add | 0.2063 ± 0.0104 | 0.2980 ± 0.0078 | 0.2025 ± 0.0067 | 0.2035 ± 0.0055 | 0.2021 ± 0.0064 | 3 | -11.59% (3/3 better) | effective |
| add-drop0.1 | 0.2131 ± 0.0106 | 0.3025 ± 0.0081 | 0.2097 ± 0.0021 | – | 0.2083 ± 0.0028 | 3 | -8.71% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Exchange, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.0874 ± 0.0006 | 0.2077 ± 0.0011 | 3 | – | – |
| add | 0.0875 ± 0.0005 | 0.2078 ± 0.0010 | 3 | +0.13% (0/3 better) | worse |

### Exchange, H=96, smamba, d_state=2, batch_size=32

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.0865 ± 0.0003 | 0.2071 ± 0.0003 | 3 | – | – |
| add | 0.0866 ± 0.0002 | 0.2072 ± 0.0002 | 3 | +0.06% (1/3 better) | unclear |

### Exchange, H=96, smamba, d_state=32, batch_size=16

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.0876 ± 0.0004 | 0.2080 ± 0.0005 | 3 | – | – |
| add | 0.0876 ± 0.0004 | 0.2082 ± 0.0006 | 3 | +0.02% (1/3 better) | unclear |
| add-lr10x | 0.0882 ± 0.0005 | 0.2091 ± 0.0009 | 3 | +0.69% (0/3 better) | worse |

### Exchange, H=96, smamba, scan order: shuffle, d_state=32, batch_size=16

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.0862 ± 0.0013 | 0.2057 ± 0.0017 | 0.0856 ± 0.0016 | 0.0857 ± 0.0015 | 0.0858 ± 0.0015 | 3 | – | – |
| add | 0.0859 ± 0.0009 | 0.2054 ± 0.0008 | 0.0853 ± 0.0008 | 0.0854 ± 0.0008 | 0.0855 ± 0.0009 | 3 | -0.33% (1/3 better) | unclear |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Exchange, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1797 ± 0.0013 | 0.3030 ± 0.0011 | 3 | – | – |
| add | 0.1804 ± 0.0013 | 0.3035 ± 0.0010 | 3 | +0.36% (0/3 better) | worse |

### Exchange, H=192, smamba, d_state=2

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1814 ± 0.0003 | 0.3033 ± 0.0001 | 3 | – | – |
| add | 0.1812 ± 0.0016 | 0.3031 ± 0.0015 | 3 | -0.14% (1/3 better) | unclear |

### Exchange, H=192, smamba, d_state=32

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.1818 ± 0.0022 | 0.3036 ± 0.0017 | 3 | – | – |
| add | 0.1827 ± 0.0022 | 0.3043 ± 0.0018 | 3 | +0.48% (0/3 better) | worse |
| add-lr10x | 0.1859 ± 0.0018 | 0.3075 ± 0.0016 | 3 | +2.26% (0/3 better) | worse |

### Exchange, H=192, smamba, scan order: shuffle, d_state=32

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.1819 ± 0.0006 | 0.3038 ± 0.0006 | 0.1811 ± 0.0004 | 0.1812 ± 0.0003 | 0.1811 ± 0.0004 | 3 | – | – |
| add | 0.1828 ± 0.0007 | 0.3045 ± 0.0007 | 0.1820 ± 0.0005 | 0.1821 ± 0.0005 | 0.1820 ± 0.0005 | 3 | +0.48% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Exchange, H=336, itransformer, epochs=1

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3339 ± 0.0014 | 0.4194 ± 0.0010 | 3 | – | – |
| add | 0.3341 ± 0.0014 | 0.4195 ± 0.0010 | 3 | +0.07% (0/3 better) | worse |
| add-lr10x | 0.3361 ± 0.0017 | 0.4206 ± 0.0012 | 3 | +0.66% (0/3 better) | worse |

### Exchange, H=336, itransformer, epochs=10

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3339 ± 0.0033 | 0.4195 ± 0.0022 | 3 | – | – |
| add | 0.3343 ± 0.0014 | 0.4195 ± 0.0008 | 3 | +0.12% (1/3 better) | unclear |

### Exchange, H=336, smamba, d_state=2, lr=0.0001

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3304 ± 0.0014 | 0.4165 ± 0.0010 | 3 | – | – |
| add | 0.3324 ± 0.0015 | 0.4177 ± 0.0011 | 3 | +0.60% (0/3 better) | worse |

### Exchange, H=336, smamba, d_state=32, lr=5e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3306 ± 0.0001 | 0.4166 ± 0.0002 | 3 | – | – |
| add | 0.3314 ± 0.0001 | 0.4170 ± 0.0002 | 3 | +0.25% (0/3 better) | worse |
| add-lr10x | 0.3377 ± 0.0003 | 0.4210 ± 0.0003 | 3 | +2.15% (0/3 better) | worse |

### Exchange, H=336, smamba, scan order: shuffle, d_state=32, lr=5e-05

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3313 ± 0.0001 | 0.4172 ± 0.0000 | 0.3309 ± 0.0000 | 0.3310 ± 0.0001 | 0.3309 ± 0.0001 | 3 | – | – |
| add | 0.3321 ± 0.0001 | 0.4177 ± 0.0001 | 0.3317 ± 0.0001 | 0.3318 ± 0.0001 | 0.3317 ± 0.0001 | 3 | +0.25% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Exchange, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.8548 ± 0.0178 | 0.7002 ± 0.0107 | 3 | – | – |
| add | 0.8568 ± 0.0202 | 0.7015 ± 0.0117 | 3 | +0.23% (1/3 better) | unclear |

### Exchange, H=720, smamba, d_state=2, lr=0.0001

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.8580 ± 0.0013 | 0.6981 ± 0.0008 | 3 | – | – |
| add | 0.8622 ± 0.0013 | 0.6997 ± 0.0006 | 3 | +0.49% (0/3 better) | worse |

### Exchange, H=720, smamba, d_state=32, lr=5e-05

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.8599 ± 0.0007 | 0.7003 ± 0.0003 | 3 | – | – |
| add | 0.8610 ± 0.0008 | 0.7008 ± 0.0004 | 3 | +0.14% (0/3 better) | worse |
| add-lr10x | 0.8685 ± 0.0018 | 0.7044 ± 0.0008 | 3 | +1.00% (0/3 better) | worse |

### Exchange, H=720, smamba, scan order: shuffle, d_state=32, lr=5e-05

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.8592 ± 0.0010 | 0.7001 ± 0.0004 | 0.8587 ± 0.0009 | 0.8589 ± 0.0010 | 0.8588 ± 0.0009 | 3 | – | – |
| add | 0.8604 ± 0.0011 | 0.7006 ± 0.0005 | 0.8599 ± 0.0010 | 0.8600 ± 0.0011 | 0.8600 ± 0.0010 | 3 | +0.14% (0/3 better) | worse |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Traffic, H=96, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3935 ± 0.0007 | 0.2688 ± 0.0007 | 3 | – | – |
| add | 0.3996 ± 0.0014 | 0.2667 ± 0.0003 | 3 | +1.54% (0/3 better) | worse |
| add-drop0.1 | 0.3880 ± 0.0007 | 0.2653 ± 0.0008 | 3 | -1.41% (3/3 better) | effective |
| add-drop0.3 | 0.3842 ± 0.0005 | 0.2648 ± 0.0004 | 3 | -2.37% (3/3 better) | effective |

### Traffic, H=96, smamba, d_state=16, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3897 ± 0.0058 | 0.2644 ± 0.0024 | 3 | – | – |
| add | 0.4000 ± 0.0055 | 0.2621 ± 0.0005 | 3 | +2.66% (0/3 better) | worse |

### Traffic, H=96, smamba, d_state=32, epochs=10

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3787 ± 0.0019 | 0.2594 ± 0.0012 | 3 | – | – |
| add | 0.3842 ± 0.0035 | 0.2549 ± 0.0012 | 3 | +1.44% (1/3 better) | unclear |
| add-drop0.1 | 0.3793 ± 0.0045 | 0.2545 ± 0.0007 | 3 | +0.15% (2/3 better) | unclear |
| add-drop0.3 | 0.3778 ± 0.0017 | 0.2547 ± 0.0007 | 3 | -0.24% (3/3 better) | marginal |

### Traffic, H=96, smamba, scan order: shuffle, d_state=32, epochs=10

| variant | mse | mae | mse_orders2 | mse_orders4 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|---|
| none | 0.3921 ± 0.0016 | 0.2636 ± 0.0006 | 0.3859 ± 0.0013 | 0.3850 ± 0.0012 | 0.3842 ± 0.0011 | 3 | – | – |
| add | 0.4070 ± 0.0020 | 0.2609 ± 0.0011 | 0.3972 ± 0.0040 | 0.3976 ± 0.0042 | 0.3961 ± 0.0035 | 3 | +3.80% (0/3 better) | worse |
| add-drop0.1 | 0.3869 ± 0.0013 | 0.2590 ± 0.0005 | 0.3796 ± 0.0028 | – | 0.3781 ± 0.0025 | 3 | -1.32% (3/3 better) | effective |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Traffic, H=192, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4122 ± 0.0007 | 0.2769 ± 0.0006 | 3 | – | – |
| add | 0.4287 ± 0.0020 | 0.2778 ± 0.0004 | 3 | +4.00% (0/3 better) | worse |
| add-drop0.1 | 0.4137 ± 0.0019 | 0.2751 ± 0.0002 | 3 | +0.37% (1/3 better) | unclear |
| add-drop0.3 | 0.4082 ± 0.0009 | 0.2742 ± 0.0005 | 3 | -0.96% (3/3 better) | marginal |

### Traffic, H=192, smamba, d_state=16, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4035 ± 0.0018 | 0.2732 ± 0.0013 | 3 | – | – |
| add | 0.4158 ± 0.0017 | 0.2718 ± 0.0009 | 3 | +3.06% (0/3 better) | worse |

### Traffic, H=192, smamba, d_state=32, epochs=10

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.3927 | 0.2683 | 1 | – | – |
| add-drop0.1 | 0.4169 ± 0.0090 | 0.2703 ± 0.0016 | 3 | – | – |
| add-drop0.3 | 0.4039 ± 0.0041 | 0.2675 ± 0.0021 | 3 | – | – |

### Traffic, H=192, smamba, scan order: shuffle, d_state=32, epochs=10

| variant | mse | mae | mse_orders2 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| add-drop0.1 | 0.4156 ± 0.0021 | 0.2714 ± 0.0011 | 0.4065 ± 0.0007 | 0.4049 ± 0.0006 | 3 | – | – |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Traffic, H=336, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4237 ± 0.0011 | 0.2827 ± 0.0002 | 3 | – | – |
| add | 0.4447 ± 0.0021 | 0.2840 ± 0.0006 | 3 | +4.95% (0/3 better) | worse |
| add-drop0.1 | 0.4304 ± 0.0010 | 0.2815 ± 0.0005 | 3 | +1.58% (0/3 better) | worse |
| add-drop0.3 | 0.4217 ± 0.0014 | 0.2806 ± 0.0006 | 3 | -0.49% (3/3 better) | marginal |

### Traffic, H=336, smamba, d_state=16, lr=0.001, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4223 ± 0.0017 | 0.2799 ± 0.0009 | 3 | – | – |
| add | 0.4460 ± 0.0040 | 0.2809 ± 0.0018 | 3 | +5.60% (0/3 better) | worse |

### Traffic, H=336, smamba, d_state=32, lr=0.002, epochs=10

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| add-drop0.1 | 0.4312 ± 0.0033 | 0.2806 ± 0.0019 | 3 | – | – |
| add-drop0.3 | 0.4293 ± 0.0027 | 0.2791 ± 0.0033 | 3 | – | – |

### Traffic, H=336, smamba, scan order: shuffle, d_state=32, lr=0.002, epochs=10

| variant | mse | mae | mse_orders2 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| add-drop0.1 | 0.4304 ± 0.0015 | 0.2788 ± 0.0005 | 0.4215 ± 0.0007 | 0.4206 ± 0.0004 | 3 | – | – |

(`*_orders`, `mse_ordersK`: the same trained model tested with the mixing averaged over several / K random scan orders)

### Traffic, H=720, itransformer

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4579 ± 0.0010 | 0.3004 ± 0.0006 | 3 | – | – |
| add | 0.4864 ± 0.0013 | 0.3050 ± 0.0004 | 3 | +6.21% (0/3 better) | worse |
| add-drop0.1 | 0.4703 ± 0.0013 | 0.3015 ± 0.0005 | 3 | +2.70% (0/3 better) | worse |
| add-drop0.3 | 0.4561 ± 0.0019 | 0.2978 ± 0.0010 | 3 | -0.39% (2/3 better) | unclear |

### Traffic, H=720, smamba, d_state=16, lr=0.001, epochs=5

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| none | 0.4661 ± 0.0004 | 0.2994 ± 0.0006 | 3 | – | – |
| add | 0.4983 ± 0.0052 | 0.3020 ± 0.0014 | 3 | +6.90% (0/3 better) | worse |

### Traffic, H=720, smamba, d_state=32, lr=0.0008, epochs=10

| variant | mse | mae | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|
| add-drop0.1 | 0.4892 ± 0.0008 | 0.3006 ± 0.0027 | 3 | – | – |
| add-drop0.3 | 0.4816 ± 0.0052 | 0.2991 ± 0.0019 | 3 | – | – |

### Traffic, H=720, smamba, scan order: shuffle, d_state=32, lr=0.0008, epochs=10

| variant | mse | mae | mse_orders2 | mse_orders8 | seeds | vs none (paired MSE) | verdict |
|---|---|---|---|---|---|---|---|
| add-drop0.1 | 0.4786 ± 0.0035 | 0.2982 ± 0.0009 | 0.4683 ± 0.0052 | 0.4679 ± 0.0053 | 3 | – | – |

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

### Does the fixed scan order act as an identity? (S-Mamba, identity `add`)

| data | H | identity gain, fixed order | identity gain, shuffled order | shuffling cost without identity |
|---|---|---|---|---|
| ETTh1 | 336 | +0.03% (0/3) | -0.03% (3/3) | -1.00% (3/3) |
| ETTh1 | 720 | -0.06% (3/3) | -0.08% (3/3) | -1.89% (3/3) |
| ETTh2 | 96 | -0.12% (3/3) | -0.10% (3/3) | +0.11% (0/3) |
| ETTh2 | 192 | -0.08% (3/3) | -0.08% (3/3) | -0.55% (3/3) |
| ETTh2 | 336 | +0.02% (0/3) | +0.01% (0/3) | -0.08% (2/3) |
| ETTm1 | 192 | -0.24% (3/3) | -0.39% (3/3) | +0.58% (0/3) |
| ETTm1 | 336 | -0.22% (3/3) | -0.31% (3/3) | +1.01% (0/3) |
| ETTm1 | 720 | -0.15% (3/3) | -0.13% (3/3) | +0.44% (0/3) |
| ETTm2 | 192 | +0.09% (0/3) | +0.15% (0/3) | -0.55% (3/3) |
| ETTm2 | 336 | +0.06% (0/3) | +0.02% (0/3) | -0.25% (3/3) |
| ETTm2 | 720 | +0.01% (1/3) | +0.01% (1/3) | -0.26% (3/3) |
| Electricity | 192 | -0.98% (2/3) | -7.30% (3/3) | +4.80% (0/3) |
| Electricity | 336 | -3.60% (3/3) | -7.11% (3/3) | +4.16% (0/3) |
| Electricity | 720 | -7.04% (3/3) | -11.59% (3/3) | +13.21% (0/3) |
| Exchange | 96 | +0.02% (1/3) | -0.33% (1/3) | -1.63% (2/3) |
| Exchange | 192 | +0.48% (0/3) | +0.48% (0/3) | +0.05% (2/3) |
| Exchange | 336 | +0.25% (0/3) | +0.25% (0/3) | +0.21% (0/3) |
| Exchange | 720 | +0.14% (0/3) | +0.14% (0/3) | -0.07% (3/3) |
| Traffic | 96 | +1.44% (1/3) | +3.80% (0/3) | +3.54% (0/3) |

