---
layout: post
comments: false
title: Example Problems on Convergence of Random Variables
description: ST779 Homework 10 on Convergence of Random Variables
tags: ST779 Measure-Theory Convergence
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $\Omega$ be a countable sample space with the power set $\mathcal{P}(\Omega)$ as the $\omega$-field on $\Omega$ (that is, all subsets of $\Omega$ are measurable). Let $X_{n}$, $X$ be random variables on $\Omega$, such that $X_{n} \stackrel{ \text{p}}{\rightarrow} X$. Show that $X_{n} \stackrel{ \text{a.s.}}{\rightarrow} X$.**

Take $\widehat{ \omega }$ to be the set of singletons with nonzero probability. Then take $\omega_{i} \in \widehat{ \omega }$. Since $X_{n} \stackrel{ \text{p}}{\rightarrow} X$, we know that $X_{n} (\omega_{i}) \stackrel{ \text{p}}{\rightarrow} X(\omega_{i})$. And we know for $\varepsilon> 0$, $\exists N$ such that for $n > N$,  

$$
P( \mid X_{n}(\omega_{i}) - X(\omega_{i}) \mid > \varepsilon ) < P(\omega_{i}) \leq \sum P(\omega_{i}) = 1.
$$

Now we can use the Borel-Cantelli Lemma. Take $A_{n} = \Big\\{ \omega : \mid X_{n}(\omega) - X(\omega) \mid < \varepsilon \Big\\}$. Then,

$$
P(\limsup A_{n}) = P \Big\{ \omega : \mid X_{n}(\omega) - X(\omega) \mid < \varepsilon \Big\} \rightarrow 0.
$$

Thus, $X_{n} \stackrel{ \text{a.s.}}{\rightarrow} X$.

# 2
**Show that $X_{n} \stackrel{ \text{p}}{\rightarrow} X$ if and only if $E \Big[ \Big( \mid X_{n} - X  \Big) / \Big( 1+\mid X_{n} - X \mid \Big)\Big] \rightarrow 0$.**


Notice that 

$$
\frac{\Big( \mid X_{n} - X \mid \Big)}{ \Big( 1+\mid X_{n} - X \mid \Big)} \leq \mid X_{n} - X  \mid.
$$

$$
\Rightarrow
$$


Assume $P( \mid X_{n} - X \mid ) > \varepsilon) \leq \varepsilon$.  We can break the expected value into two pieces.

$$
\begin{align}
E & \Big[ \frac{ \Big( \mid X_{n} - X  \Big)} { \Big( 1+\mid X_{n} - X \mid \Big)} \Big] \\
    & = E \Big[ \frac{ \Big( \mid X_{n} - X  \Big)}{\Big( 1+\mid X_{n} - X \mid \Big)} \mathbb{I}_{\mid X_{n} - X \mid ) < \varepsilon} \Big] + E \Big[ \frac{ \Big( \mid X_{n} - X  \Big) }{ \Big( 1+\mid X_{n} - X \mid \Big)} \mathbb{I}_{\mid X_{n} - X \mid ) > \varepsilon} \Big] \\
    & \leq E \Big[ \mid X_{n} - X \mid \mathbb{I}_{\mid X_{n} - X \mid ) < \varepsilon}  \Big] + E \Big[ \mathbb{I}_{\mid X_{n} - X \mid ) > \varepsilon}  \Big] \\
        & \leq E \Big[ \varepsilon \mathbb{I}_{\mid X_{n} - X \mid ) < \varepsilon}  \Big] + P(\mid X_{n - X} > \varepsilon) \\
        & = \varepsilon + \varepsilon\\
        & = 2 \varepsilon
\end{align}
$$

Thus, $E \Big[ \Big( \mid X_{n} - X  \Big) / \Big( 1+\mid X_{n} - X \mid \Big)\Big] \rightarrow 0$.



$$
\Leftarrow
$$

Now assume $E \Big[ \Big( \mid X_{n} - X  \Big) / \Big( 1+\mid X_{n} - X \mid \Big)\Big] \rightarrow 0$. Then we know for $\varepsilon> 0$, $\exists N$ such that $n > N$, $E \Big[ \Big( \mid X_{n} - X  \Big) / \Big( 1+\mid X_{n} - X \mid \Big)\Big] \leq \varepsilon^2$. Then, we know

$$
\begin{align}
\frac{ \varepsilon^{2} }{ 1 + \varepsilon } & \geq E \Big[ \frac{  \Big( \mid X_{n} - X  \Big)}{\Big( 1+\mid X_{n} - X \mid \Big)}\Big] \\
    & \geq E \Big[ \frac{ \varepsilon }{ 1 + \varepsilon } \mathbb{I}_{\mid X_[n] - X \mid < \varepsilon} \Big] \\
    & = \frac{ \varepsilon }{ 1 + \varepsilon } P( \mid X_{n} - X \mid > \varepsilon) \\ \\
