---
layout: post
comments: false
title: Example Problems on Convergence of Random Variables
description: ST779 Homework 8 on Uniform Integrability
tags: ST779 Measure-Theory Uniform-Integrability Random-Variables
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**If $\\{ X_{n}  \\}$ is uniformly integrable and $Y_{n} = n^{-1}\sum_{i=1}^{n} X_{i}$, $n = 1, 2, \dots$, show that $\\{ Y_{n} \\}$ is also uniformly integrable.**

$$
\begin{align}
\sup_{n} & \int_{\mid Y_{n} \mid > C} \mid Y_{n} \mid dP \\
    & = \sup_{n} \int_{\mid n^{-1}\sum_{i=1}^{n} X_{i} \mid > C} \mid n^{-1}\sum_{i=1}^{n} X_{i} \mid dP \\
    & = \sup_{n} n^{-1} \int_{n^{-1} \mid \sum_{i=1}^{n} X_{i} \mid > C} \mid \sum_{i=1}^{n} X_{i} \mid dP \\
    & \leq \sup_{n} n^{-1} \int_{n^{-1}  \sum_{i=1}^{n} \mid X_{i} \mid > C}  \sum_{i=1}^{n} \mid X_{i} \mid dP \\
    & = \sup_{n} n^{-1} \sum_{i=1}^{n} \int_{n^{-1} \mid X_{i} \mid > C}  \mid X_{i} \mid dP \\
    & \leq \sup_{n} n^{-1} n \int_{n^{-1} n \mid X^{*} \mid > C}  \mid X^{*} \mid dP & X^{*} = \sup_{n} \mid X_i \mid \\
    & = \int_{\mid X^{*} \mid > C} \mid X^{*} \mid dP \rightarrow 0 & \text{ \{ $X_{i}$ \} u.i.}
\end{align}
$$

Thus, $\\{ Y_{i} \\}$ is uniformly integrable.

# 2
**A sequence of random variables $X_{n}$ is called uniformly integrable from above if $\sup_{n} E\Big( X_{n} 1 \\{ X_{n} > C \\} \Big)\rightarrow 0$ as $C \rightarrow \infty$.**

**Show that if $X_{n}$ are positive random variables with $\sup_{n} E(X_{n}) < \infty$, then $\log(X_{n})$ is uniformly integrable from above.**

$$
\begin{align}
\int_{\log(X_{n}) > C} & log(X_{n}) dP \\
    & =\int_{\log(X_{n}) > C} log(X_{n})  \frac{ X_{n} }{ X_{n} }dP \\
    & \leq \frac{ log(C) }{ C } \int  X_{n} dP \\
\end{align}
$$

We know $\frac{ log(C) }{ C } \rightarrow 0$ as $C \rightarrow 0$ and $\int  X_{n} dP < \infty$ because $\sup_{n} E(X_{n}) < \infty$. Thus, $\int_{\log(X_{n}) > C}  log(X_{n}) dP \rightarrow 0$ and $\log(X_{n})$ is uniformly integrable from above.


**Is $\log(X_{n})$ necessarily uniformly integrable under the assumed condition $\sup_{n} E(X_{n}) < \infty$? Prove or give a counter example.**

Take $X_{n} = \frac{ 1 }{ n }$. Then $Y_{n} = \log(\frac{ 1 }{n  })$. Then $\sup E(\mid X_{n} \mid) = \sup E(\frac{ 1 }{ n }) = \sup \frac{ 1 }{ n } = 1 < \infty$. However,

$$
\sup E(\mid Y_{n} \mid) = \sup E( \mid \log(\frac{ 1 }{ n }) \mid) = \infty
$$

So, $Y_{n}$ is not uniformly integrable.


# 3
**Let $X_{n}$ be a sequence of random variables. Show that $E(\sup \\{ \mid X_{n} \mid \\}: n \geq 1 \\}) < \infty$ if and only if there exists a nonnegative, integrable random variable $Y$ such that $P( \mid X_{n} \mid \leq Y) = 1$.**

$\Rightarrow$

We want to show that there exists a nonnegative, integrable random variable $Y$ such that $P( \mid X_{n} \mid \leq Y) = 1$ given $E(\sup \\{ \mid X_{n} \mid \\}: n \geq 1 \\}) < \infty$.

Take $Y = \\{ \sup_{n} \mid X_{n} \\}$. Then,

$$
P( \mid X_{n} \mid \leq Y) = P( \mid X_{n} \mid \leq \sup_{n} \mid X_{n} \mid) = 1.
$$

Also 

$$
E(Y) = E(\sup_{n} \mid X_{n} \mid) < \infty ,
$$

so, $Y$ is integrable.

$\Leftarrow$

We want to show that $E(\sup \\{ \mid X_{n} \mid \\}: n \geq 1 \\}) < \infty$ given there exists a nonnegative, integrable random variable $Y$ such that $P( \mid X_{n} \mid \leq Y) = 1$.

$$
E\Big( \sup_{n} \mid X_{n} \mid \Big) = \int \sup_{n} \mid X_{n} \mid dP \leq \int Y dP \leq \infty 
$$

Where the last inequality comes from the fact that $P(\mid X_{n} \mid < Y) = 1$ $\forall n$ $\Rightarrow$ $P(\sup_{n} \mid X_{n} \mid < Y) = 1$.

Thus, $E(\sup \\{ \mid X_{n} \mid \\}: n \geq 1 \\}) < \infty$.

# 4
**Consider the probability space $[0,1]$ with the Borel $\sigma$-field and the Lebesgue measure on it. Define a double sequence of random variables by $X_{n,k}(\omega) n 1\\{ (k-1)/n^{2} \leq \omega \leq k/n^{2} \\}$, $k = 1, \dots , n^2$, $n = 1, 2, \dots$. Show that $\\{ X_{n,k} : k = 1, \dots , n^{2},\ n = 1, 2, \dots$ is uniformly integrable yet is not dominated by any integrable random variable.**

Notice

$$
\sup E(X_{n,k}(\omega)^2) = \sup n^2 \cdot \frac{ 1 }{ n^2 } = 1 < \infty.
$$

Based on the Corollary on slide 129, this is sufficient to say that $X_{n,k}$ is uniformly integrable.

However, notice that $E(\sup \mid X_{n,k} \mid ) = E(\sup X_{n,k}) = n \rightarrow \infty$. Thus, by question 3 there is no random variable that dominates $X_{n,k}$.


# 5
**Let $(a_{1}, \dots a_{n})$ and $(b_{1}, \dots , b_{n})$ be two permutations of $\\{ 1, \dots , n \\}$. Then show that $\sum_{i=1}^{n} a_{i} b_{i} \leq n(n+1)(2n+1) / 6$ with the equality holding if and only if $a_{i} = b_{i}$ for all $i = 1, \dots , n$.**

If $a_{i} = b_{i}$ $\forall n$, then $\sum_{i=1}^{\infty} a_{i} b_{i} = n(n+1)(2n+1) / 6 $.

Notice that $\sum_{i=1}^{n}a_{i} b_{i} = E(\sum_{i=1}^{\infty} a_{i} b_{i})$ with the counting measure. So, by the Cauchy-Schwartz inequality

$$
\sum_{i=1}^{n}a_{i} b_{i} = E(\sum_{i=1}^{\infty} a_{i} b_{i}) \leq \sqrt{ E(\sum_{i=1}^{n} a_{i}^2  E(\sum_{i=1}^{n} b_{i}^2)} = n(n+1)(2n+1) / 6.
$$