---
layout: post
comments: false
title: Example Problems on Random Variables and Expected Values
description: ST501 Homework 3 on Random Variables and Expected Values
tags: ST501 Random-Variables Expected-Values Probability Examples Statistics
---

Problems: 2.13, 2.14, 2.33 (just find the density), 2.34, 2.38, 2.39 bc, 4.2, 4.4, 4.5, 4.10, 4.30


* Do not remove this line (it will not be displayed)
{:toc}


# 2.13
**A multiple-choice test consists of 20 items, each with four choices. A student is able to eliminate one of the choices on each question as incorrect and chooses randomly for the remaining three choices. A passing grade is 12 items or more correct.**


## a.
**What is the probability that the student passes?**


By eliminating one incorrect choice, the student has a $\frac{1}{3}$ chance to get a question right and a $\frac{2}{3}$ chance to get it wrong. To pass, we are looking for $P(Y\ge 12)$. This can be thought of as $P(Y\ge 12) = P(Y = 12) + P(Y = 13) \dots P(Y = 20)$, or

$$
    P(Y\ge 12) = \sum_{k=12}^{20} {20 \choose k} * (\frac{1}{3})^{k} (\frac{2}{3})^{20-k}
$$


## b.
**Answer the question in part (a) again, assuming that the student can eliminate two of the choices on each question.**

By eliminating two incorrect choices, the student now has a $\frac{1}{2}$ of getting the question correct or incorrect by guessing.

$$
    P(Y\ge 12) = \sum_{k=12}^{20} {20 \choose k} * (\frac{1}{3})^{k} (\frac{2}{3})^{20-k}
$$


# 2.14
**Two boys play basketball in the following way. They take turns shooting and stop when a basket is made. Player A goes first and has a probability $p_{1}$ of making a basket on any throw. Player B, who shoots second, has a probability of $p_{2}$ of making a basket. The outcomes of the successive trials are assumed to be independent.**

## a.
**Find the frequency function for the total number of attempts.**

Let $X$ be the total number of attempts made by both Player A and Player B. If Player A wins, then they will have shot an odd total number of shots, each with the same even number of misses. If Player B wins, then they will have shot an even total number of shots, with Player A having missed one more shot than Player B. So,

$$
P(X=n)=
    \begin{cases}
        \begin{align}
            & p_1 (1-p_1)^{\frac{n-1}{2}} (1-p_2)^{\frac{n-1}{2}} & \text{Player A Wins} \\
            & p_2 (1-p_1)^{\frac{n}{2}} (1-p_2)^{\frac{n}{2}-1} & \text{Player B Wins} 
        \end{align}
    \end{cases}
$$

Cleaning up the exponents gives,

$$
P(X=n)=
    \begin{cases}
        \begin{align}
            & p_1 (1-p_1)^{k-1} (1-p_2)^{k-1} & n = 2k-1 \text{ Player A Wins}\\
            & p_2 (1-p_1)^{k} (1-p_2)^{k-1} &  n = 2k \text{ Player B Wins} 
        \end{align}
    \end{cases}
$$

## b.
**What is the probability that player A wins?**

By summing the simplified case

$$
    \begin{align}
        \sum_{k=1}^{\infty} p_1 (1-p_1)^{k-1} (1-p_2)^{k-1} & = p_1 \sum_{k=1}^{\infty} (1-p_1)^{k-1} (1-p_2)^{k-1}\\
            & = p_1 \sum_{k=1}^{\infty} \big((1-p_1)(1-p_2)\big)^{k-1} \\
            & = \frac{p_1}{p_1+p_2-p_1 p_2}
    \end{align}
$$

# 2.33
**Let $F(x) = 1 - exp(-\alpha x^{\beta})$ for $x \ge 0, \  \alpha > 0, \ \beta > 0$, and $F(x) = 0$ for $x<0$. Find the corresponding density.**

