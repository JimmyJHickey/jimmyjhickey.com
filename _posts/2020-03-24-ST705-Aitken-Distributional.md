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

We can also represent the elements of $L$ as a repeated fraction. Let's look at the $V \in \mathbb{R}^{5x5}$ case for some intuition.

$$
L = \left(
\begin{array}{ccccc}
 \sqrt{a^2+1} & 0 & 0 & 0 & 0 \\
 \frac{a}{\sqrt{a^2+1}} & \sqrt{-\frac{a^2}{a^2+1}+a^2+1} & 0 & 0 & 0 \\
 0 & \frac{a}{\sqrt{-\frac{a^2}{a^2+1}+a^2+1}} & \sqrt{-\frac{a^2}{-\frac{a^2}{a^2+1}+a^2+1}+a^2+1} & 0 & 0 \\
 0 & 0 & \frac{a}{\sqrt{-\frac{a^2}{-\frac{a^2}{a^2+1}+a^2+1}+a^2+1}} & \sqrt{-\frac{a^2}{-\frac{a^2}{-\frac{a^2}{a^2+1}+a^2+1}+a^2+1}+a^2+1} & 0 \\
 0 & 0 & 0 & \frac{a}{\sqrt{-\frac{a^2}{-\frac{a^2}{-\frac{a^2}{a^2+1}+a^2+1}+a^2+1}+a^2+1}} & \sqrt{-\frac{a^2}{-\frac{a^2}{-\frac{a^2}{-\frac{a^2}{a^2+1}+a^2+1}+a^2+1}+a^2+1}+a^2+1} \\
\end{array}
\right)
$$

As $\lim_{N \rightarrow \infty} \frac{\alpha^2}{1+\alpha^2-b} \rightarrow 1$ where $b = \frac{\alpha^2}{1+\alpha^2}$. Thus,

$$
\begin{align}
L_{j,j} & \rightarrow \sqrt{ 1+ \alpha^2 -1 } \\
	& = \alpha \\
L_{j+1, j} & \rightarrow \frac{ \alpha }{ \alpha } \\
	& = 1
\end{align}
$$


# 2 (4.21)
**Under the Aitken model, with $Cov(e)= \sigma^2 V$ if $cov(a^T y, d^T \widehat e) = 0$ for all $d$, then is $a^T y$ still the BLUE for its expectation?**

$$
\begin{align}
0 = Cov(a^t y, d^t \widehat e) & = a^t Cov(y, \widehat e) d \\
	& = a^T Cov(y, (I-P_x)y)d \\
	& = a^T Cov(y,y) (I-P_x)d \\
	& = a^T \sigma^2 V (I-P_x) d \\
0 & = a^T V (I-P_x) d & \forall d \\
0 & = a^T V(I_Px) \\
0^T & = (I-P_x) (a^T V)^T \\
0 & = (I-P_x) V a
\end{align}
$$

Thus, $Va \in \text{ column }( X )$. Thus, $a^T y$ is BLUE.


# 3 (4.22)
**Prove Aitken's Theorem (Theorem 4.2) indirectly using Corollary 4.1. Is this argument circular, that is, does the corollary use Aitken's Theorem?**

We need to check that $V t \in \text{ column }( X )$ with

$$
\begin{align}
t^T y = \lambda^T \widehat \beta_{GLS} = \lambda^T (X^T V^{-1} X)^g X^T V^{-1} y.
\end{align}
$$

$$
\begin{align}
V t &  = V(\lambda^T (X^T V^{-1} X)^g X^T V^{-1})^T \\
	& = V V^{-1} X (X^T V^{-1} X)^g \lambda \\
	& = X (X^T V^{-1} X)^g \lambda \\
	& \in \text{ column }( X )
\end{align}
$$

This argument is not circular. While Corollary 4.1 does assume the Aitken model, it does not use Aitken's Theorem.

# 4 (4.23)
**Prove Aitken's Theorem (Theorem 4.2) directly. Consider the Aitken model, and let $\lambda^T b$ be estimable. Let $a^T y$ be a linear unbiased estimator of $\lambda^T b$. Show that**

$$
Var(a^T y) = Var(\lambda^T \widehat b_{GLS}) + Var(a^T y - \lambda^T \widehat b_{GLS})
$$


