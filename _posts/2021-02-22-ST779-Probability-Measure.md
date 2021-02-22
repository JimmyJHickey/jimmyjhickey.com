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



# 2
**Let $\Omega$ be a set and $\mathcal A$ be a $\sigma$-field on it. $P: \mathcal A\rightarrow [0,1]$ with $P(\Omega) = 1$ be finitely additive and satisfy the following property: For all $A_1, A_2, \dot , \in \mathcal A$ disjoint such that $\bigcup_{n=1}^\infty A_n = \Omega$, we have that $\sum_{n=1}^\infty P(A_n) = 1$. Then show that $P$ is a (countable additive) probability measure on $(\Omega, \mathcal A)$.**


# 3
**Let $P$ be countable additive on a semifield $\mathcal C$ on $\Omega$ (i.e. whenever $C_n \in \mathcal C$ disjoint and $\bigcup_{n=1}^\infty C_n \in \mathcal C$, we have $P\left( \bigcup_{n=1}^\infty C_n \right) = \sum_{n=1}^\infty P(C_n)$.) Condisere that Caratheodory extension**

$$
P^*(A) = \inf \left\{ \sum_{i=1}^\infty P(C_i): C_1, C_2, \dots \in \mathcal C, A \in \bigcup_{i=1}^\infty C_i, \right\}
$$

**for any $A \subset \Omega$. Show that there exists $B \in \sigma \langle \mathcal C \rangle$ containing $A$ such that $P^\*(A) = P^\*(B)$.**



# 4
**Let $A$ be a Borel subset of $[0,1]$ such that its Lebsegue measure $0 < \lambda(A) < 1$. Let $0 < \alpha < 1$. Show that there exists a Borel subset $B$ of $A$ such that $\lambda(B) = \alpha \lambda(A)$.**




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