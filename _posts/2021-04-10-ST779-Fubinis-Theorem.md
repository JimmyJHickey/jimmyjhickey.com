---
layout: post
comments: false
title: Example Problems on Fubini's Theorem
description: ST779 Homework 9 on Fubini's Theorem
tags: ST779 Measure-Theory Fubini's -heorem Random-Variables
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $p_{1}, \dots , p_{k} > 1$, be such that $\sum_{j=1}^{k} p_{j}^{-1} = 1$. Let $X_{j}$, $j=1, \dots , k$, be random variables such that $\lVert X_{j} \rVert_{p_{j}} := \Big( E \mid X_{j}\mid^{p_{j}} \Big)^{1/p_{j}} < 
\infty$. Then show that $E \Big[ \prod_{j=1}^{k} \mid X_{j} \mid \Big] \leq \prod_{j=1}^{k} \lVert X_{j} \rVert_{p_{j}}$.**

We will follow the proof of Holder's inequality.

Notice that by the concavity of $\log$

$$
\log \Big( \frac{ a_{1}^{p_{1}} }{ p_{1} } + \dots + \frac{ a_{k}^{p_{k}} }{ p_{k} } \Big) \geq p_{1}^{-1} \log(a_{1}^{p_{1}}) + \dots + p_{k}^{-1} \log(a_{k}^{p_{k}}) = \log(a_{1} + \dots + a_{k}) = \log(a_{1} \cdot \dots \cdot a_{k})
$$

Now take $a_{i} = \frac{ \mid X_{i} \mid }{ E[ \mid X_{i} \mid^{p_{i}}]^{1/p_{i}} }$


$$
\begin{align}
\frac{ \mid X_{1} \mid \cdot \dots \cdot \mid X_{k} \mid }{E[ \mid X_{1} \mid^{p_{1}}]^{1/p_{1}} \cdot \dots \cdot E[ \mid X_{k} \mid^{p_{k}}]^{1/p_{k}} }
    & \leq \frac{ \mid X_{1} \mid }{ E[ \mid X_{1} \mid^{p_{1}}]^{1/p_{1}} } + \dots + \frac{ \mid X_{k} \mid }{ E[ \mid X_{k} \mid^{p_{k}}]^{1/p_{k}} } \\
\frac{ E [\mid X_{1} \mid \cdot \dots \cdot \mid X_{k} \mid] }{E[ \mid X_{1} \mid^{p_{1}}]^{1/p_{1}} \cdot \dots \cdot E[ \mid X_{k} \mid^{p_{k}}]^{1/p_{k}} }
    & \leq \frac{ 1 }{ p_{1} } + \dots + \frac{ 1 }{ p_{k} } \\
    & = 1 \\
\Rightarrow \\
E[ \mid X_{1} \cdot \dots \cdot X_{k} \mid] & \leq E[ \mid X_{1}^{p_{1}} \mid ]^{1/p_{1}} \cdot \dots \cdot E[ \mid X_{k}^{p_{k}} \mid ]^{1/p_{k}}
\end{align}
$$

# 2
**Let $X$ and $Y$ be independent random variables, $p \geq 1$, and $E(Y) = 0$. Show that for any $x$, $E \mid Y + x \mid^{p} \geq \mid x \mid^{p}$.**

This follows from Jensen's inequality.

$$
E[ \mid Y + x \mid^{p}] \geq \mid E(Y) + x \mid^{P} = \mid x \mid^{p}
$$


**Show that for $E \mid X \mid^{p} \leq E \mid X+Y \mid^{p}$.**

Notice that $E(Y \mid X) = E(Y) = 0$. By Jensen's inequality, we know that

$$
\mid X \mid^{p} = \mid X + E(Y \mid X) \mid^{p} = \mid E(X + Y \mid X) \mid^{p} \leq E( \mid X+Y \mid^{p} \mid X).
$$


Then by the law of total expectation,

