---
title: nurbs_001
mathjax: true
date: 2024-08-01 23:23:49
tags:
---

# NURBS-001

> 都是有理由的。

# 1. Bezier曲线

[Tutorial - from POMAX](https://pomax.github.io/bezierinfo/)

## 1.1 多项式曲线

$$
b_{i,n} = \dbinom ni \cdot(1-t)^{n-i}\cdot t^i
$$

基函数乘上点即可得到参数曲线。
$$
B(t) = \sum_{i=1}^n b_{i,n} \cdot \bf P_i
$$

## 1.2 有理化

即给每个点进一步加权，并进行归一化，得到有理Beizier曲线，这种表示扩展了贝塞尔曲线，使之能够表示标准的圆。
$$
B(t) = \frac{\sum_{i=1}^n b_{i,n} \cdot w_i \cdot \bf P_i }{\sum_{i=1}^n b_{i,n} \cdot w_i}
$$
调整这个新增的权重（compared with previous point weight），可以看到收尾两端仍然被固定在给定的点上，只有曲线被各个点吸引的趋势有所改变，就像重力一样。

如果给定的$t$大于1了，则我们能看到这个多项式曲线的更多部分，本质上贝塞尔曲线是一个多项式曲线的有限部分。

## 1.3 矩阵形式

> why: 矩阵可逆会带来诸多性质，三角矩阵也有诸多性质

$$
B(t) = \begin{bmatrix}
1 && t && t^2
\end{bmatrix}\begin{bmatrix}
1 && 0 && 0 \\
-2 && 2 && 0 \\
1 && -2 && 1 
\end{bmatrix}\begin{bmatrix}
P_1 \\ P_2 \\ P_3
\end{bmatrix}
$$



## 1.4 递归生成 - de Casteljau算法

[de casteljau -  WIKI](https://en.wikipedia.org/wiki/De_Casteljau%27s_algorithm)

## 1.5 曲线的分割

参数点两侧的曲线仍然是可以通过de Casteljau算法生成的， 也可以通过[矩阵形式进行分割](https://pomax.github.io/bezierinfo/#matrixsplit)。





# 2. B-Spline（B样条）

## 1.1 Knot Vectors

[节点向量教程](https://saccade.com/writing/graphics/KnotVectors.pdf)

[物理上的节点向量](https://www.core77.com/posts/55368/When-Splines-Were-Physical-Objects)

节点被定义在参数曲线的**定义域**上，节点向量定义了（NURBS）曲线对应多项式绘图的范围，**节点是固定在真实曲线上的**。

一些规则，暂时忽略阶数和度数的区别

- 控制点的数量总是大于等于曲线的阶数。
- knot vector元素的数量总是等于阶数+控制点数目
- 曲线的阶数至少为2
- 节点向量是非减的
- 曲线定义在$[u_{min},u_{max})$上，下限由阶数定义，上限由控制点数目定义
- 节点向量的绝对值没有意义

### Pinned Uniform

* 曲线在两端和控制点重叠，中间部分曲线不通过控制点
* 局部影响：如果控制点的数量等于阶数，那么移动控制点整个曲线都会运动；如果控制点的数量大于阶数，那么只会影响控制点附近的曲线
* 这种情况下的节点向量，前$k$（阶数）个和后$k$个节点的值是相同的，中间是均匀递增的。

### Piecewise Bezier

* 前$k$个点的值相同，后每$k-1$个点的值相同，均匀增加直到结尾
* 控制点的数目至少为$nk-1$，其中$n$为曲线被划分的段数
* 分段的位置为joint，与两侧控制点形成的直线如果共线则有连续性，反之没有

## 1.2 Curve Order的影响

* 移动控制点的效果受阶数的影响，阶数越高移动单个控制点的效果约明显。

* 阶数越高绘制越复杂，通常高于3阶的曲线不被用户直接使用

# 3. NURBS基本概念

## 2.1 非均匀

## 2.2 有理



