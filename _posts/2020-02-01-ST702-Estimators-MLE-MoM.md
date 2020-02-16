---
layout: post
comments: false
title: Example Problems on Estimators
description: ST702 Homework 3 on Estimators
tags: ST702 Sufficient Estimators
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}

# 7.8
**One observation, $X$, is taken from a $n(0, \sigma^2)$ population.**


## a
**Find an unbiased estimator of $\sigma^2$.**

Notice that we can't use the sample variance here because we only have one observation (and thus would be dividing by 0). Instead we will use $X^2$.

$$
E(X^2) = V(X) + E(X)^2 = \sigma^2 + \mu ^2 = \sigma^2 + 0 = \sigma^2
$$


## b
**Find the MLE of $\sigma$.**

$$
	\begin{align}
		L ( \sigma | \mathbf x) & = \prod_{i=1}^1 f(x_i | \sigma) \\
			& = \frac{ 1 }{ \sqrt{ 2 \pi \sigma^2 } } \exp(\frac{ -x^2 }{ 2 \sigma^2 }) \\
		l( \sigma | x) & = -\frac{ 1 }{ 2 } \log(2 \pi \sigma^2) - \frac{ x^2 }{ 2 \sigma ^2 } \\ \\
		\frac{ \partial l }{ \partial \sigma } & = \frac{ -1 }{ \sigma} + \frac{ x^2 }{ \sigma^3 } \\
			0 & = \frac{ -1 }{ \sigma} + \frac{ x^2 }{ \sigma^3 } \\
			\frac{ 1 }{ \sigma } & = \frac{ x^2 }{ \sigma^3 } \\
			\sigma^2 & = x^2 \\
			\sigma & = | x |
	\end{align}
$$

Notice that

$$
\frac{ \partial ^2 l }{ \partial \sigma^2 } = \frac{ 2 }{ \sigma^2 } - \frac{ 3 x^2 }{ \sigma^4 }
$$

is decreasing at $\sigma = \|x\|$, so we found a maximum.


## c
**Discuss how the method of moments estimator of $\sigma$ might be found.**

$$
	\begin{align}
		E(X) & = 0 \\
		E(X^2) & = \sigma^2 \\
		x^2 & = \sigma^2 \\
		\sigma & = | x |
	\end{align}
$$



# 7.9
**Let $X_1, \dots , X_n$ be iid with pdf**

$$
f(x | \theta) = \frac{ 1 }{ \theta }, \ 0 \leq x \leq \theta, \ \theta > 0.
$$


**Estimate $\theta$ using both method of moments and maximum likelihood. Calculate the means and variances of the two estimators. Which should be preferred and why?**

_Method of Moments_

$$
	\begin{align}
		E(X) & = \frac{ 1 }{ 2 } (\theta - 0) \\
			& = \frac{ \theta }{ 2 } \\
		\hat{\theta} & = 2 \overline{ X } \\ \\
		E(\hat{\theta}) & = E(2 \overline{ X }) \\
			& = 2 E( \frac{ 1 }{ n } \sum X_i)\\
			& = \frac{ 2 }{ n }(\frac{ 1 }{ 2 } \theta)^n \\
			& = \theta \\ \\
		V(\hat{\theta}) & = V(2 \overline{ X }) \\
			& = 4 V(\frac{ 1 }{ n }\sum X_i) \\
			& = \frac{ 4 }{ n^2 }(n \frac{ 1 }{ 12 } \theta ^2) \\
			& = \frac{ \theta^2 }{ 3n }
	\end{align}
$$


_Maximum Likelihood_

$$
	\begin{align}
		L(\theta | \mathbf X) & = \prod \frac{ 1 }{ \theta } I(0 \leq x \leq \theta) \\
			&= \frac{ 1 }{ \theta^n } I(0 \leq x_{(1)}) I(x_{(n)} \leq \theta)
	\end{align}
$$

Notice that this function decreases in $\theta$ and is maximized at $X_{(n)} = \theta$ (as is it zero for $\theta > X_{(n)}$). Recall the PDF of a maximum order statistic.

$$
f_{X_{(n)}}(x) = n f(x) F(x)^{n-1} = n \frac{ 1 }{ \theta } \Big( \frac{ x }{ \theta } \Big)^{n-1} = \frac{ n x^{n-1} }{ \theta^2 } I(0 \leq x \leq \theta)
$$



$$
	\begin{align}
		E(\hat{\theta}) & = \frac{ n }{ \theta^n } \int_{0}^{\theta} x \cdot x^{n-1} dx \\
			&= \frac{ n }{ \theta^n } \frac{ \theta^{n+1} }{ n+1 } \\
			& =\frac{ n \theta }{ n+1 } \\ \\
		E(\hat{\theta}^2) & = \frac{ n }{ \theta^n } \int_{0}^{\theta} x^2 \cdot x^{n-1} dx \\
			&= \frac{ n }{ \theta^n } \frac{ \theta^{n+2} }{ n+2 } \\
			& =\frac{ n \theta^2}{ n+1 } \\ \\
		V(\hat{\theta}) & = \frac{ n \theta^2}{ n+1 } - \frac{ n^2 \theta^2 }{ (n+1)^2 } \\
			& = \frac{ n \theta^2 }{ (n+1)^2(n+2) }
	\end{align}
