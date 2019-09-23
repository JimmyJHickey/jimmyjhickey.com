---
layout: post
comments: false
title: Example Problems on Transformation and Expectations of RVs
description: ST701 Homework 3 on Transformation and Expectations of RVs
tags: ST701 Transformations Expectations Statistics
---

Problems: 1.1, 1.4, 1.5, 1.13, 1.23, Problem 6


* Do not remove this line (it will not be displayed)
{:toc}

# 2.6
**In each of the following find the pdf of $Y$ and show that the pdf integrates to 1.**

## (a)

$$
f_X(x) = \frac{ 1 }{ 2 } e^{-|x|}, \ -\infty < x < \infty; \ Y=|X|^3
$$


## (b)

$$
f_X(x) = \frac{ 3 }{ 8 }(x+1)^2, \ -1 < x < 1;  \ Y = 1 - X^2
$$


## (c)

$$
f_X(x) = \frac{ 3 }{ 8 }(x+1)^2, \ -1 < x < 1;  \ Y = 1 - X^2 \text{ if } X \leq 0 \text{ and } Y = 1 - X \text{ if } X > 0
$$

#  2.7
**Let $X$ have pdf $f_X(x) = \frac{ 2 }{ 9 }(x+1)$ for $-1 \leq x \leq 2$.**

## (a)
**Find the pdf of $Y=X^2$. Note that Theorem 2.1.8 is not directly applicable to this problem.**


## (b)
**Show that Theorem 2.1.8 remains valid if the sets $A_0, A_1, \dots, A_k$ contain $X$ and apply the extension to solve part (a) using $A_0=\varnothing, \ A_1 = (-2, 0)$, and $A_2=(0,2)$.**

#  2.9
**If the random variable $X$ has pdf**

$$
f(x)=
    \begin{cases}
        \begin{align}
            & \frac{ x-1 }{ 2 } & 1 < x < 3\\
            & 0 & \text{otherwise,}
        \end{align}
    \end{cases}
$$

**find a monotone function $u(x)$ such that the random variable $Y=u(X)$ has a uniform(0,1) distribution.**


#  2.11
**Let $X$ have the standard normal pdf, $f_X(x) = (1/\sqrt{2\pi}) e^{-x^2/2}$.**

## (a)
**Find $E(X^2)$ directly, and then by using the pdf of $Y=X^2$ from Example 2.1.7 and calculate $E(Y)$.**


## (b)
**Find the pdf of $Y = \| X \|$, and find its mean and variance.**


#  2.23
**Let $X$ have the pdf**

$$
	\begin{align}
		f(x) & = \frac{ 1 }{2  } (1+x), & -1 < x< 1.
	\end{align}
$$

## (a)
**Find the pdf of $Y = X^2$.**


## (b)
**Find $E(Y)$ and $Var(Y)$.**



#  2.24
**Compute $E(X)$ and $Var(X)$ for each of the following probability distributions.**

## (a)

$$
f_X(x) = ax^{a-1},\ 0 < x< 1,\ a > 0
$$



## (b)

$$
f_X(x) = \frac{ 1 }{ n }, \ x = 1, 2,\dots , n, \ n > 0 \text{ an integer} 
$$


## (c)

$$
f_X(x) = \frac{ 3 }{ 2 } (x-1)^2, \ 0 < x < 2
$$



#  2.25
**Suppose the pdf $f_X(x)$ of a random variable $X$ is an _even function_. ($f_X(x)$ is an _even function_ if $f_X(x) = f_X(-x)$ for every $x$.) Show that**

## (a)
**$X$ and $-X$ are identically distributed.**


## (b)
**$M_X(t)$ is symmetric about 0.**

#  2.33
**In each of the following cases verify the expression given for the moment generating function, and in each case use the mgf to caclulate $E(X)$ and $Var(X)$.**

## (a)

$$
P(X=x) = \frac{ e^{-\lambda} \lambda^x }{ x! },\ M_X(t) = e^{\lambda (e^t - 1)},\ x = 0, 1, \dots;\ \lambda > 0
$$



## (b)

$$
P(X=x) = p(1-p)^x,\ M_X(t) = \frac{ p }{ 1-(1-p)e^t },\ x=0,1,\dots ;\ 0<p<1
$$


## (c)

$$
f_X(x) = \frac{ e^{-(x-\mu)^2/(2\sigma^2)} }{ \sqrt{2\pi} \sigma },\ M_X(t) = e^{\mu t+ \sigma^2 t^2/2},\ -\infty < x< \infty,\ -\infty < \mu < \infty, \ \sigma > 0
$$