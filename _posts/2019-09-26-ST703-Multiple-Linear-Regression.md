---
layout: post
comments: false
title: Example Problems on Multiple Linear Regression
description: ST703 Homework 4 on Multiple Linear Regression
tags: ST703 SAS Regression ANOVA Examples Statistics
---

Problems: 1, 2, 3


* Do not remove this line (it will not be displayed)
{:toc}


# 1

**"Resolution 5K Runs" typically occur on January 1st as a way to \start the new year off right" and raise funds for charity. Dataset ResolutionRun2004.txt in the database provides information on a race that occurred in 2004, giving the pace (minutes per mile), sex, age (years), and squared age for each of $n = 160$ runners. Ignoring sex, and focusing on the bivariate data consisting of age ($X$) and pace ($Y$), you will investigate a regression that models the mean pace as a quadratic in age:**

$$
\mu(x) = \beta_0 + \beta_1 x + \beta_2 x^2
$$

## (a)
**Obtain the least squares regression equation.**



## (b)
**Construct 95% confidence intervals for $\beta_0$, $\beta_1$, and $\beta_2$ and interpret the results.**



## (c)
**Estimate the error variance, $\sigma^2$, for an individual measurement of pace, given a fixed age.**



## (d)
**Which do you expect would be larger, $Var(Y)$ or $Var(Y|X=x)$? Which quantity was estimated in part (c)?**



## (e)
**Report a standard error and 95% confidence interval for the mean pace for runners aged $x=34$.**



## (f)
**Obtain a 95% prediction interval for the pace of an individual runner selected from the cohort of 34 year-olds.**


## (g)
**Explain the dierence between the two intervals in (e) and (f).**


## (h)
**Construct a 99% condence interval for the parameter $\theta = \beta_1 - \beta_2$.**


## (i)
**Consider the _rate_ at which the mean function for pace, $\mu(x)$, changes with age.**

### i.
**At what rate is the mean function for pace, $\mu(x)$, changing with age?**


### ii.
**Estimate the rate of change for 30 year-olds.**



### iii.
**Estimate the rate of change for 50 year-olds.**



### iv.
**A simple and familiar test of one of the regression parameters can we used to investigate the claim that \the rate at which the mean function for pace changes with age is constant." State relevant hypotheses and conduct the test.**



## (j)
**Under the quadratic model, at what age is the mean function for pace minimized? Estimate this age.**

# 2
**Consider the four different regression functions in Exercise 11.2 as possible candidates for expressing the expected log (oxygen demand) as a function of five explanatory variables in Example 11.2.**

## (b)
**Interpret the parameters $\beta_1$ and $\beta_2$ in exercise 11.2a.**



## (c)
**Interpret the quantity $\beta_1+\beta_2 + \beta_3$ in exercise 11.2a.**


# 3
**In Example 11.8, we considered a study in which responses were measured at $n=8$ settings of two independent variables $X_{1}$ and $X_{2}$. Suppose that we are considering two models for the study data:**


**model 1**

$$
Y_1 = \beta_0 + \beta_1 x_{i1} + \beta_{i2} x_{i2} + E_i;
$$


**and model 2**


$$
Y_i = \beta_0 + \beta_1 x_{i1} + \beta_{i2} x_{i2} + \beta_3 x_{i1} x_{i2} + E_i.
$$


## (a)
**Argue that, while the parameter $\beta_0$ has the same meaning in both models, the meanings of the parameters $\beta_1$ and $\beta_2$ are different in the two models.**



## (b)
**Determine the estimated least squares prediction equation using model 1.**


## (d)
**Use the given ANOVA table to test the null hypothesis that $H_0: \ \beta_1 = \beta_2 = 0$ in model 1. Write your conclusion.**


## (e)
**Determine the estimated least squares prediction equation based on model 2.**