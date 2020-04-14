---
layout: post
comments: false
title: Example Problems on Statistical Inference
description: ST705 Homework 11 on Statistical Inference
tags: ST705 Linear-Algebra Inference Statistics
category: ST705
published: true
---

* Do not remove this line (it will not be displayed)
{:toc}


# 6.1
**Prove Corollary 6.1.**

_Proof:_

Take $Y \sim N_n(X\beta, \sigma^2 I_n)$. Define $T_2(y) = (SSE, X^T y)$. Where $SSE = y^T y - y^T X (X^T X)^g X^T y$. Then,

$$
\begin{align}
f(y) & = (2 \pi \sigma^2)^{-n/2} \exp\Big(-\frac{ 1 }{ 2\sigma^2 } (y-X\beta)^T(y-X\beta)\Big) \\
	& = (2 \pi \sigma^2)^{-n/2} \exp\Big(-\frac{ 1 }{ \sigma^2 } y^T y + \frac{ 1 }{ \sigma^2 } y^T X \beta\Big) \exp\Big(-\frac{ 1 }{ 2 \sigma^2 }\beta^T X^T X \beta\Big) \\
	& = C(\beta, \sigma^2) \exp\Big(-\frac{ 1 }{ \sigma^2 } (y^T y - y^T X(X^T X)^g X^T y) - \frac{ 1 }{ \sigma^2 } y^T X(X^T X)^g X^T y + \frac{ 1 }{ \sigma^2 } (X^T y)^T \beta\Big) \\
	& = C(\beta, \sigma^2) \exp\Big(-\frac{ 1 }{ \sigma^2 } SSE - \frac{ 1 }{ \sigma^2 } (X^T y)^T(X^T X)^g X^T y + \frac{ 1 }{ \sigma^2 } (X^T y)^T \beta\Big).
\end{align}
$$


By the Factorization Theorem, $T_2(y)$ is sufficient. If we know $T_{2,2}$ then we know the second two terms in the exponential and if we know both $T_{2,1}$ and $T_{2,2}$ then we know the first term as well.


Recall that $T_1(y) = (y^T y, y^T X)$ is sufficient for $\beta, \sigma^2$. Also recall that our definition for a minimal sufficient statistic says that $T(y)$ is minimal sufficient if all other sufficient statistics can be written as a function of $T(y)$. We will write $T_{1,2}$ as a function of $X^T y$.

$$
T_{1,2}(y) = y^T X = (X^T y)^T = (T_{2,2}(y))^T = g_1(T_2(y)).
$$


Similarly,

$$
T_{1,1}(y) = y^T y = SSE + y^T X (X^T X)^g X^T y = T_{2,1} + T_{2,2}^T (X^T X)^g T_{2,2} = g_2(T_2(y)).
$$

Since our minimal sufficient statistic $T_1(y)$ can be written as a function of $T_2(y)$ and all sufficient statistics can be written as a function of $T_1(y)$, $T_2(y)$ must also be minimal sufficient.

<div style="text-align: right"> 🐙 </div>


# 6.2
**Show that the second derivative of the log-likelihood function under the normal Gauss-Markov model with respect to $\sigma^2$ is negative,**

$$
\log (L(b, \sigma^2)) = -(N/2) \log(2 \pi) - (N/2) \log(\sigma^2) - \frac{ 1 }{ 2 \sigma^2 } Q(b).
$$

$$
\begin{align}
\frac{ \partial  \ell }{\partial \sigma^2} & = -\frac{ n }{ 2 \sigma^2 } + \frac{ Q(b) }{ 2 (\sigma^2)^2 } \\
\frac{ \partial ^2  \ell}{\partial (\sigma^2)^2} & = \frac{ n }{ 2 (\sigma^2)^2 } - \frac{ Q(b) }{  (\sigma^2)^3 }
\end{align}
$$

We will evaluate the second derivative at $b = \widehat b, \widehat \sigma^2 = \frac{ Q(\widehat b) }{ n }$.

