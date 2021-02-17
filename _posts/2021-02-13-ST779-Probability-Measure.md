---
layout: post
comments: false
title: Example Problems on Probability Measures
description: ST779 Homework 3 on Probability Measures
tags: ST779 Measure-Theory Sigma-Algebra Field Probability Measure
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $\Omega$, $\Omega'$ be arbitrary sets and let $f:\Omega \rightarrow \Omega'$ be a function. If $\mathcal C$ is any class of subsets of $\Omega'$, show that $f^{-1}\left( \sigma \langle \mathcal C \rangle \right) = \sigma \langle f^{-1}\left( \mathcal C \right) \rangle$, where for and class $\mathcal S$. $f^{-1}\left( \mathcal S \right) = \left\\{ f^{-1}(S): S \in \mathcal S \right\\}$**

We want to show 

1. $f^{-1}\left( \sigma \langle \mathcal C \rangle \right) \subset \sigma \langle f^{-1}\left( \mathcal C \right) \rangle$
2. $f^{-1}\left( \sigma \langle \mathcal C \rangle \right) \supset \sigma \langle f^{-1}\left( \mathcal C \right) \rangle$


__1__

We can proceed with the Good Sets Principle. For $A \in \mathcal A$ we want to show that $f^{-1}(A) \in \underbrace{\sigma \langle f^{-1}(\mathcal C) \rangle}_\mathcal B$. The our good sets are

$$
\mathcal G = \left\{ A \in \mathcal A : f^{-1}(A) \in \mathcal B \right\}.
$$


1. We know that $\mathcal C$ is a generator for $\mathcal A$. 

2. $\mathcal C \in \mathcal G$ then $\forall C \in \mathcal C$, $f^{-1}(C) \in f^{-1}(\mathcal C) \subset \mathcal B$.

3. Finally we need to show that $\mathcal G$ is a $\sigma$-field.

(i) Since $\varnothing, \Omega' \in \mathcal A$, $f^{-1}(\varnothing) = \varnothing \in \mathcal B$ and $f^{-1}(\Omega') = \Omega \in \mathcal B$. Thus, $\varnothing, \Omega' \in \mathcal G$.

(ii) Take $A_1, A_2, \dots \in \mathcal G$. Since $\mathcal A$ is a $\sigma$-field, $\bigcup_{i=1}^{\infty} A_i \in \mathcal A$. Then $f^{-1}(A_1) , f^{-1}(A_n), \dots \in \mathcal B$ by definition. Since $\mathcal B$ is a $\sigma$-field 

$$
f^{-1} \left( \bigcup_{i=1}^{\infty} A_i \right) \in \mathcal B.
$$

And  since the inverse map commutes over countable set operations,

$$
f^{-1} \left( \bigcup_{i=1}^{\infty} A_i \right) =\bigcup_{i=1}^{\infty} f^{-1} \left(  A_i \right)
$$

Thus, $\bigcup_{i=1}^{\infty} A_i \in \mathcal G$. 

(iii) Finally, for any $A \in \mathcal G$, by definition $f^{-1}(A) \in \mathcal B$. Then, since $\mathcal B$ is a $\sigma$-field $f^{-1}(A)^C \in \mathcal B$. Again, since inverse map commutes over set operations

$$
f^{-1}(A)^C = f^{-1}(A^C) \in \mathcal B.
$$


Hence

$$
f^{-1}\left( \sigma \langle \mathcal C \rangle \right) \subset \sigma \langle f^{-1}\left( \mathcal C \right) \rangle
$$

__2__

First we will show that $f^{-1}\left( \sigma \langle \mathcal C \rangle \right) = \mathcal F^{-1}$ is a $\sigma$-field on $\Omega$. 

(i) $\varnothing, \Omega' \in \sigma \langle \mathcal C \rangle$ then, $f^{-1}(\varnothing) = \varnothing \in \mathcal F^{-1}$ and $f^{-1}(\Omega') = \Omega \in \mathcal F^{-1}$