$$
    \begin{align}
        f_{X}(x) &= \frac{d}{dx}(1-\exp(-\alpha x^{\beta})) \\
            &= 0 - (\alpha \cdot \beta \cdot x^{\beta - 1} \cdot \exp(-\alpha x^{\beta})) \\
            &= - \alpha \cdot \beta \cdot x^{\beta - 1} \cdot \exp(-\alpha x^{\beta})
    \end{align}
$$

# 2.34
**Let $f(x) = (1+\alpha x)/2$ for $-1 \le x \le 1$ and $f(x)=0$ otherwise, where $-1 \le \alpha \le 1$. Show that $f$ is a density, and find the corresponding cdf. Find the quartiles and the median distribution in terms of $\alpha$.**

To show that $f$ is a density, we must show that $f\ge 0$, that $f$ is piecewise continuous, and that $\int_{-\infty}^{\infty} f(x) dx = 1$.

_$f\ge 0$_

Let's see if this is the case,

$$
    \begin{align}
        (1+\alpha x)/2 & \gt 0 \\
        1+\alpha x & \gt 0 \\
        \alpha x & \gt -1
    \end{align}
$$

Notice that $f$ is minimized when $x=1, \alpha = -1$ and $x=-1, \alpha=1$, where $\alpha x = -1 \gt -1$. Thus, $f\ge 0$.

_$f$ is piecewise continuous_

The function $f$ is a linear function and is continuous.

$\int_{-\infty}^{\infty} f(x) dx = 1$

$$
  \int_{-\infty}^{\infty} (1+\alpha x)/2 dx  \\
  \int_{-1}^{1} (1+\alpha x)/2 dx  \\
  \int_{-1}^{1} \frac{1}{2} dx + \int_{-1}^{1} \frac{\alpha x}{2} dx \\
  \frac{1}{2}(1- -1) + \frac{1}{2}{\alpha}(\frac{1}{2}(1^1-(-1)^2)) \\
  \frac{1}{2}(2) + 0 \\
  1
  
$$

_Find the corresponding cdf_

$$
    \begin{align}
        F(x) & = \int_{-\infty}^{x} f(t) dt \\
            & = \int_{-1}^{x} f(t) dt \\
            & = \int_{-\infty}^{x} \frac{1+\alpha t}{2} dt \\
            & = \int_{-1}^{x} \frac{1}{2} dt + \int_{-1}^{x} \frac{\alpha t}{2} dt \\
            & = \frac{1}{2} x + \frac{1}{2} + \frac{\alpha}{2}(\frac{1}{2}(x^{2}-(-1)^{2})) \\
            & = \frac{\alpha x^{2}}{2} + \frac{x}{2} + \frac{1}{2} - \frac{\alpha}{2}
    \end{align}
$$

_Find the quartiles and the median in terms of $\alpha$_

$$
    \begin{align}
        0.25 & = \frac{\alpha x_{0.25}^{2}}{2} + \frac{x_{0.25}}{2} + \frac{1}{2} - \frac{\alpha}{2} \\
        x_{0.25} & = \frac{-1 \pm \sqrt{1 - \alpha + \alpha^{2}}}{\alpha}\\
        0.5 & = \frac{\alpha x_{0.5}^{2}}{2} + \frac{x_{0.5}}{2} + \frac{1}{2} - \frac{\alpha}{2} \\
        x_{0.5} & = \frac{-1 \pm \sqrt{1 + \alpha^{2}}}{\alpha} \\
        0.75 & = \frac{\alpha x_{0.75}^{2}}{2} + \frac{x_{0.75}}{2} + \frac{1}{2} - \frac{\alpha}{2} \\
        x_{0.75} & = \frac{-1 \pm \sqrt{1 + \alpha + \alpha^{2}}}{\alpha}
    \end{align}
$$

# 2.38
**If $f$ and $g$ are densities, show that $\alpha f + (1-\alpha)g$ is a density where $0 \le \alpha \le 1$.**

To show that $\alpha f + (1-\alpha)g$ is a density, we must show that $\alpha f + (1-\alpha)g \ge 0$, that $\alpha f + (1-\alpha)g$  is piecewise continuous, and $\int_{-\infty}^{\infty}\alpha f + (1-\alpha)g dx = 1$.


