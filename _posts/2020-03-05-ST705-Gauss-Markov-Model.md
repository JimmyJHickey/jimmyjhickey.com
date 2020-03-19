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

$$
	\begin{align}
		Var(\widehat  \beta_{OLS}) & = Var \Big( \frac{ \sum x_i y_i }{ \sum x_i^2 } \Big) \\
			& = \frac{ 1 }{ (\sum x_i^2)^2 } Var(\sum x_i y_i) \\
			& = \frac{ 1 }{ (\sum x_i^2)^2 } \sum x_i^2 Var(y_i) \\
			& = \frac{ 1 }{ (\sum x_i^2)^2 }  \sum x_i^2 \sigma^2 x_i^2 \\
			& = \sigma^2 \frac{ \sum x_i^4 }{ (\sum x_i^2)^2 } 
	\end{align}
$$


We know that $\widehat \beta_{GLS} = \frac{ \sigma^2 }{ N }$. We can proceed using the Cauchy-Schwartz inequality.


$$
\begin{align}
| \langle u , v \rangle |^2 & \leq \langle u , u \rangle \langle v , v \rangle \\
| u_1 v_1 + \dots + u_n v_n |^2 & \leq (u_1^2 + \dots + u_n^2)(v_1^2 + \dots v_n^2)
\end{align}
$$


Take $u_i = x_i^2$ and $v_i = 1$.

$$
\begin{align}
\Big( \sum_{i=1}^N x_i^2 \Big)^2 & \leq \Big( \sum_{i=1}^{N} x_i^4 \Big) N \\
\frac{ \Big( \sum_{i=1}^N x_i^2 \Big)^2 }{ \Big( \sum_{i=1}^{N} x_i^4 \Big) } & \leq N
\end{align}
$$

The OLS variance is greater or equal to the GLS variance.


# 2 (4.8)
**(Compare with Example 4.10 (equicorrelation).) Consider the linear model $y = Xb + e$ where $e = u + Z 1$ (Z is a scalar random variable), where $Cov(u) = \sigma^2 I_N$, $Var(Z) = \tau^2$, and $Z$ and $u$ are uncorrelated. Find $V$ and derive conditions under which the OLS estimator of every estimable function is BLUE.**

$$
	\begin{align}
		Cov(e) & = Cov(U + Z 1_N) \\
			& = Cov(U) + Cov(Z 1_N) + 0 \\
			& = Cov(U) + Cov(1_N Z) \\
			& = \sigma^2 I + 1_N \tau^2 1_N^T \\
			& = \sigma^2 (I + \frac{ \tau^2}{ \sigma^2 } 1_N 1_N^T)
	\end{align}
$$

Take $V = (I + \frac{ \tau^2}{ \sigma^2 } 1_N 1_N^T)$. Also take $X = \begin{bmatrix} 1_N & X^* \end{bmatrix}$.

$$
	\begin{align}
		V X & = (I + \frac{ \tau^2}{ \sigma^2 } 1 1^T) \begin{bmatrix} 1 & X^* \end{bmatrix} \\
			& = \begin{bmatrix} 1_N + \frac{ N \tau^2 }{ \sigma^2 }1_N & X^* + \frac{ \tau^2 }{ \sigma^2 } 1_N 1_N^T X^* \end{bmatrix} \\ \\
		X Q & = \begin{bmatrix} 1_N & X^* \end{bmatrix} 
			\begin{bmatrix}
				Q_{11} & Q_{12} \\
				Q_{21} & Q_{22}
			\end{bmatrix} \\
			& = \begin{bmatrix} 1_N Q_{11} + X^* Q_{21} & 1_N Q_{12} + X^* Q_{22}\end{bmatrix}
	\end{align}
$$

Thus take 

$$
Q_{11} = 1 + \frac{ N \tau^2 }{ \sigma^2 }, \ Q_{21} = 0, \ Q_{12} = \tau^2 1_N^T X^*, \ Q_{22} = I_{p-1}.
$$


# 3 (4.9)
**If $X$ has full-column rank and $C^T y$ is also unbiased for estimable $\Lambda^T b$, show that $Cov(C^T y) - Cov(\Lambda^T \widehat b)$ is nonnegative definite.**