\Rightarrow \\
P( \mid X_{n} - X \mid > \varepsilon) & \leq \varepsilon.
\end{align}
$$

Thus, $X_{n} \stackrel{ \text{p}}{\rightarrow} X$.

# 3
**Fatou's lemma for convergence in distribution: Let $X_{n}$ be nonnegative random variables converging in distribution to $X$. Then show that $E(X) \leq \liminf_{n \rightarrow \infty} E(X_{n})$.**

Since $X_{n} \stackrel{ \text{d}}{\rightarrow} X$, we know that $P(X_{n} < x) \rightarrow P(X < x)$ pointwise. So we know 

$$
\lim_{n\rightarrow \infty} P(X_{n} < n) = \liminf_{n\rightarrow \infty} P(X_{n} < n) = P(X_{n} < n).
$$


Now we can apply Fatou's Lemma.

$$
E(X) = \int_{0}^{\infty} P(X \leq x) dx = \int_{0}^{\infty} \liminf P(X_{n} < x) dx \leq \liminf \int_{0}^{\infty} P(X_{n} \leq x) dx 
$$

# 4
**Let $X_{n}$ be iid with $E \Big( \mid X_{1} \mid^{p} \Big) < \infty$, $0 < p < \infty$. Show that $n^{-1/p} \max \Big( \mid X_{1} \mid, \dots , \mid X_{n} \mid \Big) \stackrel{ \text{p}}{\rightarrow}0$.**

Take $\varepsilon>0$.


$$
\begin{align}
P & \Bigg(n^{-1/p} \max\Big( \mid X_{1}\mid ,\dots ,\mid X_{n} \mid \Big)\Bigg) > \varepsilon \Bigg) \\
    & = P\Bigg(\max\Big( \mid X_{1}\mid ,\dots ,\mid X_{n} \mid \Big)\Bigg) > n^{1/p}  \varepsilon \Bigg) \\
    & = P\Bigg(\max\Big( \mid X_{1}\mid ,\dots ,\mid X_{n} \mid \Big)^{p} \Bigg) > n \varepsilon^{p} \Bigg) \\
    & = 1 - P\Bigg(\max\Big( \mid X_{1}\mid ,\dots ,\mid X_{n} \mid \Big)^{p} \Bigg) \leq n \varepsilon^{p} \Bigg) \\
    & = 1 - P\Bigg(\mid X_{1} \mid^{p} \leq n \varepsilon^{p} \Bigg)^{n} 
\end{align}
$$

Now we need to show $P\Bigg(\mid X_{1} \mid^{p} \leq n \varepsilon^{p} \Bigg) \rightarrow 1$. We can use Chebyshev's inequality.

$$
P\Bigg(\mid X_{1} \mid^{p} \leq n \varepsilon^{p} \Bigg) = 1 - P\Bigg(\mid X_{1} \mid^{p} > n \varepsilon^{p} \Bigg) \leq 1 - \frac{ E(\mid X_{1} \mid^{p}) }{ n \varepsilon^{p} } \rightarrow 1
$$

Thus, 

$$
n^{-1/p} \max \Big( \mid X_{1} \mid, \dots , \mid X_{n} \mid \Big) = 1 - P\Bigg(\mid X_{1} \mid^{p} \leq n \varepsilon^{p} \Bigg)^{n}   \stackrel{ \text{p}}{\rightarrow} 1 - 1 = 0.
$$

# 5
**Let $X_{1}, X_{2}, \dots$ be iid standard exponential random variables. Show that $\max \Big( X_{1} , \dots X_{n} \Big) - \log(n)$ converges in distribution. Find the limiting distribution as well.**

Take $Y_{n} = \max \Big( X_{1} , \dots X_{n} \Big) - \log(n)$. Then,

$$
\begin{align}
F_{Y_{n}}(y) & = P \Bigg( \max \Big( X_{1} , \dots X_{n} \Big) - \log(n) \leq y \Bigg) \\
    & = P \Bigg( \max \Big( X_{1} , \dots X_{n} \Big) \leq y + \log(n)\Bigg) \\
    & = \prod_{i=1}^{n} P(X_{i} \leq y + \log(n)) \\
    & = \Big( 1 - \exp \Big[ -(y + \log(n)) \Big] \Big)^{n} \\
    & = \Big( 1 - \frac{ 1 }{ n }\exp \Big[ -y \Big] \Big)^{n} \\ \\
\lim_{n\rightarrow \infty} F_{Y_{n}}(y) & = \exp\Big[\exp[-y]\Big]
\end{align}
$$