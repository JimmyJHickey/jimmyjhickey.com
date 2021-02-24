---
layout: post
comments: false
title: Example Problems on Probability Measures
description: ST779 Homework 4 on Probability Measures
tags: ST779 Measure-Theory Sigma-Algebra Field Probability Measure
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}


# 1
**Let $\Omega$ be a set of $\mathcal F$ be a field on it. A function $P: \mathcal F \rightarrow [0,1]$ with $P(\Omega) = 1$ is called finitely additive on $\mathcal F$ for any $A_1, \dots , A_n \in \mathcal F$ disjoint, $n \geq 1$, $P \left( \cup_{i=1}^n A_i \right) = \sum_{i=1}^n P(A_i)$.**

**If $P_n$, $n = 1, 2, \dots $, are probability measures on $\Omega, \mathcal A$ and $\mathcal F$ is a field on $\Omega$, $\mathcal F \subset \mathcal A$, such that for all $A \in \mathcal F$, $P_n(A)$ converges to a limit, to be called $P(A)$, then show $P:\mathcal F\rightarrow [0,1]$ is finitely additive.**


**Is $P$ also countable additive? Prove or give a counterexample.**


We can show finite additivity.

$$
\begin{align}
P\left(\bigcup_{i=1}^m A_i \right) & = \lim_{n \rightarrow \infty}\left[  P_n \left( \bigcup_{i=1}^m A_i \right)\right] \\
	& = \lim_{n \rightarrow \infty} \left[ \sum_{i=1}^m P_n(A_i) \right] & \text{Finite additivity of } P \\
	& = \sum_{i=1}^m \lim_{n \rightarrow \infty} P_n(A_i) \\
	& = \sum_{i=1}^m P(A_i)
\end{align}
$$



However, we do not have infinite additivity. For example, take $\Omega = \overline{ \mathbb R }$ and $\overline{ \mathcal A }$. Let's look at the interval $[-n,n]$. Take $A_1, \dots, A_{2n}$ to be a partition over $[-n,n]$ where each $A_i$ has length $\frac{ 1 }{ 2n }$. Looking at the finite case,

$$
1 = P \left( \bigcup_{i=1}^{2n} A_i \right) = \sum_{i=1}^{2n} P(A_i) = \sum_{i=1}^{2n}\frac{ 1 }{ 2n } = 1.
$$


However, if we take $n \rightarrow \infty$, notice that the length of each $A_i \rightarrow 0$, but their union covers the all of $\Omega$.

$$
\sum_{i=1}^\infty P(A_i) = \sum_{i=1}^\infty 0 = 0 \neq 1 = P(\Omega) = P\left( \bigcup_{i=1}^\infty A_i \right)
$$



# 2
**Let $\Omega$ be a set and $\mathcal A$ be a $\sigma$-field on it. $P: \mathcal A\rightarrow [0,1]$ with $P(\Omega) = 1$ be finitely additive and satisfy the following property: For all $A_1, A_2, \dot , \in \mathcal A$ disjoint such that $\bigcup_{n=1}^\infty A_n = \Omega$, we have that $\sum_{n=1}^\infty P(A_n) = 1$. Then show that $P$ is a (countable additive) probability measure on $(\Omega, \mathcal A)$.**

We need to show that $P$ is countably additive. Take $B_1, B_2, \dots \in \mathcal A$ to be disjoint sets. Then $\Omega \setminus \left( \bigcup_{i=1}^\infty B_i\right)$ is disjoint from all $B_i$ and

$$
\bigcup_{i=1}^\infty B_i \cup \left( \Omega \setminus \left( \bigcup_{i=1}^\infty B_i\right) \right) = \Omega.
$$


Then,

$$
\begin{align}
1 & = P(\Omega) \\
	& = P\left(\bigcup_{i=1}^\infty B_i \cup \left( \Omega \setminus \left( \bigcup_{i=1}^\infty B_i\right) \right)\right) \\
	& = \sum_{j=1}^\infty \left[ P\left(B_j \right) + P\left( \Omega \setminus \left( \bigcup_{i=1}^\infty B_i\right) \right)\right] \\
	& = \sum_{j=1}^\infty \left[P(B_j) \right] + P\left(\Omega \setminus \left( \bigcup_{i=1}^\infty B_i\right)\right) \\