$$
E(\mid X \mid^{p}) \leq E\Big( E( \mid X + Y \mid^{p} \mid X)\Big) = E( \mid X+Y \mid^{p}).
$$

# 3
**Show that $\int_{0}^{\infty} e^{-x^{2}/2} dx = \sqrt{ \pi / 2 }$.**

Equivalently, we will show that

$$
\begin{align}
\Big[ \int_{0}^{\infty} & e^{-x^{2}/2} dx \Big]^2 \\
    & = \int_{0}^{\infty} e^{-x^{2}/2} dx \cdot \int_{0}^{\infty} e^{-y^{2}/2} dy \\
    & = \int_{0}^{\infty}\int_{0}^{\infty} e^{-x^{2}/2} e^{-y^{2}/2} dx dy \\
    & = \int_{0}^{\infty}\int_{0}^{\infty} e^{-\frac{ x^{2}+y^{2} }{ 2 }} dx dy \\
    & = \frac{ \pi }{ 2 }
\end{align}
$$

We will perform the polar transformation.

$$
\begin{align}
\int_{0}^{\infty}\int_{0}^{\infty} & e^{-\frac{ x^{2}+y^{2} }{ 2 }} dx dy\\
    & = \int_{0}^{\pi / 2} \int_{0}^{\infty} e^{-R^{2}/2} R dR d\theta \\
    & = \frac{ \pi }{ 2 }\int_{0}^{\infty} e^{-R^{2}/2} R dR & \text{Fubini's Theorem} \\
    & = \frac{ \pi }{ 2 } \int_{0}^{\infty} e^{-u} R \frac{ du }{ R } & u = \frac{ R^{2} }{ 2 } \\
    & = \frac{ \pi }{ 2 } \Big[ -e^{-\infty} - -e^{-0} \Big] \\
    & = \frac{ \pi }{ 2 }
\end{align}
$$



# 4
**If $X$ is a positive random variable and $\alpha > 0$, show that**

$$
E(X^{\alpha}) = \alpha \int_{[0, \infty)} x^{\alpha-1}P(X > x) dx,
$$

**where $dx$ in the right hand side stands for integration with respect to the Lebesgue measure.**

We can write 

$$
X = \int_{0}^{X} dx = \int_{0}^{\infty} 1(y < x(\omega)) dy.
$$

Then,

$$
E(X) = \int_{\Omega} \int_{0}^{\infty} 1(y < X(\omega)) dy d\omega =  \int_{0}^{\infty} \int_{\Omega} 1(y < X(\omega))  d\omega dy = \int_{0}^{\infty} P(y < X) dy.
$$

Where the change in order of integration comes from Fubini's Theorem. Also notice we can write

$$
X^{\alpha} = \alpha \int_{0}^{X} z^{\alpha-1} dz = \int \alpha x^{\alpha - 1} 1(x < X(\omega)) dx.
$$

Then, finally

$$
E(X^{\alpha}) = \int_{\Omega} \int_{0}^{\infty} \alpha 1(x^{\alpha-1} < X(\omega)) dx d \omega = \alpha \int_{0}^{\infty} x^{\alpha-1}P(X > x) dx
$$


# 5
**For a Borel measurable integration function $f$ on $\mathbb{R}$, show that**

$$
\int \int f(x-y)f(y) dy dx \geq 0.
$$

We can use Fubini's theorem to swap the order of integration.

$$
\int \int f(x-y)f(y) dy dx = \int f(y) \Big[ \int f(x-y) dx \Big] dy
$$

Since we are integrating over all the reals, we can re-write the inner integral (notice that the shift will not change the value).

$$
\int f(y) \Big[ \int f(x-y) dx \Big] dy = \int f(y) \Big[ \int f(z) dz \Big] dy = \int f(y) dy \cdot \int f(y) dy = \Big[ \int f(y) dy \Big]^{2} \geq 0
$$