---
layout: post
comments: false
title: Example Problems on Monte Carlo Simulation
description: ST793 Homework 8 on Monte Carlo Simulation
tags: ST793 Testing Asymptotics Monte Carlo Statistics
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

# 9.1
**In the context of Example 9.1 (p. 365) the MSE could be estimated by $\widehat{\text{MSE}}= N^{-1} \sum_{i=1}^N (\widehat{\theta}_i - \theta_0)^2$.**

## a.
**What is the standard deviation of $\widehat{\text{MSE}}$?**



## b.
**Based on a preliminary run of size $N_0$, how large should $N$ be to have the standard deviation of $\widehat{\text{MSE}} \leq d$?**


# 9.7
**Related tto the SV of the last problem, one might be interested in reported instead the coefficient of variation (CV), which is just the square root of $\widehat{SV}$, $\widehat{CV} = s_V / \overline{ V }$. Thus, use the Delta theorem with the asymptotic variance expression for $\widehat{SV}$, to obtain the asymptotic variance $\widehat CV$:**

$$
\frac{ \sigma^2_n }{ \mu^2_n } \Big( \text{Kurt}( V ) - 1 - 4 \frac{ \sigma_n }{ \mu_n }\text{Skew}( V ) + 4 \frac{ \sigma^2_n }{ \mu_n^2 }\Big)
$$

**where $\sigma^2_n = \text{Var}(  V )$ and $\mu_n = E(V)$.**

# 9.13
**In section 9.5.3 (p. 380), the phrase "mainly random noise" was used to describe the third decimal place of estimated convergence probabilities based on $N = 1000$ Monte Carlo replications. To quantify this phrase, suppose that $Y$ is $\text{binomial}(1000, 0.95)$ and $Y / 1000$ is the estimate of interest. Model the act of rounding from three decimal places to two as adding an independent uniform random variable $U$ on $(-0.005, 0.005)$ to $Y / 1000$. Show that the increase in the standard deviation of $Y/1000 + U$ compared to the standard deviation of $Y / 1000$ is 8.4%.**


# 7.2
**Let $Y_1, \dots , Y_n$ be iid from some distribution with finite fourth moment. The coefficients of variange is $\widehat \theta_3 = s_n / \overline{ Y }$.**

## a
**Define a three dimensional $\psi$ so that $\widehat \theta_3$ is defined by summing the third component. Find $A$, $B$, and $V$, where**

$$
V_{33} = \frac{ \sigma^4 }{ \mu^4 } - \frac{ \mu_3 }{ \mu^3 } + \frac{ \mu_4 - \sigma^4 }{ 4 \mu^2 \sigma^2 }.
$$


# 7.5
**Repeat the calculations in Section 7.2.4 (p.305) with $\widehat \theta_3 = \Phi\{(a - \overline{ Y })/s_n \}$ replacing $s_n$ and $\widehat \theta_4 = \Phi^{-1}(p) s_n + \overline{ Y }$ replacing $\log(s_n^2)$. Note that $\widehat \theta_3$ and $\widehat \theta_4$ are the maximum likeligood estimators of $P(Y\_1 \leq a)$ and the $p$th quantile qualtie of $Y\_1$ respectly, under a normal distribution assumption.**