\sum_{j=1}^\infty P(B_j) & = 1 - P\left(\Omega \setminus \left( \bigcup_{i=1}^\infty B_i\right)\right) \\
	& = 1 - \left( P(\Omega) - P\left(\bigcup_{i=1}^\infty B_i\right) \right) \\
	& = P\left(\bigcup_{i=1}^\infty B_i\right)
\end{align}
$$




# 3
**Let $P$ be countable additive on a semifield $\mathcal C$ on $\Omega$ (i.e. whenever $C_n \in \mathcal C$ disjoint and $\bigcup_{n=1}^\infty C_n \in \mathcal C$, we have $P\left( \bigcup_{n=1}^\infty C_n \right) = \sum_{n=1}^\infty P(C_n)$.) Condisere that Caratheodory extension**

$$
P^*(A) = \inf \left\{ \sum_{i=1}^\infty P(C_i): C_1, C_2, \dots \in \mathcal C, A \in \bigcup_{i=1}^\infty C_i, \right\}
$$

**for any $A \subset \Omega$. Show that there exists $B \in \sigma \langle \mathcal C \rangle$ containing $A$ such that $P^\*(A) = P^\*(B)$.**


By the definition of infimum

$$
\sum_{i=1}^\infty P(C_{i,k}) < P^*(A) + 1/k.
$$

Then $\forall k$, $A \subset \bigcup_{i=1}^\infty C_{i,k}$. And define $B$

$$
A \subset \bigcap_{k=1}^\infty \left( \bigcup_{i=1}^\infty C_{i,k} \right) = B \Rightarrow P^*(A) < P^*(B).
$$

But also $B \in \sigma \langle \mathcal C  \rangle$ and $B = \bigcup_{k=1}^\infty B_k$. Then,

$$
P^*(B) \leq P^*(B_k) \leq \sum_{i=1}^\infty P(C_{i,k}) < P^*(A) + 1/k, k > 0.
$$


Thus, $P^\*(A) = P^\*(B)$.


# 4
**Let $A$ be a Borel subset of $[0,1]$ such that its Lebsegue measure $0 < \lambda(A) < 1$. Let $0 < \alpha < 1$. Show that there exists a Borel subset $B$ of $A$ such that $\lambda(B) = \alpha \lambda(A)$.**


Notice that for a measure $\mu$ and $ S \subset T$,

$$
\begin{align}
T & = (T \setminus S) \cup (T \cap S) \\
	& = (T \setminus S) \cup S \\
\mu(T) & = \mu(T \setminus S) \cup \mu(S) \\
\mu(T \setminus S) = \mu(T) - \mu(S).
\end{align}
$$

Recall the intermediate value theorem, that is for a continuous function $f(x)$ on $[a,b]$ with minimum and maximum $\min$ and $\max$. Then $\forall l$ such that $\min < l < \max$, $\exists c $ such that $f(c) = l$.

In this case $a = 0$ and $b=1$ and $f(x) = \lambda \left( A \cap [0,x] \right)$. And our min and max are

$$
\begin{align}
f(0) & = \lambda \left( A \cap 0\right) = \begin{cases}
\lambda(0) \\
\lambda(\varnothing)
\end{cases} = 0 \\
f(1) & = \lambda \left( A \cap [0,1] \right) = \lambda \left( A \right)
\end{align}
$$

Now we need to show that $f(x)$ is continuous. That is, $\forall \epsilon > 0$ $\exists \delta$ such that $\mid x - y \mid < \delta \Rightarrow \mid f(x) - f(y) \mid < \epsilon$. Without loss of generality, take $y \geq x$ so $A \cap [0,y] \subset A \cap [0,y]$.