$$


If we look at the variances, we notice that the MoM decreases at a rate of $\frac{ 1 }{ n }$ while the MLE decreases at a rate of $\frac{ 1 }{ n^2 }$. So, for large $n$ the MLE will offer a better estimate.

# 7.10
**The independent random vaiables $X_1 , \dots , X_n$ have the common distribution**


$$
P(X_i \leq x | \alpha, \beta) = 
\begin{cases}
	0 & \text{if } x < 0 \\
	(x/\beta)^\alpha & \text{if } 0 \leq x \leq \beta \\
	1 & \text{if } x > \beta,
\end{cases}
$$

where the parameters $\alpha$ and $\beta$ are positive.

## a
**Find the two-dimensional sufficient statistic for $(\alpha, \beta)$.**

First we must differentiate the CDF to find the PDF.

$$
f( x | \alpha, \beta) = 
\begin{cases}
	0 & \text{if } x < 0 \\
	\frac{ \alpha x^{\alpha - 1} }{ \beta^\alpha } & \text{if } 0 \leq x \leq \beta \\
	0 & \text{if } x > \beta,
\end{cases}
$$


Then we can proceed by the factorization theorem.

$$
	\begin{align}
		f(\mathbb x | \alpha, \beta) & = \prod_{i=1}^n \frac{ \alpha x_i^{\alpha-1} }{ \beta^\alpha } I(0 \leq x \leq \beta) \\
			& = \frac{ \alpha^n }{ \beta^{\alpha n} } \prod(x_i^{\alpha - 1}) I(0 \leq x_{(1)}) I(x_{(n)} \leq \beta) \\
			& = \frac{ \alpha^n }{ \beta^{\alpha n} } I(0 \leq x_{(1)}) \prod(x_i)^{\alpha - 1}  I(x_{(n)} \leq \beta) \\
	\end{align}
$$


Thus our 2D sufficient statistic is $(\prod x_i, x_{(n)})$.


## b
**Find the MLEs of $\alpha$ and $\beta$.**


$MLE_\alpha$

$$
	\begin{align}
		L(\alpha | x , \beta) & = \prod \frac{ \alpha }{ \beta^\alpha } x_i^{\alpha -1} \\
			& = \frac{ \alpha^n }{ \beta^{\alpha n} } \prod x_i^{\alpha -1} \\ \\
		l(\alpha | x , \beta) & = \log \Big( \beta^{\alpha n}  \prod x_i^{\alpha -1}  \Big) \\
			& = n \log(\alpha) + \alpha n \log(\beta) + (\alpha -1) \sum (\log(x_i)) \\ \\
		\frac{ \partial l }{ \partial \alpha } & = \frac{ n }{ \alpha } + n \log(\beta) + \sum (\log(x_i)) \\ \\
		0 & = \frac{ n }{ \alpha } + n \log(\beta) + \sum (\log(x_i)) \\
		\hat{\alpha} & = \frac{ n }{ n \log(\beta) -  \sum (\log(x_i))}
	\end{align}
$$

Notice that 

$$
\frac{ \partial^2 l }{ \partial \alpha^2 } = \frac{ -n }{ \alpha^2 }
$$

is negative, so this likelihood is a maximum.



$MLE_\beta$

$$
	\begin{align}
		L(\beta | x , \alpha) & = \prod \frac{ \alpha }{ \beta^\alpha } x_i^{\alpha -1} \\
			& = \frac{ \alpha^n }{ \beta^{\alpha n} } \prod x_i^{\alpha -1} I(0 \leq x_{(1)}) I(x_{(n)} \leq \beta)
	\end{align}
$$

Notice that this decreases with $\beta$ as is zero if $\beta >x_{(n)} $, so it achieves its maximum at $x_{(n)}$.

## c
**The length (in millimeters) of cuckoos' eggs found in hedge sparrow nests can be modeled with the distribution. For the data**

$$
22.0, 23.9, 20.9, 23.8, 25.0, 24.0, 21.7, 23.8, 22.8, 23.1, 23.1, 23.5, 23.0, 23.0,
$$

**find the MLEs of $\alpha$ and $\beta$.**

Since the MLE of $\beta$ is the max, it is $25$ for this data.


$$
MLE_\alpha = \frac{14}{14 \log (25)-\log (22*23.9*20.9*23.8*25*24*21.7*23.8*22.8*23.1*23.1*23.5*23.0*23.0)} = 12.5949
$$

# 7.19
**Suppose that the random variables $Y_1, \dots , Y_n$ satisfy**

$$
Y_i = \beta X_i + \varepsilon, \ i = 1, \dots , n
$$


**where $x_1, \dots , x_n$ are fixed constants and $\varepsilon_1 , \dots , \varepsilon_n$ are iid $n(0, \sigma^2)$, $\sigma^2$ unknown.**

