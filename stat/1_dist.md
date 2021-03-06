# 概率分布

- [概率分布](#概率分布)
  - [简介](#简介)
  - [正态分布](#正态分布)
    - [随机数](#随机数)

2020-08-12, 10:13
***

## 简介

R 中内置了许多生成随机数的函数。对应不同的分布。

|分布|表示|随机数生成函数|
|---|---|---|
|Uniform|$U(a,b)$|`runif`|
|Normal|$N(\mu,\sigma)$|`rnorm`|
|Binormal|$Bin(n,p)$|`rbinorm`|
|Piosson|$pois(\lambda)$|`rpois`|
|Beta|$Beta(\alpha,\beta)$|`rbeta`|

R 中与 xxx 分布有关的函数一般有4个：

- dxxx(x), xxx 分布的分布密度函数（PDF）或概率函数（PMF） $p(x)$。
- pxxx(q), xxx 分布的分布函数（CDF）$F(q)=P(x\le q)$。
- qxxx(p)，xxx 分布的分位数函数 $q(p), p \isin (0,1)$，对连续型分布，$q(p)=F^{-1}(p)$，即 $F(x)=p$ 的解 x。
- rxxx(n)，xxx 的随机数函数，可以生成 n 个 xxx 的随机数。

dxxx(x) 函数加选项 `log=TRUE`，用来计算 $log p(x)$，比使用 `log(dxxx(x))` 更精确。

pxxx(q) 加选项 `lower.tail=FALSE`，计算 $P(X > q)=1-F(q)$。

qxxx(p) 加选项 `lower.tail=TRUE`，表示计算 $P(X > x)=p$ 的解x；加选项 `log.p=TRUE`，表示输入的 p 实际是 $lnp$。

这些函数都可以带有自己的分布参数，有些分布参数有缺省值，比如正态分布的缺省参数值均值为0，标准差为1.

常见的分布密度函数有：

- 离散分布
  - 二项分布，dbinom
  - 泊松分布，dpois
  - 几何分布，dgeom
  - 负二项分布，dnbinom
  - 多项分布，dmultinom
  - 超几何分布，dhyper
- 连续分布
  - 均匀分布，dunif
  - 正态分布，dnorm
  - 卡方分布，dchisq
  - t 分布，dt
  - F 分布，df
  - 指数分布，dexp
  - 威布尔分布，dweibull
  - 伽马分布，dgamma
  - 贝塔分布，dbeta
  - 对数正态分布，dlnorm
  - 柯西分布，dcauchy
  - 逻辑斯谛分布，dlogis

更多分布可以参考 R 网站 [https://cran.r-project.org/web/views/Distributions.html](https://cran.r-project.org/web/views/Distributions.html)。

## 正态分布

### 随机数

```r
rnorm(n, mean = 0, sd = 1)
```

默认使用均值为 0 标准差为 1的标准分布。

如果想生成固定的随机数，可以使用 `set.seed()` 函数设置 seed。

```r
> set.seed(1303)
> rnorm(50)
 [1] -1.1439763145  1.3421293656  2.1853904757  0.5363925179
 [5]  0.0631929665  0.5022344825 -0.0004167247  0.5658198405
 [9] -0.5725226890 -1.1102250073 -0.0486871234 -0.6956562176
[13]  0.8289174803  0.2066528551 -0.2356745091 -0.5563104914
[17] -0.3647543571  0.8623550343 -0.6307715354  0.3136021252
[21] -0.9314953177  0.8238676185  0.5233707021  0.7069214120
[25]  0.4202043256 -0.2690521547 -1.5103172999 -0.6902124766
[29] -0.1434719524 -1.0135274099  1.5732737361  0.0127465055
[33]  0.8726470499  0.4220661905 -0.0188157917  2.6157489689
[37] -0.6931401748 -0.2663217810 -0.7206364412  1.3677342065
[41]  0.2640073322  0.6321868074 -1.3306509858  0.0268888182
[45]  1.0406363208  1.3120237985 -0.0300020767 -0.2500257125
[49]  0.0234144857  1.6598706557
```
