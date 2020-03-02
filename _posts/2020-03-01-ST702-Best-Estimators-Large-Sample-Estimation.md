---
layout: post
comments: false
title: Example Problems on Best Estimators and Large Sample Estimation
description: ST702 Homework 6 on Best Estimators and Large Sample Estimation
tags: ST702 Large-Sample Estimators
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}



# 7.55
**For each of the following pdfs, let $X_1, \dots , X_n$ be a sample from that distribution. In each case, find the best estimator of $\theta^r$. (See Guenther 1978 for a complete discussion of this problem.)**


## a
$$
f(x | \theta) = \frac{ 1 }{ \theta } ,\ 0 < x < \theta, \ r < n
$$



## b
$$
f(x | \theta) = e^{-(x-\theta)}, \ x > \theta
$$




## c
$$
f(x | \theta) = \frac{ e^{-x} }{ e^{-\theta} - e^{-b} }, \ \theta < x < b, \ b \text{ known}
$$





# 7.58
**Let $X$ be an observation from the pdf**


$$
f(x|\theta) = \Big( \frac{ \theta }{ 2 } \Big)^{|x|} (1-\theta)^{1-|x|}, \ x = -1, 0, 1, \ 0 \leq \theta \leq 1
$$


## a
**Find the MLE of $\theta$.**




## b
**Define the estimator $T(X)$ by**

$$
T(X) = \begin{cases}
		2 & \text{if } x=1\\
		0 & \text{otherwise.}
	\end{cases}
$$

**Show that $T(X)$ is an unbiased estimator of $\theta$.**



## c
**Find a better estimator of $T(X)$ and prove that it is better.**



# 7.60
**Let $X_1, \dots , X_n$ be iid $gamma(\alpha, \beta)$ with $\alpha$ known. Find the best unbiased estimator of $\frac{ 1 }{ \beta }$.**






# 10.1
**A random sample $X_1, \dots , X_n$ is drawn from a population with pdf**

$$
f(x|\theta) = \frac{ 1 }{ 2 }(1 + \theta x), \ -1 < x< 1, \ -1< \theta < 1.
$$

**Find a consistent estimator of $\theta$ and show that it is consistent.**





# 10.3
**A random sample $X_1 , \dots , X_n$ is drawn from a population that is $n(\theta, \theta)$, where $\theta > 0$.**


## a
**Show that the MLE of $\theta$, $\widehat \theta$, is a root of the quadratic equation $\theta^2 + \theta - W = 0$ where $W = (1/n)\sum_{i=1}^{n}X_i^2$, and determine which root equals the MLE.**




## b
**Find the approximate variance of $\widehat \theta$ using the techniques of Section 10.1.13.**