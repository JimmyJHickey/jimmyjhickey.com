---
layout: post
comments: false
title: Example Problems on Hypothesis Testing
description: ST702 Homework 7 on Hypothesis Testing
tags: ST702 Hypothesis-Testing
category: ST702
---

* Do not remove this line (it will not be displayed)
{:toc}


# 8.2
**In a given city it is assumed that the number of automobile accidents in a given year follows a Poisson distribution. In past years the average number of accidents per year was 15, and this year it was 10. Is it justified to claim that the accident rate has dropped?**




# 8.6
**Suppose that we have two independent random samples: $X_1, \dots , X_N \stackrel{ \text{iid}}{\sim} exp(\theta)$ and $Y_1, \dots , Y_N \stackrel{ \text{iid}}{\sim} exp(\mu)$.**

## a
**Find the LRT of $H_0: \theta = \mu \text{ vs. } H_1: \theta \neq \mu$.**


## b
**Show that the test in part (a) can be based on the statistic**

$$
T = \frac{ \sum X_i }{ \sum X_i + \sum Y_i }.
$$



## c
**Find the distribution of $T$ when $H_0$ is true.**





# 8.8
**A special case of a normal family is one in which th mean and the variance are related, that $n(\theta, a \theta)$ family. If we are interested in testing this relationship regardless of the value of $\theta$, we are again faced with a nuisance parameter problem.**

## a
**Find the LRT of $H_0: a = 1 \text{ vs. } H_1: a \neq 1$ based on a sample $X_1, \dots , X_n$ from a $n(\theta, a \theta)$ family, where $\theta$ is unknown.**




## b
**A similar question can be asked about a related family, the $n(\theta, a \theta^2)$ family. Thus, if $X_1, \dots , X_N \stackrel{ \text{iid}}{\sim} n(\theta, a \theta^2)$, where $\theta$ is unknown, find the LRT of $H_0: a = 1 \text{ vs. } H_1: a \neq 1$.**



# 8.9
**Stefanski (1996) establishes the arithmetic-geometric-harmonic mean inequality (see Example 4.7.8 and Miscellanea 4.9.2) using a proof based on likelihood ratio tests. Suppose that $Y_1, \dots , Y_n$ are independent with pdfs $\lambda_i e^{-\lambda_i y_i}$, and we want to test $H_0: \lambda_1 = \dots = \lambda_n \text{ vs. } H_1 \lambda_i \text{ are not all equal}$.**

## a
**Show that the LRT statistic is given by $(\overline{ Y })^{-n}/(\prod Y_i)^{-1}$ and hence deduce the arithmetic-geometric mean inequality.**



## b
**Make the transformation $X_i = 1/Y_i$, and show that the LRT statistic based on $X_1, \dots , X_n$ is given by $\Big[ n / \sum (1/X_i) \Big]^n / \prod X_i$ and hence deduce the geometric-harmonic mean inequality.**