$$
\begin{align}
\frac{ \partial ^2  \ell}{\partial (\sigma^2)^2} \Big\vert_{b = \widehat b, \sigma^2 = \widehat \sigma^2} & = \frac{ n }{ 2 (Q(\widehat b)/n)^2 } - \frac{ Q(\widehat b) }{  (Q(\widehat b)/n)^3 } \\
	& = \frac{ n^3 }{ 2 Q(\widehat b)^2 } - \frac{ n^3 }{ Q(\widehat b)^2 } \\
	& = -\frac{ n^3 }{ 2 Q(\widehat b)^2 } \\
	& < 0.
\end{align}
$$


# 6.3
**In constructing maximum likelihood estimators in Result 6.3 and Corollary 6.3, does it matter whether $X$ is full-column rank or not?**

We can still construct maximum likelihood estimator of $X$ regardless of whether it is full column rank. However, the SSE may be larger as $I - P_X$ will have more in it.

# 6.4
**Recall that the usual unbiased estimator for the variance is $\widehat \sigma^2 = SSE / (N-r)$ where $SSE = y^T (I - P_X) y$ while the MLE is $SSE/N$. Find the estimator in the class $SSE/c$ (that is, find $c$) that minimizes mean square error, $E[(SSE/c - \sigma^2)^2]$.**


$$
\begin{align}
E[(SSE/c - \sigma^2)^2] & = E[\frac{ SSE^2 }{ c^2 } - 2 \frac{ SSE }{ c }\sigma^2 + (\sigma^2)^2] \\
	& = E[\frac{ SSE^2 }{ c^2 }] - E[2 \frac{ SSE }{ c }\sigma^2] + E[(\sigma^2)^2] \\
	& = \frac{ 1 }{ c^2 } E[SSE^2] - \frac{ 2 \sigma^2 }{ c } E[SSE] + (\sigma^2)^2 \\
	& = \frac{ 1 }{ c^2 } (2(n-r) + (n-r)^2) - \frac{ 2 \sigma^2 }{ c } (n-r) + (\sigma^2)^2 \\
\frac{ \partial  E[(SSE/c - \sigma^2)^2] }{\partial c} & = \frac{2 (n-r) \left(c \sigma ^2-n+r-2\right)}{c^3} \\
0 & = (2 (n - r) (-1 - n + r + c \[Sigma]^2))/c^3 \\
c & = \frac{ 1 + n - r }{ \sigma^2 } = \frac{ E(SSE^2) }{ \sigma^2 E(SSE) }
\end{align}
$$


# 6.7
**Recall Exercise 4.1, find the MLE of $p$ and compare it to the BLUE.**

Since the distributions are independent their joint distribution is the product of the marginals.

$$
\begin{align}
f(y_1, \dots , y_N) & = \prod_{i=1}^N {n \choose y_i} p^{y_i} (1-p)^{n_i - y_i} \\
	& = p^{\sum y_i} (1-p)^{\sum n_i - y_i} \prod {n \choose y_i} \\
\ell f &  = \sum (y_i) \log(p) + \sum (n_i - y_i) \log(1-p) + \sum \log( {n \choose y_i} ) \\ \\
\frac{ \partial  f }{\partial p} & = \frac{ \sum y_i }{ p } - \frac{ \sum n_i - y_i }{ 1 - p } \\
0 & = \frac{ \sum y_i }{ p } - \frac{ \sum n_i - y_i }{ 1 - p } \\
	& = \frac{ (1-p) \sum y_i - p (\sum n_i - \sum y_i) }{ p(1-p) } \\
	& = \frac{ \sum y_i - p \sum n_i }{ p(1-p) } \\
\widehat p & = \frac{ \sum y_i }{ \sum n_i  }
\end{align}
$$

This is the same as the BLUE.


# 6.10
**Consider again the two-way cross model with interaction, $y_{ijk} = \mu + \alpha_i + \beta_j + \gamma_{ij} + e_{ijk}$. Following Example 6.3, construct the design matrices for the full and reduced models for testing whether the interaction is zero, give their ranks, and thus establish the usual test statistic as a likelihood ratio test with its proper degrees of freedom. For simplicity, choose $a=3$, $n=2$, and $n_{ij} = 2$.**

