---
layout: post
comments: false
title: Example Problems on Sufficient Statistics
description: ST705 Homework 1 on Sufficient Statistics
tags: ST702 Sufficient Ancillary Statistics
category: ST702
---


* Do not remove this line (it will not be displayed)
{:toc}

# 5.23
**Let $U_i$, $i= 1, 2, \dots$ be independent uniform(0,1) random variables, and let $X$ have the distribution**

$$
P(X = x) = \frac{ c }{ x! }, \ x = 1, 2, 3, \dots
$$

**where $c = 1/(e-1)$. Find the distribution of**

$$
Z = \min \{ U_1, \dots , U_X \}
$$


**(_Hint_: Note that the distribution of $Z\|X = x$ is that of the first-order statistic from the sample of size $x$.)**

$$
P(Z > z) = \sum_{x=1}^{\infty} P(Z > z | x) P(X = x)
$$

Notice that $P(Z > z \| x)$ is the CDF of the minimum order statistic.

$$
	\begin{align}
		P(Z > z) & = \sum_{x=1}^{\infty} P(Z > z | x) P(X = x) \\
			& = \sum_{x=1}^{\infty} \Big[1 - P_U(z) \Big]^x P(X = x)  \\
			& = \sum_{x=1}^{\infty} \Big[1 - \frac{ z-0 }{ 1-0 } \Big]^x \frac{ c }{ x! } \\
			& = c \sum_{x=1}^{\infty} \frac{ (1-z)^x }{ x! } \\
			& = c (e^{1-z} - 1) & \text{Taylor series} \\
			& = \frac{ e^{1-z}-1 }{ e-1 } & \text{for } z \in [0,1]
	\end{align}
$$


# 6.1
**Let $X$ be one observation from a $n(0, \sigma^2)$ population. Is $\| X \|$ a sufficient statistic?**

Notice that $X^2 = \| X \|^2$.

$$
	\begin{align}
		f(x | \sigma^2) & = \frac{ 1 }{ \sqrt{ 2 \pi \sigma^2} } e^{-(x-0)^2 / (2\sigma^2)} \\
			& = \underbrace{\frac{ 1 }{ \sqrt{ 2 \pi \sigma^2} } e^{-|x|^2 / (2\sigma^2)}}_{g(T(x) | \sigma^2)} \cdot \underbrace{1}_{h(x)} \\
	\end{align}
$$

Thus, $\|X\|$ is a sufficient statistic by the Factorization Theorem.

# 6.3
**Let $X_1, \dots, X_n$ be a random sample from the pdf**

$$
f(x|\mu, \sigma) = \frac{ 1 }{ \sigma } e^{-(x-\mu)/\sigma}, \mu < x < \infty,\ 0 < \sigma < \infty
$$

Since we have a random sample, our joint pdf is the product of the marginals.

$$
	\begin{align}
		f(\mathbf{x} | \mu, \sigma) & = \prod_{i = 1}^{n} f_X \\
			& = \prod_{ i = 1 }^{ n } \frac{ 1 }{ \sigma } e^{-(x_i - \mu) / \sigma} \mathbb{I}(\mu < x_i < \infty) \\
			& = \frac{ 1 }{ \sigma } e^{-\sum(x_i - \mu) / \sigma} \mathbb{I}(\mu < x_(1) < \infty)
	\end{align}
$$

Notice that the indicator function becomes only a function of the miminum order statistic. Thus, our sufficient statistic is $(\sum X_i, X_{(1)})$.

# 6.5
**Let $X_1, \dots , X_n$ be independent random variables with pdfs**

$$
f(x_i | \theta) = 
\begin{cases}
\frac{ 1 }{ 2i\theta } & -i(\theta - 1) < x_i < i(\theta + 1) \\
0 & \text{otherwise,}
\end{cases}
$$


**where $\theta > 0$. Find a two-dimensional sufficient statistic for $\theta$.**

Since we have an independent sample, our joint pdf is the product of the marginals.

$$
	\begin{align}
		f_{\mathbf{x}} & = \prod_{ i=1 }^{ n } f(x_i | \theta) \\
			& = \prod_{ i=1 }^{ n } \frac{ 1 }{ 2 i \theta } \mathbb{I}(-i (\theta - 1) < x_i < i (\theta + 1)) \\
			& = \Big( \frac{ 1 }{ 2 \theta }\Big)^2 \prod_{ i=1 }^{ n } \frac{ 1 }{ i } \mathbb{I}(-i (\theta - 1) < x_i) \mathbb{I}(x_i < i (\theta + 1) ) \\
			& = \Big( \frac{ 1 }{ 2 \theta }\Big)^2 \prod_{ i=1 }^{ n } \frac{ 1 }{ i } \mathbb{I}( - (\theta - 1) < x_i / i) \mathbb{I}(x_i / i < (\theta + 1) )
	\end{align} 
$$


Notice that the first indicator is only 1 if $-(\theta - 1) < \min(x_i / i)$ and the second indicator is only 1 if $\max(x_i / i) < \theta + 1$. So, our sufficient statistic is $(\min(x_i / i), \ \max(x_i / i))$.

# 6.13
**Suppose $X_1$ and $X_2$ are iid observations from the pdf $f(x \| \alpha) = \alpha x^{\alpha - 1} e^{-x^\alpha}$, $x > 0$, $\alpha > 0$. Show that $\log(X_1) / \log(X_2)$ is an ancillary statistic.**

Take $U = \log(X_1)$ and $V = \log(X_2)$. Then,

$$
	\begin{align}
		F_U(u) & = P( U \leq u) \\
			& = P( \log(X_1) \leq u ) \\
			& = P(X_1 \leq e^u)\\ \\
		f_U(u) & = f_x(e^U) e^U \\
			& = \alpha (e^u)^{\alpha - 1} e^{-(e^u)^\alpha} e^u \\
			& = \alpha e^{u \alpha} e^{-e^{u\alpha}} \\
			& = \alpha e^{u \alpha - e^{u \alpha}} & -\infty < u < \infty
	\end{align}
$$

Notice that $V$ follows the same form. In fact, these form a scale family with rate parameter $\frac{ 1 }{ \alpha }$. Take $U = A_1$ and $V = A_2$. In chapter 3, we learned that we can write $A_i = \frac{ 1 }{ \alpha } B_i$ where $B_1$ and $B_2$ are iid from the same scale family with the scale parameter set to 1. So, $B_i$ looks like

$$
f_{B_i}(b_i) = 1 \cdot e^{b_i \cdot 1 - e^{b_i \cdot 1}} = e^{b_i - e^{b_i}}.
$$


Notice that this does not depend on $\alpha$. Thus,

$$
\frac{ \log(X_1) }{ \log(X_2) } = \frac{ U }{ V } = \frac{ A_1 }{ A_2 } = \frac{ 1/\alpha \cdot B_1 }{ 1/\alpha \cdot B_2 }.
$$

This does not depend on $\alpha$, so $\frac{ \log(X_1) }{ \log(X_2) }$ is an ancillary statistic for $\alpha$.