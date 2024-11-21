---
title: pde-01
mathjax: true
date: 2024-08-10 19:00:48
tags:
---

# PDE弱形式

## 0. 资源

1. [弱解](https://zh.wikipedia.org/zh-sg/%E5%BC%B1%E8%A7%A3)

2. [COMSOL-弱形式概述](https://cn.comsol.com/blogs/brief-introduction-weak-form)

3. [COMSOL-弱形式的力量](https://cn.comsol.com/blogs/strength-weak-form)

4. [TJ-任晓丹](http://www.renxiaodan.com/userfiles/files/course/FEM/Lecture%202-r.pdf)

## 1. 等效积分的弱形式

### 弱形式的步骤

将微分问题转换为积分问题一般包含两个步骤，第一步是等效积分步骤，第二步是应用分部积分（高斯公式，格林公式的散度定理）。

### 采用弱形式的原因

> 标准的偏微分方程推导过程中存在一个小小的缺陷：即所涉及的函数（特别是材料属性）并不总是足够平滑，从而使方程在某些地方不满足高斯定理的使用条件。由于产生的偏微分方程无法满足在所有物理意义上的合理性，因此称该微分方程过于严格（这就是弱形式发挥作用的地方）。为了返回一个比偏微分方程严格程度低的积分公式，弱方程部分地反转了推导过程。这意味着弱方程实际上比经典方程更接近基础物理学。
>
> 弱形式的力量