_$\alpha f + (1-\alpha)g \ge 0$_

Since $f$ and $g$ are densities, they are both always greater than 0. Also, since $0 \le \alpha \le 1$, $\alpha, (1-\alpha) \ge 0$. Thus, $\alpha f + (1-\alpha)g \ge 0$.


_$\alpha f + (1-\alpha)g$  is piecewise continuous_

Since $f$ and $g$ are densities, they are piecewise continuous. They are each being multiplied by a scalar, so each piece is still piecewise continuous. Similarly, adding two piecewise continuous will still be piecewise continuous.


_$\int_{-\infty}^{\infty}\alpha f + (1-\alpha)g dx = 1$_

$$
    \begin{align}
        \int_{-\infty}^{\infty}\alpha f + (1-\alpha)g dx & = \int_{-\infty}^{\infty} \alpha f dx + \int_{-\infty}^{\infty} (1-\alpha)g dx \\
        & = \alpha \int_{-\infty}{infty} f dx + (1-\alpha)\int_{\infty}{infty}g dx \\
        & = \alpha (1) + (1-\alpha) (1) \\
        & = 1
    \end{align}
$$


# 2.39
**The *Cauchy* cumulative distribution function is**
$$
    \begin{align}
        F(x)&=\frac{1}{2} + \frac{1}{\pi}\tan^{-1}(x), &-\infty < x < \infty
    \end{align}
$$

## b.
**Find the density function.**

$$
    \begin{align}
        f(x) & = \frac{d}{dx}(F(x)) \\
            & = \frac{d}{dx}\Big(\frac{1}{2} + \frac{1}{\pi}\tan^{-1}(x)\Big) \\
            & = \frac{1}{\pi}\frac{1}{1+x^2}
    \end{align}
$$

## c.
**Find $x$ such that $P(X>x)=.1$.**

$$
    \begin{align}
        0.1  & = \frac{1}{2} + \frac{1}{\pi}\tan^{-1}(x_{0.1}) \\
        x_{0.1} & = -0.128016
    \end{align}
$$

# 4.2
**If $X$ is a discrete uniform random variable -- that is, $P(X=k)=1/n$ for $k=1,2,\dots n$ -- find $E(X)$ and $\text{Var}(X)$.**

_$E(X)$_

$$
    \begin{align}
        E(X) & = \sum_{i=1}^{n} i \cdot \frac{1}{n} \\
            & = \frac{1}{n} \cdot \frac{n(n+1)}{2} \\
            & = \frac{n+1}{2}
    \end{align}
$$

_$Var(X)$_

$$
    \begin{align}
        E(X^{2}) & = \sum_{i=1}^{n} i^{2} \cdot \frac{1}{n} \\
            & = \frac{1}{n} \Big( \frac{n(n+1)(2n+1)}{6} \Big) \\
            & = \frac{(n+1)(2n+1)}{6}
    \end{align}
$$

$$
    \begin{align}
        \text{Var}(X) &= E(X^2) - (E(X))^2 \\
            & = \frac{(n+1)(2n+1)}{6} - \Big( \frac{n+1}{2} \Big)^2 \\ 
            & = \frac{1}{12}(n^{2} - 1)
    \end{align}
$$

# 4.4
**Let $X$ have the cdf $F(x) = 1-x^{-\alpha}, \ x \ge 1$.**

## a.
**Find $E(X)$ for those values of $\alpha$ for which $E(X)$ exists.**

First, we need to find $f_{X}(x)$.

$$
    \begin{align}
        f_{X}(x) &= \frac{d}{dx}(1-x^{-\alpha}) \\
            & = \alpha x^{-1-\alpha}
    \end{align}
$$

Now, $E(X)$.

$$
    \begin{align}
        E(X) & = \int_{1}^{\infty} x \alpha x^{-1-\alpha} dx \\
            & = \alpha \frac{x^{-\alpha}}{1-\alpha} \bigg\rvert_{1}^{\infty} \\
            & = 0 - \frac{\alpha}{1-\alpha} \\
            & = \frac{\alpha}{\alpha - 1}
    \end{align}
