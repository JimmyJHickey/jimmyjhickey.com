---
layout: post
comments: false
title: Example Problems on Sequences of Random Variables
description: ST779 Homework 6 on Sequences of Random Variables
tags: ST779 Measure-Theory Sequences Random-Variable Probability Measure
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $X_{1}, X_{2}, \dots $, be i.i.d. with $P(X_{1} = 1) = p = 1 - P(X_{1}=-1)$ and $S_{n} \sum_{i=1}^{n} X_{i}$.**

**Is $\\{ S_n = 0 \text{ infinitely often} \\}$ a tail event? Supply arguments.**

**Show that if $p \neq 1/2$, $P(S_{n}=0 \text{ infinitely often}) = 0$. (Hint: Use Stirling's approximation)**

$\\{ S_n = 0 \text{ infinitely often} \\}$ is a tail event. If we remove finitely many $S_n'$ from the, there will still be infinitely many $S_n$'s equal to 0. Thus, it is a tail event.


Notice that $P(S_{n}=0 \text{ infinitely often}) = 0$ only when the number of $X_i$ that equal to 1 is the same as the number equal to 0. 

$$
\begin{align}
P(S_{n} = 0) & = {n \choose n/2} p^{n/2} ( 1-p)^{n/2} \\
    & = \frac{ n! }{ (n/2)!^2 } p^{n/2}(1-p)^{n/2} \\
    & \approx \frac{ \sqrt{ 2 \pi n } n^n e^{-n} }{ \sqrt{ 2 \pi (n/2) } (n/2)^{n/2} e^{-n/2} } p^{n/2} (1-p)^{n/2} \\
    & =\frac{ \sqrt{ 2 \pi n } n^{n} e^{-n} }{ 2 \pi (n/2) (n/2)^{n} e^{-n} } p^{n/2} (1-p)^{n/2} \\
    & = \sqrt{ \frac{ 2 }{ \pi n } } [4 p (1-p)]^{n/2}.
\end{align}
$$

Then for $p \neq 1/2$,

$$
\sum_{i=1}^{\infty} P(S_{n} = 0) = \sum_{i=1}^{n} \sqrt{ \frac{ 2 }{ \pi n } } [4 p (1-p)]^{n/2} \leq \sum_{i=1}^{n} \sqrt{ \frac{ 2 }{ \pi } } [4 p (1-p)]^{n/2} < \infty.
$$

Thus, by the Borel-Cantelli Lemma, $P(S_{n}=0 \text{ infinitely often}) = 0$.

# 2
**Let $A_{n}$ be events such that $P(A_{n}) \rightarrow 0$ and $\\sum_{i=1}^{\infty} P(A_{n} \cap A_{n+1}^{C}) < \infty$. Show that $P(\limsup A_n) = 0$.**

Take $X = \limsup A_{n}$ and $Y = \limsup A_{n}^{C}$. Then,

$$
P(X) = P(X \cap Y) + P(X \cap Y^{C}) \leq P(X \cap Y) + P(Y^{C}).
$$

So if we show $P(X \cap Y) + P(Y^{C}) = 0$ then $P(X) = 0$.

Let's start by showing $P(X \cap Y)$. Notice that by the Borel-Cantelli Lemma, since $\sum_{i=1}^{\infty} A_{n} \cap A_{n+1}^C < \infty$, then $P(A_{n} \cap A_{n+1}^{C} \text{ i.o.}) = 0$.

For sake of contradiction, assume that $P(X \cap Y) \neq 0$. Then both $P(A_{n} \text{ i.o.}) \neq 0$ and $P(A_{n}^C \text{ i.o.}) \neq 0$. However, then $P(A_{n} \cap A_{n+1}^{C} \text{ i.o.}) \neq 0$. Thus, $P(X \cap Y) = 0$.

Now we will show that $P(Y^{C}) = 0$.

$$
P(Y^{C}) = \lim_{n\rightarrow \infty} P(\bigcup_{m=n}^{\infty} A_{m}) \leq \lim_{n\rightarrow \infty} P(A_{n}) \rightarrow 0
$$

Thus,

$$
P(X) \leq P(X \cap Y) + P(Y^{C}) \rightarrow 0
$$

so $P(\limsup A_{n}) = 0$.


# 3
**Let $X_{1}, X_{2}, \dots $ be independent with common distribution $P(X \leq x) = 1-e^{-x^{\alpha}}$, $x \geq 0$ for some $\alpha > 0$ (Weibull distribution). Show that with probability 1, $\limsup [X_n / log(n)^{1/\alpha}] =1$.**

Take $\varepsilon > 0$ and 

$$
A_{n} = \Big\{ \frac{ X_{n} }{ \log(n) } > 1 + \varepsilon \Big\} \text{ and } B_{n} = \Big\{ \frac{ X_{n} }{ \log(n) } > 1 - \varepsilon \Big\}.
$$

To show $\limsup [X_n / log(n)^{1/\alpha}] =1$ with probability 1, we need to show that $P(\limsup A_{n} ) = 0$ and $P(\limsup B_{n}) = 1$.


$$
\begin{align}
P(A_{n}) & = 1 - \Bigg( 1 - \exp \Big\{ \bigg[ -(1 + \varepsilon) \log(n)^{1/\alpha} \bigg]^\alpha \Big\} \Bigg) \\
    & = \exp \Big\{ -(1+\varepsilon)^\alpha \log(n) \Big\} \\
    & = \exp \Big\{ \log(n^{-(1+\varepsilon)^{\alpha}}) \Big\} \\
    & = n^{-(1+\varepsilon)^{\alpha}}
\end{align}
$$

Then,

$$
\sum_{i=1}^{\infty} P(A_{n}) = \sum_{i=1}^{\infty} n^{-[(1+ \varepsilon)^{\alpha}]} < \infty
$$
 
because $1 + \varepsilon > 1$. By the Borel-Cantelli Lemma $P(\limsup A_{n} ) = 0$.

Similary,

$$
\sum_{i=1}^{\infty} P(B_{n}) = \sum_{i=1}^{\infty} n^{-[(1+-\varepsilon)^{\alpha}]} = \infty
$$

because $1 + \varepsilon < 1$. By the Borel-Cantelli Lemma $P(\limsup B_{n}) = 1$.

Thus, $\limsup [X_n / log(n)^{1/\alpha}] =1$.



# 4
**For a sequence of numbers $\\{ a_n \\}$, the radius of convergence of the power series $\sum_{i=1}^{\infty} a_{n} z^{n}$ is the largest number $r$ such that for any $\mid z \mid < r$, the series $\sum_{i=1}^{\infty} a_{n} z^{n}$ is absolutely convergent. It is known that if the series absolutely converges for some $z$ with $\mid z \mid = c$, then it also converges for nay $w$ with $\mid w \mid < c$. If the series for all $z$ we say that $r = \infty$. If the series does not converge for an $z \neq 0$, we say that $r = 0$.**

**Now if $\\{ X_{n} \\}$ is a sequence of independent random variables, then show that the radius of convergence of the random series $\sum_{i=1}^{\infty} X_{n} z^{n}$ is a degenerate random variable (possibly infinite valued).**


Take $R$ to be the random variable that describes the radius of convergence. Also notice that convergence is a tail event. Then by Kolmogorov's zero-one law, since $X_{1}, X_{2}, \dots$ are independent all tail events are P-trivial. So, $R$ is a P-trivial event and $P(R = r_0) = 1$ for some $r_0$.


# 5
**Suppose that $X_{n}$, $n = 1, 2, \dots$ are nonneative integrable random variables such that the sequence $\\{ E(X_{n}) \\}$ is bounded and $X_{n} \uparrow X$ for some random variable $X$. Show that $X$ is also integrable and $E(X) = \lim_{n\rightarrow \infty} E(X_n)$.**

Since $X_n \geq 0$ and $X_{n} \uparrow X$, by the Monotone Convergence Theorem, $E(X_{n}) \uparrow E(X)$.

To show that $X$ is integrable, we have to show that $E(X^{-}), E(X^{+}) < \infty$. 

Since $0 \leq X_{n} \leq X$, then $X^{-} = 0$. Thus, $E(X^{-}) = 0 < \infty$.

Since $E(X_{n}^{+})$ is bounded and integrable, $\lim_{n\rightarrow \infty} E(X_{n}^{+} = E(X^{+}) = E(X) < \infty$.

Thus, $X$ is integrable.
