---
layout: post
comments: false
title: Example Problems on Sufficient and Ancillary Statistics
description: ST705 Homework 1 on Sufficient and Ancillary Statistics
tags: ST702 Sufficient Ancillary Statistics
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}

# 6.9 (c  and e)
**For each of the following distributions let $X_1, \dots X_n$ be a random sample. Find a minimal sufficient statistic for $\theta$.**

## c
$$
	\begin{align}
		f(x | \theta) & = \frac{ e^{-(x-\theta)} }{ (1+e^{-(x-\theta)})^2 }, & -\infty < x< \infty, & -\infty < \theta < \infty, & \text{logistic}
	\end{align}
$$




## e
$$
	\begin{align}
		f(x | \theta) & = \frac{ 1 }{ 2 } e^{-|x-\theta}, & -\infty < x< \infty, & -\infty < \theta < \infty, & \text{double exponential}
	\end{align}
$$

# 6.12
**A natural ancillary statistic in most problems is the _sample size_. For example, let $N$ be a random variable taking values $1, 2, \dots$ with known probabilities $p_1, p_2, \dots$, where $\sum p_i = 1$. Having observed $N = n$, perform $n$ Bernoulli trials with success probability $\theta$, getting $X$ successes.**


## a
**Prove that the pair $(X, N)$ is minimal sufficient and $N$ is ancillary for $\theta$. (Note the similarity to some of the hierarchical models discussed in section 4.4).**




## b
**Prove that the estimator $X/N$ is unbiased for $\theta$ and has variance $\theta (1-\theta) E(1/N)$.**





# 6.19

**The random variable $X$ takes the values $0, 1, 2$ according to one of the following distributions:**

$$
\begin{array}{l c c c c}
	& P(X = 0) & P(X = 1) & P(X = 2) & \\ \hline
	\text{Distribution 1} & p & 3p & 1-4p & 0 < p < \frac{ 1 }{ 4 } \\
	\text{Distribution 2} & p & p^2 & 1 - p - p^2 & 0 < p < \frac{ 1 }{ 2 }
\end{array}
$$

**In each cast determine whether the familty of distributions of $X$ is complete.**

# 6.20
**For each of the following pdfs let $X_1, \dots X_n$ be iid observations. Find a complete sufficient statistic or show that one does not exist.**


## a
$$
	\begin{align}
		f(x | \theta) & = \frac{ 2x }{ \theta^2 }, & 0 < x < \theta, & & \theta > 0
	\end{align}
$$


## b
$$
	\begin{align}
		f(x | \theta) & = \frac{ \theta }{ (1+x)^{1+\theta}}, & 0 < x< \infty, & & \theta > 0
	\end{align}
$$


## c
$$
	\begin{align}
		f(x | \theta) & = \frac{ \log(\theta) \theta^x }{ \theta - 1 }, & 0 < x< 1, & & \theta > 1
	\end{align}
$$


## d
$$
	\begin{align}
		f(x | \theta) & = e^{-(x-\theta)} exp(-e^{-(x-\theta)}) & -\infty < x< \infty, & & -\infty \leq \theta \leq \infty
	\end{align}
$$


## e
$$
	\begin{align}
		f(x | \theta) & = {2 \choose x} \theta^x (1-\theta)^{2-x}, & x=0,1,2, & & 0 \leq \theta \leq 1
	\end{align}
$$


