---
layout: post
comments: false
title: Example Problems on Sufficient and Ancillary Statistics
description: ST702 Homework 2 on Sufficient and Ancillary Statistics
tags: ST702 Sufficient Ancillary Statistics
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}

# 7.8
**One observation, $X$, is taken from a $n(0, \sigma^2)$ population.**


## a
**Find an unbiased estimator of $\sigma^2$.**



## b
**Find the MLE of $\sigma$.**




## c
**Discus how the method of moments estimator of $\sigma$ might be found.**





# 7.9
**Let $X_1, \dots , X_n$ be iid with pdf**

$$
f(x | \theta) = \frac{ 1 }{ \theta }, \ 0 \leq x \leq \theta, \ \theta > 0.
$$


**Estimate $\theta$ using both method of moments and maximum likelihood. Calculate the means and variances of the two estimators. Which should be preferred and why?**



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



## b
**Find the MLEs of $\alpha$ and $\beta$.**



## c
**The length (in millimeters) of cuckoos' eggs found in hedge sparrow nests can be modeled with the distribution. For the data**

$$
22.0, 23.9, 20.9, 23.8, 25.0, 24.0, 21.7, 23.8, 22.8, 23.1, 23.1, 23.5, 23.0, 23.0,
$$

**find the MLEs of $\alpha$ and $\beta$.**


# 7.19
**Suppose that the random variables $Y_1, \dots , Y_n$ satisfy**

$$
Y_i = \beta X_i + \varepsilon, \ i = 1, \dots , n
$$


**where $x_1, \dots , x_n$ are fixed constants and $\varepsilon_1 , \dots , \varepsilon_n$ are iid $n(0, \sigma^2)$, $\sigma^2$ unknown.**

## a
**Find the two dimensional sufficient statistic for $(\beta, \sigma^2)$.**



## b
**Find the MLE of $\beta$, and show that it is an unbiased estimator of $\beta$.**



## c
**Find the distribution of the MLE of $\beta$.**





# 7.20
**Consider $Y_1, \dots , Y_n$ as defined in Exercise 7.19.**

## a
**Show that $\sum Y_i / \sum x_i$ is an unbiased estimator of $\beta$.**


## b
**Calculate the exact variance of $\sigma Y_i / \sigma x_i$ and compare it to the variance of the MLE.**