(ii) For $C_1, C_2, \dots \in \sigma \langle \mathcal C \rangle$ we know $\bigcup_{i=1}^{\infty} C_i \in \sigma \langle \mathcal C \rangle$ since it is a $\sigma$-field. Then, $f^{-1}(C_1), f^{-1}(C_2), \dots \in \mathcal F^{-1}$ and $f^{-1}\left( \bigcup_{i=1}^{\infty} C_i \right) \in \mathcal F^{-1}$. Since the inverse map commutes over countable set operations, 

$$
f^{-1}\left( \bigcup_{i=1}^{\infty} C_i \right) = \bigcup_{i=1}^{\infty} f^{-1} C_i \in \mathcal F^{-1}.
$$


(iii) Take $C \in \sigma \langle \mathcal C \rangle$, since it's a $\sigma$-field $C^C \in \sigma \langle \mathcal C \rangle$. Then $f^{-1}(C), f^{-1}(C^C) \in \mathcal F^{-1}$. Again, since the inverse map commutes over set operations $f^{-1}(C)^C \in \mathcal F^{-1}$.

Now take $g : S\rightarrow T$ with $A, B \in T$ and $A \subset B$. We want to show that $g^{-1}(A) \subset g^{-1}(B)$. By definition

$$
g^{-1}(A) = \left\{ x \in A : f(x) \in A \right\} \subset \left\{ x \in S : f(x) \in B \right\} = f^{-1}(B).
$$


Thus for $\mathcal C \subset \sigma \langle \mathcal C \rangle$ we have $f^{-1} \left( \mathcal C \right) \subset f^{-1} \left( \sigma \langle \mathcal C \rangle \right)$. Then 

$$
\sigma \langle f^{-1}(\mathcal C) \rangle \subset \sigma \langle f^{-1}(\sigma \langle \mathcal C \rangle) \rangle = f^{-1}\left( \sigma \langle \mathcal C \rangle \right)
$$


# 2
**Let $\mathcal A$ be a $\sigma$-field on $\Omega$ and $\mathcal C$ be a generator for $\mathcal A$. Show that for every $A \in \mathcal A$, there exists a countable subcollection $\mathcal C_A \subset \mathcal C$ such that $A \in \sigma \langle \mathcal C_A \rangle$.**

We can proceed with the Good Sets Principle. Take our good set as

$$
\mathcal G = \left\{ A \in \mathcal A: \exists \mathcal C_A \subset \mathcal C \text{ with } A \in \sigma \langle \mathcal C_A \rangle \text{ and } \mathcal C_A \text{ countable} \right\}
$$


1. By definition, $\mathcal C$ is a generator. ✅

2. Take $A \in \mathcal C$ and $\mathcal C_A = \left\\{ A \right\\}$. This satisfies all requirements and $\mathcal C \subset \mathcal G$. ✅

3. Finally we need to show that $\mathcal G$ is a $\sigma$-field. 

(i) Since $A \in \sigma \langle \mathcal C_A \rangle$, we know that $\varnothing, \Omega \in \mathcal G$.

(ii) For $A_1, A_2, \dots \in \mathcal G$ we know that $\mathcal C_{A_n} \subset \mathcal C$ is countable and $A_n \in \sigma \langle \mathcal C_{A_n} \rangle$. Thus, $\bigcup_{i=1}^{\infty} \mathcal C_{A_n} \subset \mathcal C$. This is countable and $A_n \in \sigma \langle A_n \rangle \subset \sigma \langle \bigcup_{m=1}^{\infty} A_m  \rangle$. 

(iii) Finally, if $A \in \sigma \langle \mathcal C_A \rangle$ then $A^C \in \sigma \langle C_A \rangle$ since $\sigma \langle \mathcal C_A \rangle$ is a $\sigma$-field. ✅


# 3
**Let $P$ be a probability measure of $(\Omega, \mathcal A)$. Two sets $A$ and $B$ are called almost disjoint if $P(A \cap B)=0$.**


**Let $A_1, A_2, \dots \in \mathcal A$. Show that $P\left( \bigcup_{i=1}^{\infty} A_i \right) = \sum_{i=1}^{\infty} P(A_i)$ if and only if $A_i$ and $A_j$ are (pairwise) almost disjoint for all $i,j = 1,2, \dots$, $i \neq j$.**