$$
	\begin{align}
		Cov(c^T y) & = Cov(c^T y - \Lambda^T \widehat \beta + \Lambda^T \widehat \beta) \\
			& = Cov(c^T y - \Lambda^T \widehat \beta) + Cov(\Lambda^T \widehat \beta) + 2 Cov(c^T y - \Lambda^T \widehat \beta, \Lambda^T \widehat \beta) \\
			& = Cov(c^T y - \Lambda^T \widehat \beta) + Cov(\Lambda^T \widehat \beta) + 0 & \text{result 4.1} \\
		Cov(c^T y) - Cov(\Lambda^T \widehat \beta) & = Cov(c^T y - \Lambda^T \widehat \beta) 
	\end{align}
$$

Since this is a covariance matrix, it must be nonnegative definite.

# 4 (4.12)
**Prove the Gauss-Markov Theorem directly, that is, by constructing all linear estimators $a^T y$ that are unbiased for $\lambda^T b$ (find a family of solutions $a(z)$), and then minimizing the variance $\sigma^2 a^T a$.**

We want to minimize $\sigma^2 a^T a$ which is the same as minimizing $\|\|a\|\|_2^2$.

$$
\begin{align}
||a||_2^2 & = ||\underbrace{(X^T)^g \lambda}_{\in C(X)} + \underbrace{(I-(X^T)^g X^t)z}_{\in N(X^T)}||_2^2 \ z \in \mathbb{R}^n \\
	& = ||(X^T)^g \lambda||_2^2 + ||(I-(X^T)^g X^t)z||_2^2 + 2 (X^T)^g \lambda (I-(X^T)^g X^t)z \\
	& = ||(X^T)^g \lambda||_2^2 + ||(I-(X^T)^g X^t)z||_2^2 + 0 \\
\end{align}
$$

Since these are in orthogonal spaces and both only add to the variance (since they are norms), we know that the minimum is at $z = 0$ where $a = (X^t)^g \lambda$.

$$
a^T y = \lambda^T (X^T X)^g X^T y = \lambda^T b
$$

# 5 (4.26)
**Ridge regression is a technique that has been recommended by some statisticians to address multicollinearity problems arising in multiple regression. In our usual linear models framework with $E(y) = X b$, and $Cov(y) = \sigma^2 I_N$, the ridge regression estimator takes the form**

$$
\widetilde b = (X^T X + k I_P)^{-1} X^T y
$$

**where $k>0$. Assume here that $X$ is full-column rank, that is, $\text{rank}( X ) = p$.**

## a
**Find $E(\widetilde b)$.**

$$
\begin{align}
E(\widetilde b) & = E \Big( (X^T X + k I_P)^{-1} X^T y \Big) \\
	& = (X^T X + k I_P)^{-1} X^T E(y) \\
	& = (X^T X + k I_P)^{-1} X^T X b \\
	& = \Big[ (X^T X)^{-1}(X^T X + k I_p) \Big]^{-1} b \\
	& = \Big[ I_p + k(X^T X)^{-1} \Big]^{-1} b
\end{align}
$$


## b
**Is $\lambda^T \widetilde b$ an unbiased estimator of $\lambda^T b$?**

$$
\begin{align}
E(\lambda^T \widetilde b) & = \lambda^T E(\widetilde b) \\
	& = \lambda^T (X^T X + k I_P)^{-1} X^T X b  \\
	& = a^T X (X^T X + k I_P)^{-1} X^T X b 
\end{align}
$$

## c
**Find $Cov(\widetilde b)$.**

$$
\begin{align}
Cov(\widetilde b) & = \Big[ (X^T X + k I_P)^{-1} X^T \Big] Cov(y) \Big[ (X^T X + k I_P)^{-1} X^T  \Big]^T \\
	& = \Big[ (X^T X + k I_P)^{-1} X^T  \Big] \sigma^2 I_n \Big[ (X^T X + k I_P)^{-1} X^T  \Big]^T \\
	& = \sigma^2 \Big[ (X^T X + k I_P)^{-1} X^T \Big] \Big[ (X^T X + k I_P)^{-1} X^T  \Big]^T
\end{align}
$$

## d
**Mean squared error is commonly used to assess the quality of an estimator. For the ridge regression estimator $\widetilde  b$, find the mean squared error**

