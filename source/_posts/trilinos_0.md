---
title: Trilinos
date: 2024-07-25 17:48:43
tags:
---

# Trilinos-001

## 0. Trilinos相关资源

1. [Github页面](https://github.com/trilinos/Trilinos)

2. [Trilinos Home Page-官方主页](https://trilinos.github.io/)：由sandia实验室创建

3. [文档页面](https://trilinos.github.io/documentation.html)：DOXYGEN
4. [Overview-slide](https://www.osti.gov/servlets/purl/1727326)：可以看到各种求解器的说明
5. [WIKI](https://en.wikipedia.org/wiki/Trilinos)

## 1. 安装

### 1. 指令

目标是在ubuntu 16.04版本上安装trlinos的[Epetra](https://trilinos.github.io/epetra.html)，[AMESOS](https://trilinos.github.io/amesos.html)，[BELOS](https://trilinos.github.io/belos.html)和[AZTECOO](https://trilinos.github.io/aztecoo.html)。

```bash
 sudo apt-get install libboost-all-dev libblas-dev liblapack-dev binutils-dev binutils-dev libtbb-dev libmumps-dev libsuperlu-dev libptscotch-dev libhdf5-openmpi-dev libiberty-dev clang-3.7 doxygen libxerces-c-dev -y
```

### 2. 一些教训

基于trilinos-12-4在ubuntu16.04上的状态（for IGATOOLS）

1. 要用源码编译，不然在链接对应的库会有符号表冲突（c++11和c++14），apt安装得到的是c++11版本的
2. 缺失"mpi.h"时需要在编译的flag中将"-I/usr/local/include/openmpi"引入（即头文件的位置）
3. `ldd -r`，`nm -D`，`c++filt`，`readelf`可以用来检查undefined reference或者undefined symbol问题

## 2. 几个库的介绍

### 1. 线性代数库-Epetra

[Epera-DOC](https://docs.trilinos.org/dev/packages/epetra/doc/html/index.html)

### 2. 稀疏求解器-AMESOS

[AMESOS-DOC](https://docs.trilinos.org/dev/packages/amesos/doc/html/index.html)

### 3. 求解器-BELOS

[BELOS-DOC](https://docs.trilinos.org/dev/packages/belos/doc/html/index.html)

### 4. 求解器-AZTECOO

[AZTECOO-DOC](https://docs.trilinos.org/dev/packages/aztecoo/doc/html/index.html)

## 3. Krylov subspace

矩阵求解的基础： [Krylov subspace- WIKI](https://en.wikipedia.org/wiki/Krylov_subspace)

