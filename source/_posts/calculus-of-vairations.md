---
title: calculus_of_vairations
mathjax: false
date: 2024-08-01 13:42:15
tags:
mathjax: true
---

# 伽辽金法

从数学的角度看微分方程的数值解法（此处特指有限元方法）可以有如下两种思路

- [Rayleigh-Ritz](https://en.wikipedia.org/wiki/Rayleigh%E2%80%93Ritz_method)法：对于**有变分原理**的问题，将其转化为泛函分析问题，更进一步转换为代数问题，最终求解
- 加权余量法：对于一般的没有变分原理的情况，可以用加权余量法求解
  - 配点法
  - 最小二乘法
  - [Galerkin](https://en.wikipedia.org/wiki/Galerkin_method)法

## 0. 资源

1. [中科大教材-非工程](http://staff.ustc.edu.cn/~humaobin/course/cht/ppt/10.2.pdf)

2. [天深科技-加权余量法](https://www.teesim.com/Theory/FEM06/FEM06.html)
3. [天深科技-里兹法](https://www.teesim.com/Theory/FEM04/FEM04.html)
4. 有限单元法_王勖成
5. [WRM教程-带案例](https://www.iist.ac.in/sites/default/files/people/IN08026/WRM.pdf)

## 1. 加权余量法

加权余量的核心就是：**余量**（残量，残差）+**权函数**

## 1.1 标准步骤

> 1. 选择满足边界条件的试函数（包含基函数和待定系数）。
> 2. 将试函数代入控制方程计算残差。由于试函数不是准确解，将会产生残差或余量（Residual）。
> 3. 用权函数（weight function）乘以上一步中的余量，并在定义域内求积分；该积分等于零，得到关于待定系数的代数方程，解方程可以求出待定系数。

## 1.2 等效积分形式

一般工程问题的可以由微分方程组$\bf{A}\rm({u})$和边界条件$\bf{B}\rm({u})$组成描述，而此描述可以转换成等效积分形式
$$
\int_{\Omega}\bf{v}^TA\bf(u)\rm d\Omega+\int_{\Gamma}\bf \bar{v}^TB\bf(u)\rm d\Gamma = 0
$$
其中$\bf v$和$\bf \bar{v}$是一组和微分方程个数相等的任意函数，**此积分形式对于所有的$\bf v$和$\bf \bar{v}$组合都成立是等效于原问题的**。此外可以通过分部积分提高$\bf v$和$\bf \bar{v}$的连续性要求来降低对微分方程场函数$\bf u$的连续性要求，进而得到问题的**等效积分弱**形式。

在此基础上，利用一组近似函数$\bf N_i$（试探函数，trial function，形函数，shape function，基函数， basis function）来近似$\bf u$。
$$
\bf u \approx \bar{u} = \sum_{i=1}^nN_ia_i 
$$
其中$\bf N_i$是所谓近似函数，$\bf a_i$是一组待定参数。另外如果将等效积分形式中的任意函数$\bf v$和$\bf \bar{v}$替换为指定的**权函数**$\bf W_i$和$\bf \bar{W_i}$则可以得到**近似的等效积分**形式。这个操作同样可以作用在弱形式上。
$$
\int_{\Omega}\bf{W_j}^TA\bf(Na)\rm d\Omega+\int_{\Gamma}\bf \bar{W_j}^TB\bf(Na)\rm d\Gamma = 0， \it j=1...n
$$
或余量形式的
$$
\int_{\Omega}\bf{W_j}^TR\rm d\Omega+\int_{\Gamma}\bf \bar{W_j}^T\bar{R}\rm d\Gamma = 0， \it j=1...n
$$


此时得到一般的加权余量法（weighted residual method， **WRM**），选择不同的**权函数**就可以得到不同的加权余量法。

## 2. 伽辽金法（Galerkin method）

直接取权函数等于试探函数序列，在内部取$W_j = N_j$，在边界上取$\bar{W_j} = -W_j=-N_j$，则可以得到如下形式的伽辽金法。
$$
\int_{\Omega}\bf{N_j}^TR\rm d\Omega -\int_{\Gamma}\bf N_j^T\bar{R}\rm d\Gamma = 0， \it j=1...n
$$
同样的在弱形式上也可以构造相应的伽辽金法。

## 3. 配点法（collocation method）

强迫余量在域内n个点上为零，取权函数为狄拉克函数（[Dirac function](https://en.wikipedia.org/wiki/Dirac_delta_function)），$W_j = \delta(x - x_i)$。由于狄拉克函数的特性，配点法只需要令余量为0就可以构建相应的方程组，来求解待定参数$a_i$。即$\bf R=A(Na) = 0$。

