---
layout: post
comments: false
title: Example Problems on Asymptotic Variance
description: ST793 Homework 3 on Asymptotic Variance
tags: ST793 Likelihoods Statistics
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

2.34 , 2.35, 2.42, 2.44, 2.47  

# 2.34
**Continuation of problem 2.2 p107.**

## a
**Find an estimate of the asymptotic covariance of $\widehat \mu, \widehat \sigma$. Here it helps to know that the Fisher information matrix has elements $I(\mu, \sigma)_{11} =1 / \sigma^2, \ I(\mu, \sigma)_{12} = -0.423 / \sigma^2, \ I(\mu, \sigma)_{22} = 1.824/\sigma^2$.**



## b
**Estimate the median of the distribution of the largest flow rate in 100 years.**

$$
\widehat Q = \widehat \sigma [-\log(-\log(0.993))] + \widehat \mu.
$$




## c.
**Find an estimate of the variance of $\widehat Q$**



# 2.35
**Derive the Fisher information matrix $I(\theta)$ for the reparameterized ZIP model**

$$
\begin{align}
P(Y = 0)& = \pi \\
P(Y = y)& = \Big( \frac{ 1 - \pi }{ 1 - e^{-\lambda} } \Big) \frac{ \lambda^y e^{-\lambda} }{ y! } & y = 1, 2, \dots
\end{align}
$$


**The (2,2( element of $I(\theta)$ is**

$$
(1-\pi) \Big( \frac{ 1 }{ \lambda(1- e^{-\lambda}) } - \frac{ e^{-\lambda} }{ (1-e^{-\lambda})^2 } \Big)
$$





# 2.42
**Use simulation to verify that the inverse information matrix Example 2.21 (p. 78) is correct when $\mu = 1$ and $\sigma = 1$. One approach is to generate samples of size $n=100$ (or larger) form a $\text{normal}(1,1)$ distribution and exponentiate to get lognormal data. Then form the log likelihood and find the estimates $\mu, \sigma^2, \lambda$. Repeat for 1000 replications giving a data matrix of size 1000 by 3 estimates. Compute the sample covariance matrix of these and compare it to the inverse of the given information matrix.**





# 2.44
**Continuing the last problem, show that the Fisher information matrix for the $\beta$ part of the generalized linear model is given by**

$$
\overline{ I }(\beta) = \frac{ 1 }{ n } \sum_{i=1}6n \frac{ D_i D_i^T }{ \text{Var}(  Y_i ) }
$$

**Here you can use either of two methods: a) take the expectation of the negative of the derivative of $S(\beta, \phi)$, and noting that all the ugly derivatives drop out because $E(Y_i - \mu_i) = 0$. or b) the individual summed components of $\overline{ I }(\beta)$ can also be found using the cross-product definition of information in (2.39 p. 67).**


# 2.47
**A mixture of three component densities has the form**

$$
f(y; \theta, p) = p_1 f_1(y; \theta) + p_2 f_2(y; \theta) + p_3 f_3(y; \theta)
$$

**where $p_1 + p_2 + p_3 = 1$. We observe an iid sample $Y_1, \dots , Y_n$ from $f(y; \theta, p)$.**

## a
**Show how to define multinomial$(1; p_1, p_2, p_3)$ vectors $(Z_{i1}, Z_{i2}, Z_{i3})$ to get a representation for the $Y_i$ from $f(y; \theta, p)$ based on independent random variables $X_{i1}, X_{i2}, X_{i3}$ from the individual components.**



## b
**Give the complete data log likelihood and the function $Q$ to be maximized at the M step.**