$$
\begin{align}
Var(a^T y) & = Var(a^T y - \lambda^T \widehat b_{GLS} + \lambda^T \widehat b_{GLS}) \\
	& = Var(\lambda^T \widehat b_{GLS}) + Var(a^T y - \lambda^T \widehat b_{GLS}) + 2 Cov(a^T y - \lambda^T \widehat b_{GLS}, \lambda^T \widehat b_{GLS}) \\ \\
Cov(a^T y - \lambda^T \widehat b_{GLS}, \lambda^T \widehat b_{GLS}) & = Cov(a^T y - \lambda^T (X^t V^{-1} X)^g X^t V^{-1} y, \lambda^T (X^t V^{-1} X)^g X^t V^{-1} y) \\
	& = (a^T - \lambda^T (X^t V^{-1} X)^g X^t V^{-1}) Cov(y,y) (\lambda^T (X^t V^{-1} X)^g X^t V^{-1})^T \\
	& = (a^T - \lambda^T (X^t V^{-1} X)^g X^t V^{-1}) \sigma^2 V (\lambda^T (X^t V^{-1} X)^g X^t V^{-1})^T \\
	& = \sigma^2 \Big( (a^T - \lambda^T (X^t V^{-1} X)^g X^t V^{-1}) V V^{-1} X (X^T V^{-1} X)^g \lambda \Big) \\
	& = \sigma^2 \Big( a^T X (X^T V^{-1} X)^g \lambda  - \lambda^T (X^t V^{-1} X)^g X^t V^{-1} X (X^T V^{-1} X)^g \lambda \Big) \\
	& = \sigma^2 \Big( \lambda^T (X^T V^{-1} X)^g \lambda  - \lambda^T (X^T V^{-1} X)^g \lambda \Big) \\
	& = 0
\end{align}
$$

Where the second to last step comes from question 5 of the practice midterm.

Thus,

$$
Var(a^T y) = Var(\lambda^T \widehat b_{GLS}) + Var(a^T y - \lambda^T \widehat b_{GLS}).
$$

# 5 (5.2)
**Let $Z \sim N_p(0, I_p)$, and let $A$ be a $p \times p$ matrix such that $A A^T = V$.**

## a
**Show that if $Q$ is an orthogonal matrix, then $QZ \sim N_p(0, I_p)$**

$$
\begin{align}
Q Z & \sim N_p(Q \mu, Q \Sigma Q^T) \\
	& = N_p (Q \cdot 0, Q I_p Q^T) \\
	& = N_p(0, Q Q^T) \\
	& = N_p(0, I_p)
\end{align}
$$

## b
**Show that $(AQ)(AQ)^T = V$.**

$$
(AQ)(AQ^T) = AQ Q^T A^T = A I_p A^T = V
$$



## c
**Show that $X = \mu + AQZ \sim N_p(\mu , V)$.**


$$
\begin{align}
X & \sim N_p(\mu + AQ \cdot 0, (AQ) I_p (AQ)^T) \\
	& = N_p(\mu, (AQ)(AQ)^T) \\
	& = N_p(\mu, V)
\end{align}
$$

# 6
**Recall the definition of the multivariate normal distribution from class:**

---

_Definition:_

**The $p$-dimensional random vector $Y$ is said to follow the multivariate normal distribution with mean $\mu$ and covariance matrix $\Sigma$ if for every $p$-dimensional vector $v$ such that $v'\Sigma v \ne 0$,**

$$
v'Y \sim \text{N}(v'\mu,v'\Sigma v).
$$

**Denote $Y \sim \text{N}_{p}(\mu,\Sigma)$.**

---

**Prove that if $\Sigma$ is nonsingular, then $Y \sim \text{N}_{p}(\mu,\Sigma)$ if and only if $Y$ has density,**