$$
E\Big(||\widetilde b - b ||^2\Big) = E\Big( (\widetilde  b - b)^T(\widetilde b - b) \Big)
$$


$$
\begin{align}
E\Big(||\widetilde b - b ||^2\Big) & = E\Big( (\widetilde b - b)^T (\widetilde b - b) \Big) \\
	& = E\Big( (\widetilde b -E(\widetilde b) + E(\widetilde b) - b)^T (\widetilde b - E(\widetilde b) + E(\widetilde b) - b) \Big) \\
	& = E\Big( (\widetilde b - E(\widetilde b))^T (\widetilde b - E(\widetilde b)) + (\widetilde b -  E(\widetilde b))^T (E(\widetilde b) - b) + (E(\widetilde b) - b)^T(\widetilde b - E(\widetilde b)) + (E(\widetilde b) - b)^T (E(\widetilde b) - b) \Big) \\
	& = E\Big( (\widetilde b - E(\widetilde b))^T (\widetilde b - E(\widetilde b)) \Big) + 0 + 0 E\Big( (E(\widetilde b) - b)^T(E(\widetilde b)-b) \Big) \\
	& = tr(Cov(\widetilde b)) + || E(\widetilde b) - b ||_2^2
\end{align}
$$

## e
**Consider applying ridge regression to a multivariate regression problem with two centered covariates ($\sum x_i = \sum z_i = 0$), taking the form**


$$
Xb = 
\begin{bmatrix}
	1 & x_1 & z_1 \\
	1 & x_2 & z_2 \\
	\vdots & \vdots & \vdots \\
	1 & x_N & z_N
\end{bmatrix}
\begin{bmatrix}
	\beta_0 \\
	\beta_1 \\
	\beta_2
\end{bmatrix}
$$


**yielding the inner product matrix**


$$
X^T X = 
\begin{bmatrix}
	N & 0 & 0 \\
	0 & \sum x_i^2 & \sum x_i z_i \\
	0 & \sum x_i z_i & \sum z_i^2
\end{bmatrix}.
$$


**For simplicity, suppose $N = 10$, $\sum x_i^2 = \sum z_i^2 = 5$, and $\sum x_i z_i = 4$.**



**Find the covariance matrix of our usual least squares estimator $\widehat b = (X^T X)^{-1} X^T y$ in this situation.**


$$
\sigma^2 (X^T X)^{-1} = \left(
\begin{array}{ccc}
 \frac{\sigma ^2}{10} & 0 & 0 \\
 0 & \frac{5 \sigma ^2}{9} & -\frac{1}{9} \left(4 \sigma ^2\right) \\
 0 & -\frac{1}{9} \left(4 \sigma ^2\right) & \frac{5 \sigma ^2}{9} \\
\end{array}
\right)
$$


## f
**Find a value of $k$ such that one component of $\widetilde  b$ (your choice of component) has smaller variance than the corresponding least squares estimator.**

$$
\sigma^2 (X^T X + k I_P)^{-1} X^T X (X^T X + k I_P)^{-1} = \left(
\begin{array}{ccc}
 \frac{10 \sigma ^2}{(k+10)^2} & 0 & 0 \\
 0 & \frac{5 (k+5)^2 \sigma ^2}{(k+1)^2 (k+9)^2} & \frac{64 \sigma ^2}{(k+1)^2 (k+9)^2} \\
 0 & \frac{64 \sigma ^2}{(k+1)^2 (k+9)^2} & \frac{5 (k+5)^2 \sigma ^2}{(k+1)^2 (k+9)^2} \\
\end{array}
\right)
$$

Take $k = 5$ and then the first column will be smaller than in (e).

## g
**Part (f) looks like it violates the Gauss-Markov Theorem, Does it?**

This does not violate the Guass-Markov Theorem because $\widetilde b$ is not unbiased (so it cannot be BLUE).

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

**partitioning off the first $p$ columns of $U$, and express the least squares estimator as $\widehat b = V \Lambda^{-1} U_1^T y$.
Setting some of the small singular values to zero, and using**

$$
\Lambda_*^- = diag\{\lambda_1^{-1}, \dots , \lambda_k^{-1}, 0, \dots , 0\},
$$ 

**changing the rank from $p$ to $k$, leads to the estimator $\widetilde b = V \Lambda_*^- U_1^T y$. Find its bias and mean squared error.**

