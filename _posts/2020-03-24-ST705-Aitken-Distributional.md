---
layout: post
comments: false
title: Example Problems on the Aitken Model and Distributional Theory
description: ST705 Homework 9 on the Aitken Model and Distributional Theory
tags: ST705 Linear-Algebra Aitken Distributional Statistics
category: ST705
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1 (4.15)
**Let $\sigma^2 V$ be the $N \times N$ covariance matrix for a first-order moving average process:**

$$
\begin{align}
V_{ij} & = 1 + \alpha^2 & \text{if } i =j \\
V_{ij} & = \alpha & \text{if } |i - j| = 1 \\
V_{ij} & = 0 & \text{if } |i - j| > 1
\end{align}
$$

**Notice that $V$ is banded with zeros outside of three bands, on the diagonal and above and below the diagonal.**

## a
**Show that the Cholesky factor of $V$ is also banded (lower triangular, with nonzeros on the diagonal and below the diagonal).**



## b
**Find the limit of the two nonzero elements in row $N$ as $N \rightarrow \infty$.**




# 2 (4.21)
**Under the Aitken model, with $Cov(e)= \sigma^2 V$ if $cov(a^T y, d^t \widehat e) = 0$ for all $d$, then is $a^T y$ still the BLUE for its expectation?**



# 3 (4.22)
**Prove Aitken's Theorem (Theorem 4.2) indirectly using Corollary 4.1. Is this argument circular, that is, does the corollary use Aitken's Theorem?**



# 4 (4.23)
**Prove Aitken's Theorem (Theorem 4.2) directly. Consider the Aitken model, and let $\lambda^T b$ be estimable. Let $a^T y$ be a linear unbiased estimator of $\lambda^T b$. Show that**

$$
Var(a^T y) = Var(\lambda^T \widehat b_{GLS}) + Var(a^T y - \lambda^T \widehat b_{GLS})
$$


# 5 (5.2)
**Let $Z \sim N_p(0, I_p)$, and let $A$ be a $p \times p$ matrix such that $A A^T = V$.**

## a
**Show that if $Q$ is an orthogonal matrix, then $QZ \sim N_p(0, I_p)$**



## b
**Show that $(AQ)(AQ)^T = V$.**




## c
**Show that $X = \mu + AQZ \sim N_p(\mu , V)$.**

# 6
**Recall the definition of the multivariate normal distribution from class:**

---

_Definition:_

**The $p$-dimensional random vector $Y$ is said to follow the multivariate normal distribution with mean $\mu$ and covariance matrix $\Sigma$ if for every $p$-dimensional vector $v$ such that $v'\Sigma v \ne 0$,**

$$
v'Y \sim \text{N}(v'\mu,v'\Sigma v).
$$

---

**Denote $Y \sim \text{N}_{p}(\mu,\Sigma)$.**


**Prove that if $\Sigma$ is nonsingular, then $Y \sim \text{N}_{p}(\mu,\Sigma)$ if and only if $Y$ has density,**

$$
f(y) = \det(2\pi\Sigma)^{-\frac{1}{2}}e^{-\frac{1}{2}(y-\mu)'\Sigma^{-1}(y-\mu)}.
$$




# 7
**Construct two random variables that have zero correlation, but are _not_ independent.**





# 8 (5.6)
**(Another derivation of the central chi-square distribution)**

## a
**Let $Z \sim N(0,1)$; find the density of $U_1 = Z^2$.**


## b
**Let $U_1, U_2$ be independent, each with $\chi_1^2$ distribution. Find the density of $U_1 + U_2$ directly using transformation rules.**



## c
**Let $U_i, i = 1, \dots , p$ be iid $\chi_1^2$. Find the density of $U_1 + \dots + U_p$**