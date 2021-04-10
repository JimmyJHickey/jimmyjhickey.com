---
layout: post
comments: false
title: Example Problems on Fubini's Theorem
description: ST779 Homework 9 on Fubini's Theorem
tags: ST779 Measure-Theory Fubini's -heorem Random-Variables
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $p_{1}, \dots , p_{k} > 1$, be such that $\sum_{j=1}^{k} p_{j}^{-1} = 1$. Let $X_{j}$, $j=1, \dots , k$, be random variables such that $\lVert X_{j} \rVert_{p_{j}} := \Big( E \mid X_{j}\mid^{p_{j}} \Big)^{1/p_{j}} < 
\infty$. Then show that $E \Big[ \prod_{j=1}^{k} \mid X_{j} \mid \Big] \leq \prod_{j=1}^{k} \lVert X_{j} \rVert_{p_{j}}$.**



# 2
**Let $X$ and $Y$ be independent random variables, $p \geq 1$, and $E(Y) = 0$. Show that for any $x$, $E \mid Y + x \mid^{p} \geq \mid x \mid^{p}$.**

**Show that for $E \mid X \mid^{p} \leq E \mid X+Y \mid^{p}$.**




# 3
**Show that $\int_{0}^{\infty} e^{-x^{2}/2} dx = \sqrt{ \pi / 2 }$.**



# 4
**If $X$ is a positive random variable and $\alpha > 0$, show that**

$$
E(X^{\alpha}) = \alpha \int_{[0, \alpha)} x^{\alpha-1}P(X > x) dx,
$$

**where $dx$ in the right hand side stands for integration with respect to the Lebesgue measure.**



# 5
**For a Borel measurable integration function $f$ on $\mathbb{R}$, show that**

$$
\int \int f(x-y)f(y) dy dx \geq 0.
$$