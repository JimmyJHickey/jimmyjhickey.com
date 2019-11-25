---
layout: post
comments: false
title: Example Problems on Properties of a Random Sample
description: ST701 Homework 6 on Properties of a Random Sample
tags: ST701 Distributions Expectations Statistics Random-Sample
---

Problems: 4.54, 5.6, 5.22, 5.24, 5.42, 5.44, 7, 8


* Do not remove this line (it will not be displayed)
{:toc}


# 4.54
**Find the pdf of $\product_{i=1}^{n} X_i$ where the $X_i$'s are independent uniform(0, 1) random variables. (_Hint_: Try to calculate the cdf, and remember thre relationship between uniforms and exponentials.)**


# 5.6
**If $X$ has pdf $f_X(x)$ and $Y$, independent of $X$, has pdf $f_Y(y)$, establish formulas, similar to (5.2.3), for the random variable $Z$ in each of the following situations.**



## a.
$$
Z = X - Y
$$





## b.
$$
Z = XY
$$




## c.
$$
Z = X/Y
$$




# 5.22
**Let $X$ and $Y$ be iid n(0, 1) random variables, and define $Z = \min(X,Y)$. Prove that $Z^2 \sim \chi^2_1$.**



# 5.24
**Let $X_1, \dots ,X_n$ be a random sample from a population with pdf**


$$
f_X(x) = 
\begin{cases}
1/\theta & \text{if } 0 < x < \theta \\
0 & \text{otherwise.}
\end{cases}
$$


**Let $X_{(1)}< \dots < X_{(n)}$ be the order statistics. Show that $X_{(1)} / X_{(n)}$ and $X_{(n)}$ are independent random variables.**

# 5.42
**Similar to Example 5.5.11, let $X_1, X_2, \dots$ be iid and $X_{(n)} = \max_{1 \leq i \leq n} X_i$.**


## a.
**If $X_i \sim beta(1, \beta)$, find a value of $\nu$ so that $n^\nu (1 - X_{(n)})$ converges in distribution.**




## b.
**If $X_i \sim exponential(1)$, find a sequence $a_n$ so that $X_{(n)} - a_n$ converges in distribution.**



# 5.44
**Let $X_i, i = 1, 2, \dots$ be independent Bernoulli($p$) random variables and let $Y_n = \frac{ 1 }{ n } \sum_{i=1}^n X_i$.**


## a.
**Show that $\sqrt{n} (Y_n - p) \arrow n[0, p(1-p)]$ in distribution.**





## b,
**Show that for $p \neq 1/2$, the estimate of variance $Y_n(1-Y_n)$ satisfies $\sqrt{n} [Y_n ( 1 - Y_n)-p(1-p) ] \arrow n[0, (1-2p)^2 p (1-p)]$ in distribution.**





## c.
**Show that for $p = 1/2$, $n [Y_n(1-Y_n)-\frac{ 1 }{ 4 }] \arrow \frac{ 1 }{ 4 } \chi^2_1$ in distribution. (If this appears strange, note that $Y_n(1-Y_n) \leq 1/4$, so the left-hand is always negative. An equivalent form is $2n [\frac{ 1 }{ 4 } - Y_n(1-Y_n)] \arrow \chi^2_1$.)**


# 7
**Let $X_1, X_2, \dots$ be a sequence of independent random variables with $E(X_i) = \mu$ and $V(X_i) = \sigma_i^2$. Show that if $n^{-2} \sum_{i=1}^n \sigma_i^2 \rightarrow 0 $, then $\bar{X} \rightarrow \mu$ in probability.**


# 8
**Let $X_i$ be as in Problem 7 above but with $E(X_i) = \mu_i$ and $n^{-1} \sum_{i=1}^{n} \mu_i \arrow \mu$. Show that $\bar{X} \arrow \mu$ in probability.**


