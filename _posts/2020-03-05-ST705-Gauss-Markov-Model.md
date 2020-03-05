---
layout: post
comments: false
title: Example Problems on the Gauss-Markov Model
description: ST705 Homework 8 on the Gauss-Markov Model
tags: ST705 Linear-Algebra Gauss-Markov Statistics
category: ST705
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1 (4.3)
**In Example 4.8 (heteroskedasticity) find $Var(\widehat b_{OLS})$ and compare it to $Var(\widehat b_{GLS})$.**




# 2 (4.8)
**(Compare with Example 4.10 (equicorrelation).) Consider the linear model $y = Xb + e$ where $e = u + Z 1$ (Z is a scalar random variable), where $Cov(u) = \sigma^2 I_N$, $Var(Z) = \tau^2$, and $Z$ and $u$ are uncorrelated. Find $V$ and derive condisitions under which the OLS estimator of every estimable function is BLUE.**




# 3 (4.9)
**If $X$ has full-column rank and $C^T y$ is also unbiased for estimable $\Lambda^T b$, show that $Cov(C^T y) - Cov(\Lambda^T \widehat b)$ is nonnegative definite.**




# 4 (4.12)
**Prove the Gauss-Markov Theorem directly, that is, by constructing all linear estimators $a^T y$ that are unbiased for $\lambda^T b$ (find a family of solutions $a(z)$), and then minimizing the variance of $\sigma^2 a^T a$.**




# 5 (4.26)
**Ridge regression is a technique that has been recommended by some statisticians to address multicollinearity problems arising in multiple regression. In our usual linear models framework with $E(y) = X b$, and $Cov(y) = \sigma^2 I_N$, the ridge regression estimator takes the form**

$$
\widetilde b = (X^T X + k I_P)^{-1} X^T y
$$

**where $k>0$. Assume here that $X$ is full-column rnak, that is, $\text{rank}( X ) = p$.**

## a
**Find $E(\widetilde b)$.**




## b
**Is $\lambda^T \widetilde b$ and unbiased estimator of $\lambda^T b$?**



## c
**Find $Cov(\widetilde b)$.**



## d
**Mean squared error is commonly used to assess the quality of an estimator. For the ridge regression estimator $\widetilde  b$, find the mean squared error**

$$
E\Big(||\widetilde b - b ||^2\Big) = E\Big( (\widetilde  b - b)^T(\widetilde b - b) \Big)
$$




## e
**Consider applying ridge regression to a multivariate regression problem with two centered covariates ($\sum x_i = \sum z_i = 0$), taking the form**


$$
Xb = 
\begin{bmatrix}
	1 & x_1 & z_1 \\
	1 & x_2 & z_2 \\
	\vdots & \vdots & \vdots \\
	1 & x_N & x_N
\end{bmatrix}
\begin{bmatrix}
	\beta_0 \\
	\beta_1 \\
	\beta_2
\end{bmatrix}
$$


**yielding the inner product matrix**


$$
\begin{bmatrix}
	N & 0 & 0 \\
	0 & \sum x_i^2 & \sum x_i z_i \\
	0 & \sum x_i z_i & \sum z_i^2
\end{bmatrix}.
$$


**For simplicity, suppose $N = 10$, $\sum x_i^2 = \sum z_i^2 = 5$, and $\sum x_i z_i = 4$.**



**Find the covariance matrix of our usual least squares estimator $\widehat b = (X^T X)^{-1} X^T y$ in this situation.**




## f
**Find a value of $k$ such that one component of $\widetilde  b$ (your choice of component) has smaller variance than the corresponding least squares estimator.**




## g
**Part (f) looks like it violates the Gauss-Markov Theorem, Does it?**



# 6 (4.27)
**Principal components regression is considered another alternative to least squares estimators in the case of multicollinearity. Begin with the singular value decomposition matrix**

$$
X = U
\begin{bmatrix}
	\Lambda \\
	0
\end{bmatrix}
V^T = 
U_1 \Lambda V^T,
$$

**partitioning off the first $p$ columns of $U$, and express the least squares estimator as $\widehat b = V \Lambda^-1 U_1^T y$.
Setting some of the small singular values to zero, and using**

$$
\Lambda_*^- = diag\{\lambda_1^{-1}, \dots , \lambda_k^{-1}, 0, \dots , 0\},
$$ 

**changing the rank from $p$ to $k$, leads to the estimator $\widetilde b = V \Lambda_*^- U_1^T y$. Find its bias and mean squared error.**