$$

## b.
**Find $\text{Var}(X)$ for those values of $\alpha$ for which it exists.**

To find $\text{Var}(X)$ we need to find $E(X^2)$.

$$
    \begin{align}
        E(X^2) & = \int_{1}^{\infty} x^2 \alpha x^{-1-\alpha} dx \\
            & = \alpha \frac{x^{2-\alpha}}{2-\alpha} \bigg\rvert_{1}^{\infty} \\
            & = \frac{\alpha}{\alpha - 2}
    \end{align}
$$

So,

$$
    \begin{align}
        \text{Var}(X) & = E(X^2) - E(X)^2 \\
            & = \frac{\alpha}{\alpha - 2} - (\frac{\alpha}{\alpha - 1})^2 \\
            & = \frac{\alpha}{(\alpha-2)(\alpha - 1)^2}
    \end{align}
$$

# 4.5
**Let $X$ have the density**

$$
    \begin{align}
        f(x) &= \frac{1+\alpha x}{2}, & -1 \le x \le 1, -1 \le \alpha \le 1
    \end{align}
$$

**Find $E(X)$ and $\text{Var}(X)$.**

$$
    \begin{align}
        E(X) & = \int_{-1}^{1} x \frac{1+\alpha x}{2} dx \\
            & = \int_{-1}^{1} \frac{x}{2} + \frac{1+\alpha x}{2} dx \\
            & = \int_{-1}^{1} \frac{x}{2} dx + \int_{-1}^{1} \frac{1+\alpha x}{2} dx \\
            & = \frac{\alpha}{3}
    \end{align}
$$


To find $\text{Var}(X)$ we need to find $E(X^2)$.

$$
    \begin{align}
        E(X^2) & = \int_{-1}^{1} x^2 \frac{1+\alpha x}{2} dx \\
            & = \int_{-1}^{1} \frac{x^2}{2} + \frac{1+\alpha x}{2} dx \\
            & = \frac{1}{3}
    \end{align}
$$

So,

$$
    \begin{align}
        \text{Var}(X) & = E(X^2) - E(X)^2 \\
            & = \frac{1}{3} - (\frac{\alpha}{3})^{2} \\
            & = \frac{1}{3} - \frac{\alpha^2}{9}
    \end{align}
$$



# 4.10
**A list of $n$ items is arranged in order; to find a requested item, they are searched sequentially until the desired item is found. What is the expected number of items that must be searched through, assuming that each item is equally likely to be requested? (Questions of this nature arise in the design of computer algorithms.)**

This is an applied version of a discrete uniform random variable. So, the expected number of items to search through is $P(X=k)=1/n$.

$$
    \begin{align}
        E(X) & = \sum_{i=1}^{n} i \cdot \frac{1}{n} \\
            & = \frac{1}{n} \cdot \frac{n(n+1)}{2} \\
            & = \frac{n+1}{2}
    \end{align}
$$

# 4.30
**Find $E[1/(X+1)]$, where $X$ is a Poisson random variable.**

For a Poisson random variable, 

$$
    \begin{align}
        P(X=k) & = \frac{\lambda^{k} e^{-\lambda}}{k!} & k=0,1,2,\dots
    \end{align}
$$

So,

$$
    \begin{align}
        E\big(\frac{1}{X+1}\big) & = \sum_{x=0}^{\infty} \frac{1}{x+1} \frac{e^{-\lambda} \lambda^{x}}{x!} \\
            & = e^{-\lambda} \sum_{x=0}^{\infty} \frac{\lambda^{x}}{(x+1)!} \\
            & = e^{-\lambda} \sum_{x=0}^{\infty} \frac{1}{\lambda} \frac{\lambda^{x+1}}{(x+1)!} \\
            & = e^{-\lambda} \frac{1}{\lambda} (e^{\lambda} - 1) \\
            & = \frac{1 - \cosh(\lambda) + \sinh(\lambda)}{\lambda}
    \end{align}
$$