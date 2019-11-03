---
layout: post
comments: false
title: Example Problems on Multivariate Distributions
description: ST701 Homework 5 on Multivariate Distributions
tags: ST701 Distributions Expectations Statistics
---

Problems: 4.5, 4.10, 4.15, 4, 4.17, 4.24, 4.30, 4.40


* Do not remove this line (it will not be displayed)
{:toc}



# 4.5

## a
**Find $P(X > \sqrt{Y}$ if $X$ and $Y$ are jointly distributed with pdf**

$$
f(x,y) = x + y, \ 0 \leq x \leq 1, \ 0 \leq y \leq 1.
$$



## b
**Find $P(X^2 < Y < X)$ if $X$ and $Y$ are jointly distributed with pdf**

$$
f(x,y) = 2x, \ 0 \leq x \leq 1, \ 0 \leq y \leq 1.
$$


# 4.10
**The random pair $(X,Y)$ has the distribution**

$$
\begin{array}{c c | c c c}
	& & & X & \\
	& & 1 & 2 & 3 \\ \hline
	& 2 & \frac{ 1 }{ 12 } & \frac{ 1 }{ 6 } & \frac{ 1 }{ 12 }\\
	Y & 3 & \frac{ 1 }{ 6 } & 0 & \frac{ 1 }{ 6 }\\
	& 4 & 0 & \frac{ 1 }{ 3 } & 0
\end{array}
$$


## a
**Show that $X$ and $Y$ are dependent.**



## b
**Given a probability table for random variables $U$ and $V$ that have hte same marginals as $X$ and $Y$ but are independent.**




# 4.15
**Let $X\sim Poisson(\theta), \ Y\sim Poisson(\lambda)$, independent. It was shown in Theorem 4.3.2 that the distribution of $X+Y$ is $Poisson(\theta + \lambda)$. Show that the distribution of $X \| X+Y$ is binomial with success of probability $\theta / (\theta + \lambda)$. What is the distribution of $Y\| X + Y$?**


# 4
** If $X$ has a binomial distribution with parameters $n$ and $p$, $Y$ has a binomial distribution with parameters $m$ and $p$, and $X$, $Y$ are independent. Show that $X + Y$ has a binomial distribution with parameters $n + m$ and $p$.**


# 4.17
**Let $X$ be an $exponential(1)$ random variable and define $Y$ to be the integer part of $X+1$, that is**

$$
Y = i + 1\ \text{if and only if} \ i \leq X \< i + 1, \ i = 0, 1, 2, \dots
$$


## a
**Find the distribution of $Y$. What well-known distribution does $Y$ have?**



## b
**Find the conditional distribution of $X - 4$ given $Y \geq 5$.**




# 4.24
**Let $X$ and $Y$ be independent random variables with $X \sim gamma(r, 1)$ and $Y \sim gamma(s,1)$. Show that $Z_1 = X+Y$ and $Z_2 = X/(X+Y)$ are independent, and find the distribution of each ($Z_1$ is gamma and $Z_2$ is beta).**



# 4.30
**Suppose the distribution of $Y$ is conditional on $X=x$ is $n(x,x^2)$ and that the marginal distribution of $X$ is $uniform(0,1)$.**

## a
**Find $E(Y)$, $Var(Y)$, and $Cov(X,Y)$.**



## b
**Prove that $Y/X$ and $X$ are independent.**





# 4.40
**A generalization of the beta distriubtion is the _Dirichlet_ distribution. In its bivariate version $(X,Y)$ have pdf**

$$
f(x,y) = C x^{a-1} y^{b-1}(1-x-y)^{c-1}, \ 0 < x < 1, \ 0 < y < 1, \ 0 < y < 1 - x < 1,
$$

**where $a>0,\ b>0$, and $c > 0$ are constants.**


## a
**Show that $C = \frac{ \Gamma(a + b + c) }{ \Gamma(a) + \Gamma(b) + \Gamma(c) }$**



## b
**Show that, marginally, both $X$ and $Y$ are beta.**



## c
**Find the conditional distribution of $Y\| X = x$, and show that $Y/(1-x)$ is $beta(b,c)$,**


## d
**Show that $E(XY) = \frac{ ab }{ (a+b+c+1)(a+b+c)}$, and find their covariance.**