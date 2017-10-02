---
title: Description of an Alembic
category: ML
feature_image: "https://unsplash.it/1200/400?image=200"
---

## EM的一个一般性的解释

### 出发点
最大化 likelihood function 
$p(X|\theta) = \sum_{Z}p(X,Z|\theta)$
$\ln p(X|\theta) = \sum_{Z}q(Z)\ln p(X| \theta)
=\sum_{Z}q(Z)\ln \sum_{Z}p(X,Z|\theta)$
其中 $q(Z)$ 是隐变量的概率分布

### 推导

$\ln p(X|\theta) = L(q,\theta) + KL(q||p)$

Part1: $L(q,\theta) = \sum_{Z}q(Z)\ln\{\frac{p(X,Z|\theta)}{q(Z)}\}$

Part2: $KL(q||p)=-\sum_{Z}q(Z)\ln\{\frac{p(Z|X,\theta)}{q(Z)}\}$

注意到 $L(q,\theta)$ 是 $q(Z)$ 的泛函和 $\theta$ 的函数，同时 $KL(q||p)\ge 0$。

### 方法
思路是通过优化 $q(Z)$，使得 $L(q,\theta) = \ln p(X|\theta)$，通过优化 $\theta$，使得 $L(q,\theta)$ 进一步增大，前一步骤中，$\ln p(X|\theta)$ 保持不变，后一步骤中，$\ln p(X|\theta)$ 增大，因为它的两个部分都增大。

我们可以通过E步骤和M步骤，分别优化 $q(Z)$ 和 $\theta$。
* E步骤：
$q(Z) = p(Z|X,\theta^{old})$
* M步骤：
$\theta = arg\max_{\theta}Q(\theta,\theta^{ild})$