Our hypotheses are $H_0 : \gamma_{ij} = 0 \text{ vs. } H_1: \gamma{ij} \neq 0$. Our model under the null hypothesis is

$$
y_{0,ijk} = \mu + \alpha_i + \beta_j + e_{ijk}.
$$

Under $H_0$, our design matrix looks like

$$
X_0 = 
\begin{bmatrix}
\text{intercept} & \alpha_1 & \alpha_2 & \alpha_3 & \beta_1 & \beta_2 \\ \hline
1 & 1 & 0 & 0 & 1 & 0 \\
1 & 1 & 0 & 0 & 1 & 0 \\
1 & 1 & 0 & 0 & 0 & 1 \\
1 & 1 & 0 & 0 & 0 & 1 \\
1 & 0 & 1 & 0 & 1 & 0 \\
1 & 0 & 1 & 0 & 1 & 0 \\
1 & 0 & 1 & 0 & 0 & 1 \\
1 & 0 & 1 & 0 & 0 & 1 \\
1 & 0 & 0 & 1 & 1 & 0 \\
1 & 0 & 0 & 1 & 1 & 0 \\
1 & 0 & 0 & 1 & 0 & 1 \\
1 & 0 & 0 & 1 & 0 & 1
\end{bmatrix}.
$$

This has rank 4.

Under $H_1$, our design matrix looks like,

$$
X = 
\begin{bmatrix}
\text{intercept} & \alpha_1 & \alpha_2 & \alpha_3 & \beta_1 & \beta_2 & \gamma_{11} & \gamma_{12} & \gamma_{21} & \gamma_{22} & \gamma_{31} & \gamma_{32} \\ \hline
1 & 1 & 0 & 0 & 1 & 0 &	1	&	0	&	0	&	0	&	0	& 	0	\\
1 & 1 & 0 & 0 & 1 & 0 &	1	&	0	&	0	&	0	&	0	& 	0	\\
1 & 1 & 0 & 0 & 0 & 1 &	0	&	1	&	0	&	0	&	0	& 	0	\\
1 & 1 & 0 & 0 & 0 & 1 &	0	&	1	&	0	&	0	&	0	& 	0	\\
1 & 0 & 1 & 0 & 1 & 0 &	0	&	0	&	1	&	0	&	0	& 	0	\\
1 & 0 & 1 & 0 & 1 & 0 &	0	&	0	&	1	&	0	&	0	& 	0	\\
1 & 0 & 1 & 0 & 0 & 1 &	0	&	0	&	0	&	1	&	0	& 	0	\\
1 & 0 & 1 & 0 & 0 & 1 &	0	&	0	&	0	&	1	&	0	& 	0	\\
1 & 0 & 0 & 1 & 1 & 0 &	0	&	0	&	0	&	0	&	1	& 	0	\\
1 & 0 & 0 & 1 & 1 & 0 &	0	&	0	&	0	&	0	&	1	& 	0	\\
1 & 0 & 0 & 1 & 0 & 1 &	0	&	0	&	0	&	0	&	0	& 	1	\\
1 & 0 & 0 & 1 & 0 & 1 &	0	&	0	&	0	&	0	&	0	& 	1
\end{bmatrix}.
$$


Thanks Qiang Heng for the rest!

Take

$$
\beta^T = \begin{bmatrix}
mu & \alpha_1 & \alpha_2 & \alpha_3 & \beta_1 & \beta_2 & \gamma_{11} & \gamma_{12} & \gamma_{21} & \gamma_{22} & \gamma_{31} & \gamma_{32} 
\end{bmatrix}
$$

To conduct an F-test, we need to a testable $K$ with rank $(a-1)(n-1)$ that does not involve the main effect parameters $\mu, \alpha_i, \beta_j$. It will look like $\gamma_{i_1 j_1} - \gamma_{i_1 j_2} - \gamma_{i_2 j_1} + \gamma_{i_2 j_2}$. See the discussion in Example 6.2. An example of of a testable $K$ is

$$
K^T = \begin{bmatrix}
	0 & 0 & 0 & 0 & 0 & 0 & 1 & -1 & -1 & 1 & 0 & 0 \\
	0 & 0 & 0 & 0 & 0 & 0 & 1 & -1 & 0 & 0 & -1 & 1 
