---
layout: post
comments: false
title: Example Problems on Asymptotics
description: ST793 Homework 4 on Asymptotics
tags: ST793 Likelihoods Statistics
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

5.5, 5.9, 5.11, 5.13, 5.24 

# 5.5
**Consider the simple linear regression setting**

$$
Y\_i = \alpha + \beta x\_i + e\_i,  \ i = 1, \dots ,n,
$$

**where the $x\_i$ are known constants, and $e\_1, \dots , e\_i$ are iid with mean 0 and finite variance $\sigma^2$. After a little algebra, the least squares estimator has the following representation**


$$
\widehat \beta - \beta = \frac{ \sum\_{i=1}^n (x\_i - \overline{ x }) e\_i }{ \sum\_{i=1}^n(x\_i - \overline{ x })^2 }.
$$

**Using that representation, prove that $\widehat \beta \stackrel{ \text{p}}{\rightarrow} \beta$ as $n \rightarrow \infty$ if $\sum\_{i=1}^n (x\_i - \overline{ x })^2 \rightarrow \infty$.**




# 5.9
**Let $X\_1, \dots , X\_n$ be iid from a distribution with mean $\mu$, variance $\sigma^2$ and finite central moments, $\mu\_3$ and $\mu\_4$. Consider $\widehat \theta = \overline{ X } / s\_n$, a measure of "effect size" used in meta-analysis. Prove that $\widehat \theta \stackrel{ \text{p}}{\rightarrow} \theta = \mu / \sigma$ as $n \rightarrow \infty$.**



# 5.11
**In the continuation of Example 5.20 (p. 230) on 231, it follows that under the local alternative $\mu\_i = \mu + d\_i/\sqrt{ n }$, $(k-1) F = \sum\_{i=1}^k n (\overline{ X }\_i - \overline{ \overline{ X }})^2/s\_p^2$ converges in distribution to a noncentral chi-squared distribution with $k-1$ degrees of freedom and noncentrality parameter $\lambda = d^T (I\_k - k^{-1} 1\_k 1\_k^T)d/\sigma^2 = \sum\_{i=1}^k(d\_i - \overline{ d })^2 / \sigma^2$. Now, if the data in a one-way ANOVA setup such as Example 5.20 (p.230) are normally distributed with means $\mu\_1 , \dots \mu\_k$ and common variance $\sigma^2$, then the exact power of the ANOVA $F$ statistic is the probability that a noncentral $F$ distribution with $k-1$ and $k(n-1$ degrees of freedom and noncentrality parameter $\lambda = \sum\_{i=1}^{k}n(\mu\_i - \overline{ \mu })^2 / \sigma^2$ is larger than a percentile of the central version f that $F$ distribution. In R, that would be `1-pf(qf(.95,k-1,k*(n-1)),k-1,k*(n-1),nc)`, where $\text{nc} = \lambda$ and the level is 0.05. Show that if $\mu\_i = \overline{ \mu } + d\_i / \sqrt{ n }$, then $\sum\_{i=1}^k (d_i - \overline{ d })^2 / \sigma^2$ = \sum\_{i=1}^k n(\mu\_i - \overline{ \mu })^2 / \sigma^2$, that is, the asymptotic chi-squared approximation uses the same noncentrality parameter. In R that would be `1-pchisq(qchisq(.95,k-1),2,nc)`. Compare the approximation for $k=3$ and $nc=10$ to the true power for $n=5,10,$ and $20$.**



# 5.13
**Suppose that $\widehat \theta_1$ is $\text{AN}(\theta_0, A_1/n)$ as $n \rightarrow \infty$.**


## a.
**What can we say about the consistency of $\hat \theta_1$? Why?**




## b.
**If $\widehat \theta_1 - \widehat \theta_2 \stackrel{ \text{p}}{\rightarrow} 0$, what can we say about the consistency of $\widehat \theta_2$? Why?**



## c.
**If $\sqrt{ n }(\widehat \theta_1 - \widehat \theta_2) \stackrel{ \text{p}}{\rightarrow} b $, what can we say about the asymptotic normality of $\widehat \theta_2$? Why?**


# 5.24 
**When two independent binomials $X_1$ is $Binomial(n_1, p_1)$ and $X_2$ is $Binomial(n_2, p_2)$, are put in the form of a $2 \times 2$ table (see Example 5.31, p. 240), then one often estimates the odds ratio**

$$
\theta = \frac{ \frac{ p_1 }{ 1-p_1 } }{ \frac{ p_2 }{ 1-p_2 } } = \frac{ p_1 ( 1- p_2) }{ p_2 (1 - p_1) }.
$$

**The estimate $\widehat \theta$ is obtained by inserting $\widehat p_1 = X_1 / n_1$ and $\widehat p_2 = X_2 / n_2$ in the above expression. Show that the $\log(\widehat \theta)$ has asymptotic variance**

$$
\frac{ 1 }{ n_1 p_1 (1-p_1) } + \frac{ 1 }{ n_2 p_2(1-p_2) }
$$