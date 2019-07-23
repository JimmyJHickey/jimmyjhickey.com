---
layout: post
comments: false
title: Example Problems on Limit Theorems
description: ST501 Homework 7 on Limit Theorems
tags: ST501 Random-Variables Limit Theorems Distribution Probability Examples Statistics
---

Problems: 5.2, 5.5, 5.6, 5.19, 5.28, Extra Problem 1


* Do not remove this line (it will not be displayed)
{:toc}

# 5.2
**Let $X_i$ be as in Problem 1 but with $E(X_i) = \mu_i$ and $n^{-1}\sum_{i=1}^{n}\mu_i \rightarrow \mu$. Show that $\bar X \rightarrow \mu$ in probability.**

Since these distributions have different means, we cannot apply the Law of Large Numbers. Thus, we will start this the definition of convergence in probability.

$$
	\begin{align}
		\lim_{n\rightarrow \infty}
	\end{align}
$$

# 5.5
**Using moment-generating functions, show that as $n\rightarrow \infty, \ p \rightarrow 0$, and $np\rightarrow \lambda$, the binomial distribution with parameters $n$ and $p$ tends to the Poission distribution.**

# 5.6
**Using moment-generating functions, show that as $\alpha \rightarrow \infty$ the gamma distribution with parameters $\alpha$ and $\lambda$, properly standardized, tends to the standard normal distributions**

# 5.19

## a.
**Use the Monte Carlo method with $n = 100$ and $n = 1000$ to estimate $\int_0^1 \cos(2\pi x)dx$. Compare the estimates to the exact answer.**

See R Code.

## b.

**Use Monte Carlo to evaluate $\int_0^1 \cos(2\pi x^2)dx$. Can you find the exact answer?**

See R Code.


# 5.28
**Let $f_n$ be a sequence of frequency functions with $f_n(x) = \frac{ 1 }{ 2 }$ if $x = \pm \Big( \frac{ 1 }{2} \Big)^n$ and $f_n(x) = 0$ otherwise. Show that $\lim f_n(x) = 0$ for all $x$ which means that the frequency functions do not converge to a frequency function, but there exists a CDF $F$ such that $\lim F_n(x) = F(x)$.**

# Extra Problem 1

**Suppose $X_i$ are independent random variables and that $E(X_i)-\mu, \ Var(X_i) = \sigma^2$.**

## a.
**What is the mean of $(\bar X)^2$?**

## b.
**Prove that $(\bar X)^2$ converges in probability to a constant and give that constant. State any theorems or results you use in your proof.**