Notice

$$
\begin{align}
	\Lambda^{-1} & = \begin{bmatrix}
			1 / \lambda_1  \\
			& 1 / \lambda_2 \\
			& & \ddots \\
			& & & 1/ \lambda_p
		\end{bmatrix} \\
	\Lambda_*^- & = \begin{bmatrix}
			1/\lambda_1  \\
			& 1/\lambda_2 \\
			& & \ddots \\
			& & & 1/\lambda_k \\
			& & & & 0 \\
			& & & & & \ddots
		\end{bmatrix}
\end{align}
$$


$$
\begin{align}
E(\widetilde \beta) & = V \Lambda_*^- U_1^T U_1 \Lambda V^T \beta \\
	& = V \Lambda_*^- \Lambda V^T \beta \\
	& = V  
		\begin{bmatrix}
			1/\lambda_1  \\
			& 1/\lambda_2 \\
			& & \ddots \\
			& & & 1/\lambda_k \\
			& & & & 0 \\
			& & & & & \ddots
		\end{bmatrix}
		\begin{bmatrix}
			\lambda_1  \\
			& \lambda_2 \\
			& & \ddots \\
			& & & \lambda_p
		\end{bmatrix}
		V^T \beta \\
	& = V 
		\begin{bmatrix}
			1 \\
			& 1 \\
			& & \ddots \\
			& & & 1 \\
			& & & & 0 \\
			& & & & & \ddots
		\end{bmatrix}
		V^T \beta \\
	& = \begin{bmatrix} v_1 & \dots & v_k & 0 & \dots & 0\end{bmatrix} V^T \beta \\
	& = \begin{bmatrix} v_1 & \dots & v_k & 0 & \dots & 0\end{bmatrix}
		\begin{bmatrix}
				v_1^T \beta \\
				\vdots \\
				v_p^T \beta
			\end{bmatrix} \\
		& = \sum_{i=1}^k \langle v_i , \beta \rangle v_i
\end{align}
$$

This is the projection of $\beta$ onto the $k$-dimensional subspace.

So the bias is 

$$
Bias(\widetilde \beta) = \sum_{i=1}^k [\langle v_i , \beta \rangle v_i] - \beta.
$$

Also from 5 we know $MSE = tr(Cov(\widetilde b)) + \|\|E(\widetilde b - b)\|\|_2^2$.

$$
\begin{align}
E(\widetilde b - b) & = (V \Lambda_*^- U_1^T X - I)b \\
	& = (V \Lambda_*^- U_1^T U_1 \Lambda V^T - I) b \\
	& = (V \Lambda_*^- \Lambda V^T - I)b \\
	& = \Big( V \begin{bmatrix}	I & 0 \\ 0 & 0 \end{bmatrix} V^T - I\Big) b \\ \\
||E(\widetilde b - b)||_2^2 & = \Big[ b^T \Big( V \begin{bmatrix}
		I & 0 \\
		0 & 0 
	\end{bmatrix} V^T - I\Big) \Big] \Big[ \Big( V \begin{bmatrix}
		I & 0 \\
		0 & 0 
	\end{bmatrix} V^T - I\Big) b  \Big] \\
	& = b^T V \begin{bmatrix}	I & 0 \\ 0 & 0 \end{bmatrix}  v - 2 b^T V \begin{bmatrix}	I & 0 \\ 0 & 0 \end{bmatrix}  V^T b + b^T b \\
	& = b^T b - b^T V \begin{bmatrix}	I & 0 \\ 0 & 0 \end{bmatrix}  V^T b
\end{align}
$$



$$
\begin{align}
Var(V \Lambda_*^- U_1^T y)) & = V \Lambda_*^- U_1^T Var(y) U_1 (\Lambda_*^-)^T V^T \\ \\
MSE & = tr(V \Lambda_*^- U_1^T Var(y) U_1 (\Lambda_*^-)^T V^T) + b^T b - b^T V \begin{bmatrix}	I & 0 \\ 0 & 0 \end{bmatrix}  V^T b \\
	& = tr(Var(y) U_1 (\Lambda_*^-)^2 U_1^T) + b^T b - b^T V \begin{bmatrix}	I & 0 \\ 0 & 0 \end{bmatrix}  V^T b
\end{align}
$$
