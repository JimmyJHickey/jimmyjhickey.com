---
layout: post
comments: false
title: Example Problems on the Central Limit Theorem
description: ST779 Homework 10 on the Central Limit Theorem
tags: ST779 Measure-Theory CLT
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**If $X_1, X_{2}, \dots$ are iid with expectation zero and finite variance, show that $\sum_{i=2}^{\infty} \frac{ X_{n} }{ \sqrt{ n } \log(n)}$ is a.s. convergent and that $(\sum_{i=2}^{n}X_{i}) / (\sqrt{ n } \log(n)) \rightarrow 0$ a.s.**



# 2
**Let $X_{n}$ be independent uniform $[-a_{n}, a_{n}]$, $n = 1, 2, \dots$, where $\\{ a_{n} \\}$ is a bounded sequence. Show that the Lindeberg condition for the array $\\{ X_1, \dots , X_n \\}$, $n = 1, 2, \dots$ holds if and only if $\sum_{n=1}^{\infty} a_{n}^{2} = \infty$.**




# 3
**Let $X_{n}$ be independent gamma distributed with shape parameter $2^{-n}$ and scale parameter 1, and $S_{n} = \sum_{i=1}^{n} X_{i}$, $n = 1, 2, \dots $. Show that the Lindeberg condition fails for the array $\\{X_{1}, \dots , X_{n} \\}$, $n = 1, 2, \dots$ and the central limit theorem does not hold, i.e. $(S_{n} - E(S_{n}))/\sqrt{ \text{var}(S_{n}) }$ doe not go to $N(0,1)$ in distribution.**




# 4
**Let $(U_{1,n} , \dots , U_{n,n})$ be a sequence of random vectors uniformly distributed over the set $\\{ (u_{1}, \dots u_{n} : \sum_{i=1}^{n} u_{i}^{2} = n \\}$. Show that $U_{1,n} \stackrel{ \text{d}}{\rightarrow} N(0,1)$.**



# 5
**Let $X_{1}, X_{2}, \dots $ be iid with pdf $f(x) = \mid x \mid ^{-3}$, $\mid x \mid > 1$. Show that $X$ has infinite variance, but $\sum_{i=1}^{n} X_{i} / \sqrt{ n \log(n) } \stackrel{ \text{d}}{\rightarrow} N(0,1)$.**