First notice that for any sets $A$ and $B$ you can write $A$ as the union of disjoint sets $A = (A \cap B^C) \cup ( A \cap B)$. Thus,

$$
P(A) = P(A \setminus B) + P(A \cap B) \Rightarrow P(A\setminus B) = P(A) - P(A\cap B).
$$

Now define disjoint sets $D_n = A_n \setminus \left( \bigcup_{i=1}^{n-1} A_i \right)$. 

$$
\begin{align}
P\left(\bigcup_{i=1}^{\infty} A_i\right) & = P \left( \bigcup_{i=1}^{\infty} D_i \right)\\
    & = \sum_{i=1}^{\infty} P(D_i) \\
    & = P \left(\bigcup_{i=1}^{\infty}  A_i \setminus \left( \bigcup_{j=1}^{n-1} A_j  \right) \right) \\   
    & = \sum_{i=1}^{\infty} P\left(A_i\right) - \sum_{i=1}^{\infty} P\left( A_i \cap \left( \bigcup_{j=1}^{i-1} A_j \right) \right)
\end{align}
$$


Notice that $P(\bigcup_{i=1}^{\infty} A_i) = \sum_{i=1}^{\infty} P(A_i)$ if and only if $\sum_{i=1}^{\infty} P\left( A_i \cap \left( \bigcup_{j=1}^{i-1} A_j \right) \right)=0$. We can use our distributive rule to say

$$
\begin{align}
\sum_{i=1}^{\infty} P\left( A_i \cap \left( \bigcup_{j=1}^{i-1} A_j \right) \right) & = \sum_{i=1}^{\infty} P\left( \bigcup_{j=1}^{i-1} \left( A_i \cap A_j \right) \right) \\
    & \leq \sum_{i=1}^{\infty} \sum_{j=1}^{i-1} P(A_i \cap A_j).
\end{align}
$$

However, this is 0 if and only if $P(A_i \cap A_j) = 0$ for all $i \neq j$.

# 4
**Let $\Omega = \mathbb R \times \mathbb R$, $\mathcal B = \left\\{ B \times \mathbb R : B \in \mathcal R \right\\}$, $A = \mathbb R \times C$, where $\mathcal R$ is the Borel $\sigma$-field on $\mathbb R$, $C \subset \mathbb R$. Let $\mathcal F = \sigma \langle \mathcal B \cup \left\\{ A \right\\} \rangle$, $P$ be a probability measure on $(\mathbb R, \mathcal R)$ and $0 < \alpha < 1$. Show that $Q(F) = \alpha P(B_1) + (1-\alpha)P(B_2)$ for $F = (B_1 \times C) \cup (B_2 \times C^C)$ defines a probability measure on $\mathcal F$ and satisfies $Q(B \times \mathbb R) = P(B)$ for all $B \in \mathcal R$.**

First we must show that the probability of the whole space is equal to 1.

$$
Q(\mathcal F)  = Q\left( (\mathcal R \times C) \cup (\mathcal R \times C^C) \right) = \alpha P(\mathcal R) + (1-\alpha ) P(\mathcal R) = P(\mathcal R)
$$

This is equal to 1 because $P$ is a probability measure on $\mathcal R$.


Now we must show the second condition. Take $F_1, F_2, \dots \in \mathcal F$ to be pairwise disjoint. This means that $B_{1i}$ and $B_{2i}$ will be disjoint from all $B_{1j}$ and $B_{2j}$ where $i \neq j$, respectively. Hence,