## a
**Find the two dimensional sufficient statistic for $(\beta, \sigma^2)$.**

Notice 

$$
\varepsilon_i = \underbrace{\beta x_i - Y_i}_{N(0, \sigma^2)}.
$$


We will proceed by the factorization theorem.


$$
	\begin{align}
		\prod \varepsilon_i & = \prod_{i=1}^n \frac{1}{\sqrt{2 \pi \sigma}} e^{-\frac{1}{2 \sigma^2}(\beta x_i - y_i)^2} \\
			& = \frac{1}{(2 \pi \sigma)^{n/2}} e^{-\frac{1}{2 \sigma^2}\sum (\beta x_i - y_i)^2} \\
			& = \frac{1}{(2 \pi \sigma)^{n/2}} e^{\frac{ -\beta \sum x_i^2 }{ 2 \sigma^2 } - \frac{ \sum y_i^2 }{ 2 \sigma^2 } + \frac{ 2 \beta \sum x_i y_i }{ 2 \sigma^2 }}
	\end{align}
$$

Thus a sufficient statistic is $(\sum y_i^2, \sum x_i y_i)$.


## b
**Find the MLE of $\beta$, and show that it is an unbiased estimator of $\beta$.**

$$
	\begin{align}
		L(\beta | y) & = \prod_{i=1}^n \frac{1}{\sqrt{2 \pi \sigma}} e^{-\frac{1}{2 \sigma^2}(\beta x_i - y_i)^2} \\
			& = \frac{1}{(2 \pi \sigma)^{n/2}} e^{-\frac{1}{2 \sigma^2}\sum (\beta x_i - y_i)^2} \\ \\
		l( \beta | y ) & = \frac{ -n }{ 2 } \log(2 \pi \sigma^2) - \frac{ -\beta \sum x_i^2 }{ 2 \sigma^2 } - \frac{ \sum y_i^2 }{ 2 \sigma^2 } + \frac{ 2 \beta \sum x_i y_i }{ 2 \sigma^2 } \\ \\
		\frac{ \partial l  }{ \partial \beta } & = 0 -0 -0 - \frac{ 1 }{ \sigma^2 } \sum x_i y_i - \frac{ \beta }{ \sigma^2 } \sum x_i^2 \\ \\
		0 & = - \frac{ 1 }{ \sigma^2 } \sum x_i y_i - \frac{ \beta }{ \sigma^2 } \sum x_i^2 \\
		\hat \beta & = \frac{ \sum x_i y_i }{ \sum x_i ^2}
	\end{align}
$$


$$
	\begin{align}
		E(\hat \beta) & = E\Big( \frac{ \sum x_i y_i }{ \sum x_i } \Big) \\
			& = \frac{ \sum x_i E(y_i) }{ \sum x_i^2 } \\
			& = \frac{ \sum x_i \cdot x_i \beta }{ \sum x_i^2 } \\
			& = \beta
	\end{align}
$$

## c
**Find the distribution of the MLE of $\beta$.**

We now know that $Y_i \sim N(\beta x_i, \sigma^2)$, so we know that $\sum c_i Y_i \sim N(\sum c_i \mu_i, \sum c_i^2 \sigma_i^2)$. So,

$$
	\begin{align}
		\hat \beta & \sim N\Big(\frac{ \sum x_i \cdot x_i \beta }{ \sum x_i^2 }, \frac{ \sum x_i^2 }{ \sum x_i^4)} \sigma^2\Big) \\
			& \sim N( \beta, \frac{ \sigma^2 }{ \sum x_i^2 })
	\end{align}
$$


# 7.20
**Consider $Y_1, \dots , Y_n$ as defined in Exercise 7.19.**

## a
**Show that $\sum Y_i / \sum x_i$ is an unbiased estimator of $\beta$.**

$$
E\Big( \frac{ \sum Y_i }{ x_i } \Big) = \frac{ \sum E(Y_i) }{ \sum x_i } = \frac{ \sum x_i \cdot \beta}{ \sum x_i } = \beta
$$


## b
**Calculate the exact variance of $\sum Y_i / \sum x_i$ and compare it to the variance of the MLE.**

$$
Var \Big(  \frac{ \sum Y_i }{ x_i } \Big) = \frac{ 1 }{ (\sum x_i)^2 } \sum V(Y_i) = \frac{ \sum \sigma_i^2 }{ (\sum x_i)^2} = \frac{ n \sigma^2 }{ n^2 \overline{ x}^2 } = \frac{ \sigma^2 }{ n \overline{ x }^2 }
$$

Since the numerators of the variances are the same, we can just look at the denominators. Notice that

$$
\sum x_i^2 - n \overline{ x }^2 = \sum x_i^2 - (\sum x_i)^2 = \sum (x_i - \overline{ x })^2 \geq 0.
$$

Thus, $\sum x_i^2 \geq n \overline{ x }^2$, or $V(\hat \beta) \leq Var \Big(  \frac{ \sum Y_i }{ x_i } \Big)$.