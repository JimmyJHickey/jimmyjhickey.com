---
layout: post
comments: false
title: Example Problems on Random Variables
description: ST779 Homework 5 on Random Variables
tags: ST779 Measure-Theory Random-Variables
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $X$ be a real-valued random variable. Given any $\epsilon > 0$, show that there exists and an $M>0$ and a random variable $\mid Y \mid \leq M$ and $P(X\neq Y) < \epsilon$.**




# 2
**Let $X:[-1,1] \rightarrow [0,1]$ be a random variable defined be $X(\omega) = \omega^2$ for $- 1 \leq \omega < 0$. and $X(\omega) = \omega^3$ for $0 \leq \omega \leq 1$. Let $P$ be the uniform distribution on $[-1,1]$, i.e. $P(B) = \lambda(B) / 2$, $B$ and Borel subset of $[-1,1]$ and $\lambda$ the Lebesgue measure. Find $P_X([a,b])$, where $[a,b]$ is a Borel subset of $[0,1]$ and $P_X$ is the induced distribution, i.e., $P_X(C) = P(X^{-1}(C))$, $C$ a Borel subset of $[0,1]$.**




# 3
**Let $\Omega$ be a sample space and $\mathcal A$ be a $\sigma$-field on $\Omega$. Let $X$ be a random variable. Show that the induced $\sigma$-field on $\sigma \langle X \rangle = \\{ X^{-1}(B): B\in \mathcal R \\}$ is countably generated.**





# 4
**Let $a<b$ be real numbers. Construct a sequence of continuous functions $f_n: \mathbb R \rightarrow \mathbb R$ such that $f_n(x) \rightarrow \mathbb I_{[a,b]}(x)$ as $n\rightarrow \infty$ for all $x$.**

**What about intervals $(a,b)$ and $(a,b]$?**


# 5
**Let $\mathcal A_n$, $n \geq 1$, be a sequence of $\sigma$-fields on $\Omega$. Show that the $\\{ \mathcal A_n: n = 1, 2, dots \\}$ is mutually independent if and only if for all $n$, $\mathcal A_n$ is indpendent of $\sigma \langle \mathcal A_1, \dots , \mathcal A_{n-1} \rangle$.**

**State in terms of random variables, $\\{ X_n: n = 1, 2, \dots \\}$ is mutually independent if and only if $X_n$ is independent of $\\{ X_k: k = 1, 2, \dots, n-1 \\}$, with the connection $\mathcal A_n = \sigma \langle X_n \rangle$, the $\sigma$-field induced by $X_n$.**