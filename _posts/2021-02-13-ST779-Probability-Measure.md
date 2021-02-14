---
layout: post
comments: false
title: Example Problems on Probabilities Measures
description: ST779 Homework 3 on Probabilities Measures
tags: ST779 Measure-Theory Sigma-Algebra Field Probability Measure
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $\Omega$, $\Omega'$ be arbitrary sets and let $f:\Omega \rightarrow \Omega'$ be a function. If $\mathcal C$ is an class of subsets of $\Omega'$, show that $f^{-1}\left( \sigma \langle \mathcal C \rangle \right) = \sigma \langle f^{-1}\left( \mathcal C \right) \rangle$, where for and class $\mathcal S$. $f^{-1}\left( \mathcal S \right) = \left\\{ f^{-1}(S): S \in \mathcal S \right\\}$**



# 2
**Let $\mathcal A$ be a $\sigma$-field on $\Omega$ and $\mathcal C$ be a generator for $\mathcal A$. Show that for every $A \in \mathcal A$, there exists a countable subcollection $\mathcal C_A \subset \mathcal C$ such that $A \in \sigma \langle \mathcal C_A \rangle$.**




# 3
**Let $P$ be a probability measure of $(\Omega, \mathcal A)$. Two sets $A$ and $B$ are called almost disjoint if $P(A \cup B)=0$.**


**Let $A_1, A_2, \dots \in \mathcal A$. Show that $P\left( \bigcup_{i=1}^{\infty} A_i \right) = \sum_{i=1}^{\infty} P(A_i)$ if and only if $A_i$ and $A_j$ are (pairwise) almost disjoint for all $i,j = 1,2, \dots$, $i \neq j$.**



# 4
**Let $\Omega = \mathbb R \times \mathbb R$, $\mathcal B = \left\\{ B \times \mathbb R : B \in \mathcal R \right\\}$, $A = \mathbb R \times C$, where $\mathcal R$ is the Borel $\sigma$-field on $\mathbb R$, $C \subset \mathbb R$. Let $\mathcal F = \sigma \langle \mathcal B \cup \left\\{ A \right\\} \rangle$, $P$ be a probability measure on $(\mathbb R, \mathcal R)$ and $0 < \alpha < 1$. Show that $Q(F) = \alpha P(B_1) + (1-\alpha)P(B_2)$ for $F = (B_1 \times C) \cup (B_2 \times C^C)$ defines a probability measure on $\mathcal F$ and satisfies $Q(B \times \mathbb R) = P(B)$ for all $B \in \mathcal R$.**



# 5
**Let $(\Omega, \mathcal A, P)$ be a probability space and $A_1, \dots , A_n$ be events. Using induction, show that**


$$
P(A_1 \Delta \dots \Delta A_n) = \sum_{i=1}^{n} P(A_i) - 2 \sum_{i<j} P (A_i \cap A_j) + 4 \sum_{i<j<k} P(A_i \cap A_j \cap A_k) + \dots + (-2)^{n-1} P(A_1 \cap \dots \cap A_n),
$$

**where $A\Delta B$ stands for the symmetric difference of $A$ and $B$.**