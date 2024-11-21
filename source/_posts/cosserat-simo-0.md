---
title: '''cosserat-simo-0'''
mathjax: true
date: 2024-08-14 19:28:13
tags:
---

# A finite strain beam formulation. The three-dimensional dynamic problem. Part I

## 0. Intro

* 本文是在Reissner的工作上的延申
* 是对Kirchhoff-Love杆模型的扩展，引入了finite extension和finite shearing
* configuration是由一个rotation和一个position vector构成的
* 用incremental vorticity（旋量？）描述小的变化



## 1. Basic Kinematics

### 1.1 Moving basis. Kinematic assumption

建模定义几个元素

1. line of centroids
2. 截面法线$n$
3. 截面上的向量$t_1$
4. 与$n$和$t_1$都垂直的$t_2$，记$t_3 =n =  t_1 \times t_2$

通常以直线作为reference configuration，未受力的状态。**需要说明的是$n$并不一定是line of centroids的切线。**

### 1.2 Derivatives of the moving basis

 如果用$SO(3)$的元素表示旋转，可以求其对弧长参数的微分，有反对称矩阵的形式和向量的形式两种写法。

> 如果参考位置不是直线，同样可以找出相应的计算方式。

* 可以计算随体坐标系（convected basis）和移动坐标系(moving basis)的关系，convected basis的$n$分量与中轴线相切，在moving basis的情况下$n$与截面相垂直。在不考虑剪切变形的情况下二者相同。
* 计算一般运行在current configuration（欧拉系，空间坐标系）下，可以通过旋转矩阵和material configuration（拉格朗日系，物质系）变换。
* 计算不考虑截面收缩。

## 2. Motion. Linear and angular momentum

除了以弧长$s$为参数，运动情况下还要考虑时间参数$t$。用$\dot t_I$表示对时间的导数。

同时有如下动量和角动量表示：
$$
L_t = \int_A\rho_0(\xi, S)\dot \phi_t(\xi, S,t) \rm d \it\xi = A_\rho\dot\phi_0(S,t)
$$

$$
H_t = \int_A\rho_0(\xi, S)[x-\phi_0(S,t)] \times \dot \phi(\xi, S,t) \rm d\xi
$$

$$
\dot H_t = I_\rho \dot w + w \times H_t
$$

## 3. Force and torque. equations of motion

同时可以定义单位长度上的外力和力矩如下。
$$
f(S,t) = \int_AP(\xi, S)E_3\rm d \xi
$$

$$
m(S,t) \int_A[x-\phi_0(S,t)] \times T_3(\xi, S) \rm d \xi
$$

平衡方程如下
$$
\frac{\partial }{\partial S}f+\bar q= \dot L_t = A_{\rho}\ddot \phi_0
$$

$$
\frac{\partial }{\partial S}m+ \frac{\partial \phi_0}{\partial S} \times f + \bar m = \dot H_t
$$

* 可以给出相应的物质系变换
* 可以导出经典的kirchhoff-love模型

## 4. Internal power and strain measures. Consititutive equations





## 5. Concluding remarks: The plane case