$$
\begin{align}
f(x) - f(y) & = \lambda\left( A \cap [0,x] \right) - \lambda \left( A \cap [0,y]\right) \\
	& = \lambda \left(  \left( A \cap [0,x] \right) \setminus \left( A \cap [0,y] \right) \right) \\
	& = \lambda \left(  \left( A \cap [0,x] \right) \cap \left( A \cap [0,y] \right)^C \right) \\
	& = \lambda \left(  \left( A \cap [0,x] \right) \cap \left( A^C \cup (y, 1] \right) \right) \\
	& = \lambda \left(  \left( A \cap [0,x] \cap A^C \right) \cup \left( A \cap [0,x] \cap (y, 1] \right) \right) \\
	& = \lambda \left(  \left( \varnothing \right) \cup \left( A \cap [0,x] \cap (y, 1] \right) \right) \\
	& = \lambda \left(  A \cap [0,x] \cap (y, 1] \right) \\
	& < \epsilon
\end{align}
$$

Then take $l = \alpha \lambda(A)$. By the intermediate value theorem $\exists z$ such that

$$
f(z) = l = \alpha \lambda(A) = \lambda(\underbrace{A \cap [0,z]}_{B}).
$$

Then $B \subset A$ and is a Borel subset.

# 5
**Let $\alpha > 0$. For $\delta > 0$ and $ A \in \mathbb R$, let**

$$
H_\delta^\alpha(A) = \inf \left\{ \sum_{n=1}^\infty \mid I_n \mid^\alpha: \cup_{n=1}^\infty I_n \supset A, I_n \text{ are intervals of length } \mid I_n \mid < \delta \right\}.
$$

**Note that $H_\delta^\alpha(A)$ increases as $\delta \downarrow 0$. Define $H^\alpha(A) = \lim_{\delta\rightarrow 0} H_\delta^\alpha(A)$, called the $\alpha$-Hausdorff outer measure of $A$. It can be shown, using the Caratheodory extension theorem that this is a measure on the Borel $\sigma$-field $\mathcal R$. Note that $H^1$ is the Lebesgue measure.**

**Note the following: if $H^\alpha(A) = \infty$ and $\beta < \alpha$, then $H^\beta(A) = \infty$. Define the Hausdorff dimension of a Borel $A$ set by**

$$
\text{Hdim}(A) = \inf \left\{ \alpha > 0: H^\alpha(A) < \infty \right\} = \sup \left\{ \alpha >0 : H^\alpha(A) = \infty \right\}.
$$

**Show that the Hausdorff dimension of the Cantor set $C$ is $\log(2) / \log(3)$.**



Recall that $C = \bigcap_{n=1}^\infty C_n$ and that $C_n$ has $2^n$ disjoint elements each of length $(1/3)^n$ with $\lambda(C_n) = (2/3)^n$. We want to take a small $\delta = (1/3)^n + \epsilon$ for $\epsilon > 0$. Then we can take each $I_m$ to be one of the elements of $C_n$. Then,

$$
\sum_{m=1}^{2^n}\mid I_m \mid ^\alpha = \sum_{m=1}^{2^n} (1/3)^{n\alpha} = \left( \frac{ 2 }{ 3^\alpha } \right)^n.
$$

This holds for all $\alpha$, so take $\alpha = 0.001$ Then,

$$
\left(\frac{ 2 }{ 3^\alpha } \right)^n \approx 2^n.
$$

And since $C = \bigcap_{n=1}^\infty C_n$ we know $C \subset C_n$ $\forall n$ and $H^\alpha(C) < H^\alpha(C_n)$. Now we can take the limit of $n$.

$$
\lim_{n\rightarrow \infty} 2^n \rightarrow \infty
$$

And if we take $\alpha$ large, such as $\alpha = 1$

$$
\lim_{n \rightarrow \infty} (2/3)^n \rightarrow 0.
$$

We want to find $\alpha$ such that $H^\alpha(C) = 1$.

$$
2/3^\alpha = 1 \rightarrow \alpha = \frac{ \log(2) }{ \log(3) }
$$