$$
f(y) = \det(2\pi\Sigma)^{-\frac{1}{2}}e^{-\frac{1}{2}(y-\mu)'\Sigma^{-1}(y-\mu)}.
$$


Without loss of generality, let's take $Z = A^{-1}(Y-\mu)$ where $A A^T = \Sigma$.


$\Leftarrow$


$$
\begin{align}
f(z) & = (2 \pi)^{-p/2} e^{-z^T z / 2} \\
	& = (2 \pi)^{-p/2} e^{-1 / 2 \sum z_i^2} \\
	& = \prod \frac{ 1 }{ \sqrt{ 2 \pi } } e^{1/2 z_i^2}
\end{align}
$$


Since the joint is the product of the marginals, $Z_i \stackrel{ \text{iid}}{\sim} N(0,1)$. Thus, $v^T Z = \sum v_i Z_i$. Since the sum of univariate normals is still normal, we know that $Z \sim N_p(0,1)$. We can then transform this back to $Y$. Since $v^T Y = v^T (AZ + \mu)$, by normal transformation rules, we know that $Y \sim N(v^T \mu, v^T \Sigma v)$


$\Rightarrow$

Take $v = e_1, \dots e_p$. Then $Z_i = e_i^T z$.

$$
Z_i \sim N(e_i^T \cdot 0, e_i^T I e_i) = N(0,1)
$$

Now we need to show that the multivariate joint is the product of the marginals.

Since $\Sigma = Cov(Z) = I$, we know that $Cov(Z_i, Z_j) = 0$ for $i \neq j$. All normal distributions with no covariance are independent, so $Z_i \perp Z_j$. Then,

$$
f_Z(z) = \prod f_{Z_i}(z_i).
$$

This is the expected density. We could transform back to $Y$ using the Jacobian Method.


$$
\begin{align}
f_Y(y) & = f_Z(y) \cdot | J(AZ + \mu) | \\
	& = f_Z(y) \cdot | A^{-1} | \\
	& = f_Z(y) \cdot | \Sigma |^{-1/2} \\ 
	& = |\Sigma |^{-1/2} \frac{ 1 }{ \sqrt{ 2\pi } } e^{\frac{ -1 }{ 2 }z^T z} |_{z=y}\\
	& = |\Sigma |^{-1/2} \frac{ 1 }{ \sqrt{ 2\pi } } e^{\frac{ -1 }{ 2 }(y - \mu)^T (A^{-1})^T A^{-1} (y - \mu)}\\ 
	& = | 2 \pi \Sigma |^{-1/2} e^{-\frac{1}{2}(y-\mu)'\Sigma^{-1}(y-\mu)}
\end{align}
$$

Thus, $Y \sim N_p(\mu, \Sigma)$.

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

$$
\begin{align}
M_{U_1}(t) & = E(e^{t z^2}) \\
	& = \int_{-\infty}^{\infty} e^{t z^2} \frac{ 1 }{ \sqrt{ 2 \pi } } e^{-z^2 / 2} dz \\
	& = \int_{-\infty}^{\infty} \frac{ 1 }{ \sqrt{ 2 \pi } } e^{z^2 (t - 1/ 2)} dz \\
	& = \frac{ 1 }{ \sqrt{ 2 \pi } } \frac{ \sqrt{ \pi } }{ \sqrt{ \frac{ 1 }{ 2 } - t} } \\
	& = (1 - 2t)^{-1/2} \\
	& \sim \chi_1^2
\end{align}
$$

## b
**Let $U_1, U_2$ be independent, each with $\chi_1^2$ distribution. Find the density of $U_1 + U_2$ directly using transformation rules.**

Take $X = U_1 + U_2$.

$$
\begin{align}
M_X(t) & = E(e^{t (U_1 + U_2)}) \\
	& = E(e^{tU_1} e^{t U_2}) \\
	& = E(e^{tU_1}) E(e^{tU_2}) & \text{independence} \\
	& = \Big( (1 - 2t)^{-1/2} \Big)^2 \\
	& = (1 - 2t)^{-2/2} \\
	& \sim \chi_2^2
\end{align}
$$

## c
**Let $U_i, i = 1, \dots , p$ be iid $\chi_1^2$. Find the density of $U_1 + \dots + U_p$**

Take $Y = \sum_{i=1}^{p} U_i$.

$$
\begin{align}
M_Y(t) & = E(e^{t \sum U_i}) \\
	& = E(\prod e^{t U_i}) \\
	& \prod E(e^{t U_i}) & \text{independence} \\
	& = (1 - 2t)^{-p/2} \\
	& \sim \chi^2_p
\end{align}
$$
