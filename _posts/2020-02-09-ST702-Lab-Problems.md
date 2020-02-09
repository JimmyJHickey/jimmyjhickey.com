---
layout: post
comments: false
title: Lab Problems on Estimators
description: We're leading a lab about estimators. Wish us luck.
tags: ST702 Cramer-Rao
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}

# 7.41
**Let $X_1, \dots , X_n$ be an random sample from a population with mean $\mu$ and variance $\sigma^2$**

## a
**Show that the estimator $\sum_{i=1}^{n} a_i X_i$ an unbiased estimator of $\mu$ if $\sum_{i=1}^{n} = 1$.**

These $a_i$'s act as a weighted average. 

$$
E\Big( \sum a_i X_i \Big) = \sum  E\Big( a_i X_i \Big) = \sum a_i E(X_i) = \sum a_i \mu = \mu \sum a_i = \mu
$$

## b
**Among all unbiased estimators of this form (called _linear unbiased estimators_) find the one with miminum variance and calculate the variance.**

$$
V\Big( a_i X_i \Big) = \sum a_i^2 V(X_i) = \sum a_i^2 \sigma = \sigma \sum a_i^2
$$

We want to minimize this variance subject to $\sum a_i = 1$. Notice that the average of $\sum a_i$ is $\frac{ 1 }{ n }$. A trick we often use when dealing with sums is to add and subtract the mean.

$$
	\begin{align}
		\sum a_i^2 & = \sum (a_i + 1/n - 1/n)^2 \\
			& = \sum a_i^2 + \frac{ 1 }{ n^2 } + \frac{ 2 a_i }{ n } + \frac{ 1 }{ n^2 } - \frac{ 2 a_i}{ n } - \frac{ 2 }{ n^2 } \\
			& = \sum a_i^2 - \frac{ 1 }{ n }^2 + \frac{ 1 }{ n^2 } \\
			& = \sum (a_i - \frac{ 1 }{ n })^2 + \frac{ 1 }{ n^2 }
	\end{align}
$$

This is minimized when $a_i = \frac{ 1 }{ n }$. Then,

$$
	\begin{align}
		V\Big(\sum a_i X_i\Big) & = \sigma^2 \sum \frac{ 1 }{ n^2 } = \frac{ \sigma^2 }{ n } \\
		\sum a_i X_i & = \sum \frac{ 1 }{ n } X_i = \frac{ 1 }{ n } \sum X_i = \overline{ X }
	\end{align}
$$