$$
\begin{align}
Q\left( \bigcup_{i=1}^{\infty} F_i \right) & = Q \left( \bigcup_{i=1}^{\infty} \left[ (B_{1i} \times C) \cup (B_{2i} \times C^C) \right] \right) \\
    & = Q \left( \left( \bigcup_{i=1}^{\infty} B_{1i} \times C \right) \cup \left( \bigcup_{i=1}^{\infty} B_{2i} \times C^C \right) \right) \\
    & = \alpha P\left( \bigcup_{i=1}^{\infty} B_{1i} \right) + (1-\alpha) P\left( \bigcup_{i=1}^{\infty} B_{2i} \right) \\
    & = \alpha \sum_{i=1}^{\infty} P(B_{1i}) + (1-\alpha) \sum_{i=1}^{\infty} P(B_{2i}) \\
    & = \sum_{i=1}^{\infty} \left( \alpha P(B_{1i}) + (1-\alpha) P(B_{2i}) \right) \\
    & = \sum_{i=1}^{\infty} Q(F_i).
\end{align}
$$

Finally,

$$
\begin{align}
Q(B \times \mathbb R) & = Q\left( (B \times C) \cup (B \times C^C) \right) \\
    & = \alpha P(B) + (1-\alpha) P(B) \\
    & = P(B).
\end{align}
$$


# 5
**Let $(\Omega, \mathcal A, P)$ be a probability space and $A_1, \dots , A_n$ be events. Using induction, show that**


$$
P(A_1 \Delta \dots \Delta A_n) = \sum_{i=1}^{n} P(A_i) - 2 \sum_{i<j} P (A_i \cap A_j) + 4 \sum_{i<j<k} P(A_i \cap A_j \cap A_k) + \dots + (-2)^{n-1} P(A_1 \cap \dots \cap A_n),
$$

**where $A\Delta B$ stands for the symmetric difference of $A$ and $B$.**





We can look at the case for $n=2$. 

$$
\begin{align}
P(A_1 \Delta A_2) & = P \left( (A_1 \setminus A_2) \cup (A_2 \setminus A_1) \right) \\
    & = P(A_1 \setminus A_2) + P(A_2 \setminus A_1)& \text{disjoint} \\
    & = P(A_1) - P(A_1 \cap A_2) + P(A_2) - P(A_2 \cap A_1) \\
    & = \sum_{i=1}^{2} P(A_1) - 2 \sum_{i<j}P(A_i \cap A_j) 
\end{align}
$$

Now we assume that our hypothesis holds for an arbitrary $n$ and will show that it holds for $n+1$.

$$
\begin{align}
P(A_1 \Delta \dots \Delta A_{n+1}) & = P \left( (A_1 \Delta \dots A_n) \Delta A_{n+1} \right) \\
    & = P \left( A_1 \Delta \dots A_n \right) + P(A_{n+1}) - 2 P \left( (A_1 \Delta \dots A_n) \cap A_{n+1} \right) \\
    & = \sum_{i=1}^{n+1} P(A_i) - 2 \sum_{i<j}^{n} P(A_i \cap A_j) + 4 \sum_{i<j<k}^{n} P(A_i \cap A_j \cap A_k) + \dots + (-2)^{n-1}P(A_1 \cap \dots \cap A_n) - 2 P \left( (A_1 \Delta \dots A_n) \cap A_{n+1} \right)
\end{align}
$$

Where at first we applied the step we saw for $n=2$ and then used our inductive step. Finally, recall that intersection distributes over symmetric difference. With that, we can use our inductive step to address this last term.

$$
\begin{align}
P \left( (A_1 \Delta \dots A_n) \cap A_{n+1} \right) & = P \left( (A_1 \cap A_{n+1}) \Delta \dots \Delta (\dots A_n \cap A_{n+1}) \right) \\
    & = \sum_{i=1}^{n} P(A_i \cup A_{n+1}) - 2 \sum_{i<j} P(A_i \cap A_j \cap A_{n+1}) + \dots + (-2)^{(n-1)-1}P(A_1 \cap \dots \cap A_{n+1})
\end{align}
$$

Thus,

$$
P(A_1 \Delta \dots \Delta A_n) = \sum_{i=1}^{n} P(A_i) - 2 \sum_{i<j} P (A_i \cap A_j) + 4 \sum_{i<j<k} P(A_i \cap A_j \cap A_k) + \dots + (-2)^{n-1} P(A_1 \cap \dots \cap A_n).
$$
