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

# 7.45
**Let $X_1, X_2, \dots X_n$ be iid from a distribution with mean $\mu$ and variance $\sigma^2$, and let $S^2$ be the usual unbiased estimator of $\sigma^2$. In Example 7.3.4 we saw that, under normality, the MLE has smaller MSE than $S^2$. In this exercise we will explore variance estimators some more.**

# a
**Show that, for any estimator of the form $aS^2$, where $a$ is some constant,**

$$
MSE(aS^2) = E[aS^2 - \sigma^2]^2 = a^2 Var(S^2) + (a - 1)^2 \sigma^4
$$


## b
**Show that**

$$
Var(S^2) = \frac{ 1 }{ n } \Big( \kappa - \frac{ n-3 }{ n-1 } \sigma^4 \Big)
$$

**where $\kappa = E[X-\mu]^4$ is the _kurtosis_.**



## c
**Show that under normality, the kurtosis is $3 \sigma^4$ and establish that, in this case, the estimator of the form $aS^2$ with the minimum MSE is $\frac{ n-1 }{ n+1 }S^2$. (Lemma 3.6.5 may be helpful)**




## d 
**If normality is not assumed, show that $MSE(aS^2)$ is minimized at**

$$
a = \frac{ n-1 }{ n+1 + \frac{ (\kappa - 1) (n-1) }{ n } }
$$

**which is useless as is depends on a parameter.**




## e
**Show that**


### i
**for distributions with $\kappa > 3$, the optimial $a$ will satify $a < \frac{ n-1 }{ n+1 }$.**



## ii
**for distributions with $\kappa < 3$, the optimal $a$ will satify $\frac{ n-1 }{ n+1 } < a < 1$.**




# 7.48
**Suppose that $X_i, \ i = 1, \dots , n$ are iid $Bernoulli(p)$.**

## a
**Show that the variance of the MLE of $p$ attains the Cramér-Rao Lower Bound.**




## b
**For $n \geq 4$, show that the product $X_1 X_2 X_3 X_4$ is an unbiased estimator of $p^4$. and use this fact to find the best unbiased estimator of $p^4$.**




# 7.49
**Let $X_1, \dots , X_n$ be iid $exponential(\lambda)$.**

## a
**Find an unbiased estimator of $\lambda$ based only on $Y = \min \{X_1, \dots , X_n \}$.**




## b
**Find a better estimator than the one in part (a). Prove that it is better.**




## c
**The following data are high-stress failure times (in hours) of Kevlar/epoxy spherical vessels used in a sustained pressure environment on the space shuttle:**

$$
50.1, 70.1, 137.0, 166.9, 170.5, 152.8, 80.5, 123.5, 112.6, 148.5, 160.0, 125.4.
$$

**Failure times are often modeled with the exponential distribution. Estimate the mean failure time using the estimators from parts (a) and (b).**





# 4
**Consider a random sample $X_1, X_2, \dots X_n$ from the density $f(x\| \theta) = \exp\Big[ -(x-\theta) \Big]$, $\theta < x < \infty$, and 0 elsewhere. Show that the first order statistic $X_{(1)} = \min X_i$ is a complete sufficient statistic for $\theta$, and find the UMVUE of $\theta$.**
