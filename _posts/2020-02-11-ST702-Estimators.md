---
layout: post
comments: false
title: Example Problems on Estimators
description: ST702 Homework 4 on Estimators
tags: ST702 Cramer-Rao Estimators
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}

# 7.6
**Let $X_1, \dots X_n$, be a random sample from the pdf**

$$
f(x | \theta) = \theta x^{-2} , \ 0 < \theta \leq x < \infty.
$$


## a
**What is a sufficient statistic for $\theta$?**

$$
	\begin{align}
		f( \mathbf x | \theta ) & = \prod \frac{ \theta }{ x_i ^2} I( 0 < \theta \leq x < \infty) \\
			& = \frac{ \theta^n }{ \prod x_i^2 } I( \theta < x_{(1)})
	\end{align}
$$

By the factorization theorem, $X_{(1)}$ is sufficient.



## b
**Find the MLE of $\theta$.**

We calculated $L(\theta \| x)$ above. Notice that it increases with $\theta$, so we want to maximize $\theta$. The max value it can take is $X_{(1)}$, so take $\theta = X_{(1)}$



## c
**Find the method of moments estimator of $\theta$.**

First we need to find $E(X)$.

$$
E(X) - \int_{\theta}^{\infty} x \frac{ \theta }{ x^2 } dx = \theta \log(x) |^{\infty}_{\theta} = \theta (\log(\infty) - \log(\theta)) = \infty
$$

Since $E(X)$ does not exist/ is not finite, the method of moments estimator does not exist.


# 7.11
**Let $X_1, \dots , X_n$ be iid with pdf**

$$
f(x | \theta) = \theta x^{\theta -1} , \ 0 \leq x \leq 1, \ 0 < \theta < \infty
$$


## a
**Find the MLE of $\theta$, and show that its variance $\rightarrow 0$ and $n \rightarrow \infty$.**

Notice that $f \sim Beta(\theta, 1)$.


$$
	\begin{align}
		L(\theta | x) & = \prod \theta X_i^{\theta - 1} \\
			& = \theta^2 \prod\theta X_i^{\theta - 1} \\
		\ell (\theta |x ) & = n \log(\theta) + (\theta -1 ) \sum \log(x_i) \\
		\frac{ \partial \ell }{ \partial \theta }& = \frac{ n }{ \theta } + \sum \log(x_i) \\
			& = 0 \\
		\hat{\theta} & = \frac{ n }{ \sum - \log(x_i) } \\
		\frac{ \partial^2 \ell }{ \partial \theta^2 } & = \frac{ - n^2 }{ \theta^2 } < 0
	\end{align}
$$

Notice that the second derivative is negative, meaning that this is indeed a maximum. Now we will use our knowledge of distribution relationships, so buckle up.

Our original function was a Beta distribution. We are taking the negative log of it, which is a $Exp(\frac{ 1 }{ \theta })$. We are then summing iid exponentials which gives a $Gamma(n, \frac{ 1 }{ \theta }$. Finally, we are taking the reciprocal of this, which is an inverse gamma. So,  $\hat \theta \sim Inverse Gamma(n, \theta)$.

$$
V(\hat \theta) = V(n \cdot IG(n, \theta))=  n^2 \frac{ \theta^2 }{ (n-1)^2(n-2) }
$$

Notice that the denominator grows in $n^3$ and the numerator in $n^2$, so the variance goes to 0 as $ n \rightarrow \infty$.


## b
**Find the method of moments estimator of $\theta$.**


$$
	\begin{align}
		E(X) & = \frac{ \theta }{ \theta + 1 } \\
		\frac{ 1 }{ n } \sum  X_i & = \frac{ \theta }{ \theta + 1 } \\
		- \theta \frac{ 1 }{ n } \sum X_i - \frac{ 1 }{ n } \sum X_i - \theta & = 0 \\
		\theta(-\frac{ 1 }{ n } \sum x_i - 1) & = \frac{ 1 }{ n } \sum X_i \\
		\hat \theta & = \frac{ 1/n \sum X_i }{ -\frac{ 1 }{ x } \sum X_i - 1 }
	\end{align}

$$


# 1

**Suppose that a random variable $X$ has Poisson distribution for which the parameter $\lambda > 0$ is unknown. Find a statistic $\tau(X)$ that will be unbiased for $e^\lambda$. Hint: If $E\Big[ \tau(X) \Big] = e^\lambda$, then $\sum_{x=0}^{\infty} \frac{ \tau(x) e^{-\lambda} \lambda^x }{ x! } = e^\lambda$. Multiply both sides of this equation by $e^\lambda$; expand the right hand side in a power series of $\lambda$, and then equate the coefficients of $\lambda^x$ on both sides of the equation for $x=0, 1, \dots$.**


$$
	\begin{align}
		\sum_{x=0}^{\infty} \frac{ \tau(x) e^{-\lambda} \lambda^x }{ x! } & = e^\lambda \\
		e^\lambda \sum_{x=0}^{\infty} \frac{ \tau(x) e^{-\lambda} \lambda^x }{ x! } & = e^\lambda e^\lambda \\
		\sum_{x=0}^{\infty} \frac{ \tau(x) \lambda^x }{ x! } & = e^{2 \lambda} \\
		& = \frac{ (2 \lambda)^0 }{ 0! } + \frac{ (2 \lambda)^1 }{ 1! } + \frac{ (2 \lambda)^2 }{ 2! } + \frac{ (2 \lambda)^3 }{ 3! } + \dots \\
		& = 1 + \frac{ 2 \lambda }{ 1! } + \frac{ 2^2 \lambda^2 }{ 2! } + \frac{ 2^3 \lambda^3 }{ 3! } + \dots
	\end{align}
$$


So take $\tau(X) = 2^X$.

# 2
**Let $X_1, X_2, \dots X_n$ be a random sample from a distribution whose first two moments are finite. Let $\mu = E(X)$ and $\sigma^2 = V(X)$. Determine an unbiased estimator for $\mu^2$.**


Take $\tau(X) = \frac{ 1 }{ n } \sum_{i=1}^{n}(X_i^2) - S^2$. Then,

$$
	\begin{align}
		E\Big[ \frac{ 1 }{ n } \sum_{i=1}^{n}(X_i^2) - S^2 \Big] & = E\Big[ \frac{ 1 }{ n } \sum_{i=1}^{n}(X_i^2) \Big] - E(S^2) \\
			& = \frac{ 1 }{ n } E\Big[ \sum_{i=1}^{n}(X_i^2) \Big] - \sigma^2 \\
			& = \frac{ 1 }{ n } \sum_{i=1}^{n}\Big[ E(X_i^2) \Big] - \sigma^2 \\
			& = \frac{ 1 }{ n } \sum_{i=1}^{n} \Big[ E(X_i^2) \Big] - \sigma^2 \\
			& = \frac{ 1 }{ n } \sum_{i=1}^{n} \Big[ E(X_i)^2 + V(X_i) \Big] - \sigma^2 \\
			& = \frac{ 1 }{ n } \Big[ n \mu^2 + n \sigma^2 \Big] - \sigma^2 \\
			& = \mu^2.
	\end{align}
$$