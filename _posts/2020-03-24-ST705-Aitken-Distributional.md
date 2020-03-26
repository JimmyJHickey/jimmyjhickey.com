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

Our $V$ looks like

$$
\begin{bmatrix}
1 + \alpha^2 & \alpha & 0 & \dots \\
\alpha & 1 + \alpha^2 & \alpha & 0 & \dots \\
0 & \alpha & 1 + \alpha^2 & \alpha &  & \\
\vdots & & \ddots & \ddots & \ddots  \\
0& 0 &  \dots & \alpha & 1 + \alpha^2 
\end{bmatrix}
$$

We can use the [Cholesky-Crout algorithm](https://en.wikipedia.org/wiki/Cholesky_decomposition#The_Cholesky%E2%80%93Banachiewicz_and_Cholesky%E2%80%93Crout_algorithms) to calculate $L$.

$$
\begin{align}
L_{j,j} & = \pm \sqrt{ V_{j,j} - \sum_{k=1}^{j-1} L^2_{j,k} } \\
L_{i,j} & = \frac{ 1 }{ L_{j,j} } \Big( V_{i,j} - \sum_{k=1}^{j-1} L_{i,k} L_{j,k} \Big) & i > j \\
L_{i,j} & = 0 & i < j
\end{align}
$$


Let's calculate some of the values of $L$.

$$
\begin{align}
L_{1,1} & = \sqrt{ V_{11} } \\
	& = \sqrt{ 1 + \alpha^2 } \\
L_{2,1} & = \frac{ V_{21} }{ L_{11} } \\
	& = \frac{ \alpha }{ \sqrt{ 1 + \alpha^2 } } \\
L_{3,1} & = \frac{ V_{31} }{ L_{11} } \\
	& = \frac{ 0 }{ L_{11} } \\
	& = 0
\end{align}
$$

Notice that the rest of the first column will also be 0. Now we can proceed with column 2.

$$
\begin{align}
L_{2,2} & = \sqrt{ A_{22} - L_{21}^2 } \\
	& = \sqrt{ 1 + \alpha^2 - \Big( \frac{ a }{ \sqrt{1 + \alpha^2} } \Big)^2} \\
	& = \sqrt{ \alpha^2 + \frac{ 1 }{ 1 + \alpha^2 } } \\
L_{3,2} & = \frac{ A_{32} - L_{31}L_{21} }{ L_{22} } \\
	& = \frac{ \alpha - 0 }{ \sqrt{ \alpha^2 + \frac{ 1 }{ 1 + \alpha^2 } } } \\
L_{4,2} & = \frac{ A_{42} - L_{41}L_{31} }{ L_{22}} \\
	& = \frac{ 0 - 0 \cdot L_{31} }{  \sqrt{ \alpha^2 + \frac{ 1 }{ 1 + \alpha^2 } }} \\
	& = 0
\end{align}
$$

Notice that the rest of the second column will also be 0. In general,

$$
\begin{align}
L_{j,j} & = \sqrt{ 1 + \alpha^2 - (0 + \dots + 0  + L_{j, j-1}^2)} \\
	& = \sqrt{ 1 +\alpha^2 - L_{j, j-1}^2 } \\
L_{j+1, j} & = \frac{ 1 }{ L_{j,j} } \Big( A_{j+1,j} - L_{j+1, 1} L_{j, 1} - \dots - L_{j+1, j-1}, L_{j, j-1} \Big) \\
	& = \frac{ 1 }{ L_{j,j} } \Big( \alpha - 0 \cdot 0- \dots - 0 \cdot L_{j, j-1} \Big) \\
	& = \frac{ \alpha }{ L_{j,j} } \\
L_{j+x , j} & = \frac{ 1 }{ L_{j,j} } \Big( A_{j+x,j} - L_{j+x, 1} L_{j, 1} - \dots - L{j+x, j-1}, L_{j, j-1} \Big) \\
	& = \frac{ 1 }{ L_{j,j} } \Big( 0 - 0 \cdot 0- \dots - 0 \cdot L_{j, j-1} \Big) \\
	& = 0.
\end{align}
$$




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

Take $X \sim N(0,1)$ and $Y = X^2$. Notice that $Y$ and $X$ are dependent. However,

$$
\begin{align}
Cov(X, Y) & = Cov(X, X^2) \\
	& = E(X X^2) - E(X) E(X^2) \\
	& = E(X^3) - E(X) E(X^2) \\
	& = 0 - 0 \cdot E(X^2) \\
	& = 0.
\end{align}
$$

These random variables, while dependent, have 0 covariance because covariance and correlation are a measure of linear relationship. There is no linear relationship between $X$ and $Y$, but rather a quadratic relationship.

# 8 (5.6)
**(Another derivation of the central chi-square distribution)**

## a
**Let $Z \sim N(0,1)$; find the density of $U_1 = Z^2$.**


## b
**Let $U_1, U_2$ be independent, each with $\chi_1^2$ distribution. Find the density of $U_1 + U_2$ directly using transformation rules.**



## c
**Let $U_i, i = 1, \dots , p$ be iid $\chi_1^2$. Find the density of $U_1 + \dots + U_p$**