\end{bmatrix}.
$$

This first row of $K^T$ corresponds to $\gamma_{11} - \gamma_{12} - \gamma_{21} + \gamma_{22}$ and the second row corresponds to $\gamma_{11} - \gamma_{12} - \gamma_{31} + \gamma_{32}$. Our usual test statistic looks like

$$
F_1 = \frac{ (K^T \widehat \beta - 0)^T H^{-1} (K^T \widehat \beta - 0) / s }{ SSE/(N-r) }.
$$

The likelihood ratio test discussed on page 138-139 is 

$$
F_2 = \frac{ y^T (P_X -P_{X_0}) y / s }{ y^T (I-P_X)y/(N-r) }.
$$

Here $s = (a-1)(n-1) = 2$ and $N-r = 12 - 2\cdot 3 = 6$. This are our degrees of freedom for the $F$ statistic. We can see that the denominators of these tests are the same, so we only need to check that the numerators are the same.

$$
\begin{align}
(K^T \widehat \beta - 0)^T H^{-1} (K^T \widehat \beta - 0) & = \widehat \beta K(K^T (X^T X)^g K)^{-1} K^T \widehat \beta \\
	& = y^T X((X^T X)^g)^T K (K^T (X^T X)^g)K)^{-1} K^T (X^T X)^g X^T y
\end{align}
$$

So we need to show

$$
P_X - P_{X_0} = X((X^T X)^g)^T K (K^T (X^T X)^g)K)^{-1} K^T (X^T X)^g X^T.
$$

We can show this computationally.

``` 
# Thank you Qiang!

library(MASS)

X = matrix(c(
 1 , 1 , 0 , 0 , 1 , 0 ,	1	,	0	,	0	,	0	,	0	, 	0,
 1 , 1 , 0 , 0 , 1 , 0 ,	1	,	0	,	0	,	0	,	0	, 	0,
 1 , 1 , 0 , 0 , 0 , 1 ,	0	,	1	,	0	,	0	,	0	, 	0,
 1 , 1 , 0 , 0 , 0 , 1 ,	0	,	1	,	0	,	0	,	0	, 	0,
 1 , 0 , 1 , 0 , 1 , 0 ,	0	,	0	,	1	,	0	,	0	, 	0,
 1 , 0 , 1 , 0 , 1 , 0 ,	0	,	0	,	1	,	0	,	0	, 	0,
 1 , 0 , 1 , 0 , 0 , 1 ,	0	,	0	,	0	,	1	,	0	, 	0,
 1 , 0 , 1 , 0 , 0 , 1 ,	0	,	0	,	0	,	1	,	0	, 	0,
 1 , 0 , 0 , 1 , 1 , 0 ,	0	,	0	,	0	,	0	,	1	, 	0,
 1 , 0 , 0 , 1 , 1 , 0 ,	0	,	0	,	0	,	0	,	1	, 	0,
 1 , 0 , 0 , 1 , 0 , 1 ,	0	,	0	,	0	,	0	,	0	, 	1,
 1 , 0 , 0 , 1 , 0 , 1 ,	0	,	0	,	0	,	0	,	0	, 	1
), byrow=T, ncol=1+3+2+6)

X0 = X[,1:6]

K = matrix(c(
 0 , 0 , 0 , 0 , 0 , 0 , 1 , -1 , -1 , 1 , 0 , 0 ,
 0 , 0 , 0 , 0 , 0 , 0 , 1 , -1 , 0 , 0 , -1 , 1 
), ncol = 2)

PX = X %*% ginv(t(X) %*% X) %*% t(X)
PX0 = X0 %*% ginv(t(X0) %*% X0) %*% t(X0)

quadratic_form1 = PX - PX0

quadratic_form2 = X %*% t(ginv( t(X) %*% X)) %*% K %*% solve(t(K) %*% ginv(t(X) %*% X) %*% K) %*% t(K) %*% ginv(t(X) %*% X) %*% t(X)

mean(abs(quadratic_form1 - quadratic_form2))
# [1] 1.179612e-16
```

Thus, these two quadratic-form matrices are identical.