---
layout: post
comments: false
title: Example Problems on $\sigma$-Fields
description: ST779 Homework 1 on $\sigma$-Fields
tags: ST779 Measure-Theory Sigma-Algebra Field
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}


# 1
**Show that the collection of all finite strings of letters A-Z is countable, but the collection of all infinite (i.e. unending) sequences of letters is uncountable.**

Take $\mathcal S$ to be the collection of all finite strings of A-Z. We can write this as $\mathcal S = \bigcup_{k=1}^{\infty} \left\\{ A, \dots, Z \right\\}^k$. Since $\mid A-Z \mid < \mid \mathbb N \mid$, we can define a one-to-one function $f: A-Z \rightarrow \mathbb N$. Since $\mathcal S \rightarrow \bigcup_{k=1}^\infty \mathbb N^k$, we know that $\mathcal S$ is countable. 

Now consider $\mathcal S_\infty$ to be the collection of infinitely long sequences of strings of A-Z. We have shown that $T = \left\\{ 0,1 \right\\}^{\infty}$ is uncountable and $\mathcal S_\infty \subset T$. Thus, $\mathcal S_\infty$ must be uncountable.                                           p


# 2
**Let $A_n$ be a sequence of subsets of $\Omega$. Show that $\lim \inf A\_n = \left\\{ \omega: \lim\_{n\rightarrow \infty} \mathbb I\_{A\_n}(\omega) = 1 \right\\}$.  What is $\left\\{ \omega: \lim_{n\rightarrow \infty} \mathbb I\_{A\_n}(\omega) = 0 \right\\}$? Also characterize the set $\left\\{ \omega: \mathbb I\_{A\_n}(\omega) \text{ does not converge} \right\\}$.**

_Proof_

Take $\omega \in \lim \inf A_n$. By definition, $\omega \in \bigcup_{n=1}^{\infty} \left[ \bigcap_{m=n}^\infty A_m \right]$. Take $B_n = \bigcap_{m=n}^\infty A_m$. Notice that as $n$ increases, so does $B_n$. Then, there exists $n_0$, $\omega \in B_{n_0}$. Then, since $B_n$ is increasing, for all $l \geq n_0$ we know $\omega \in B_l$, or $ \mathbb I\_{B\_l}(\omega) = 1$. Thus, $\omega \in \left\\{ \lim\_{n\rightarrow \infty} \mathbb{I}\_{A\_n}(\omega = 1) \right\\}$. So, $\lim \inf A\_n \subset \left\\{ \omega: \lim\_{n\rightarrow \infty} \mathbb I\_{A\_n}(\omega) = 1 \right\\}$.

Now take $\omega \in \left\\{ \omega: \lim\_{n\rightarrow \infty} \mathbb{I}\_{A\_n}(\omega) = 1 \right\\}$. Thus, ther exists some $n_0$ such that for $l > n_0$, $\omega\in A_n$. Then, 

$$
\omega \in \bigcap_{m = n_0}^\infty A_m \Rightarrow \omega \in \bigcup_{n=1}^\infty \bigcap_{m = n_0}^\infty A_n = \lim \inf A_n.
$$

So, $\lim \inf A\_n \supset \left\\{ \omega: \lim\_{n\rightarrow \infty} \mathbb I\_{A\_n}(\omega) = 1 \right\\}$.

Thus, $\lim \inf A\_n = \left\\{ \omega: \lim\_{n\rightarrow \infty} \mathbb I\_{A\_n}(\omega) = 1 \right\\}$.

<div style="text-align: right"> 🐙 </div>

Notice that $\left\\{ \omega: \lim_{n\rightarrow \infty} \mathbb I\_{A\_n}(\omega) = 0 \right\\}$ means taht at some stage onward, $\omega$ is not in any $A_n$. That is, at some point $\omega \in A_n^C$. By the same argument as above, 

$$
\left\{ \omega: \lim_{n\rightarrow \infty} \mathbb I\_{A\_n}(\omega) = 0 \right\} = \lim \inf A_n^C.
$$

If $\left\\{ \omega: \mathbb I\_{A\_n}(\omega) \text{ does not converge} \right\\}$, then $\omega \in A_n$ infinitely many times AND $\omega \in A_n^C$ infinitely many times. That is,

$$
\omega \in \lim \sup A_n \cap \lim \sup A_n^C.
$$

# 3
**Let $\Omega = \left\\{ 1,2,3,4,5,6 \right\\}$. Find the smallest $\sigma$-field containing the class $\left\\{  \left\\{  1,2,3\right\\}, \left\\{  2,5,6\right\\} \left\\{  3,6\right\\} \right\\}$.**

We can start by creating a partition by taking intersections of the given sets and their complements. 


$$
\begin{align}
\text{set} & & \text{ complement} \\
\left\{ 1,2,3 \right\} & & \left\{ 4,5,6 \right\} \\
\left\{ 2,5,6 \right\} & & \left\{ 1,3,4 \right\} \\
\left\{ 3,6 \right\} & & \left\{ 1,2,4,5 \right\}
\end{align}
$$

Take $C_1 =  \left\\{  1,2,3\right\\}$, $C_2 = \left\\{  2,5,6\right\\}$, and $\left\\{  3,6\right\\}$. Our partition is

$$
\begin{align}
\mathcal P = C_1^C \cap C_2^C \cap C_3^C & = \left\{ 4 \right\} \\
    C_1^C \cap C_2^C \cap C_3 & = \left\{ 5 \right\}\\
    C_1^C \cap C_2 \cap C_3^C & = \varnothing\\
    C_1^C \cap C_2 \cap C_3 & = \left\{ 1 \right\}\\
    C_1 \cap C_2^C \cap C_3^C & = \left\{ 6 \right\}\\
    C_1 \cap C_2^C \cap C_3 & = \left\{ 3 \right\}\\
    C_1 \cap C_2 \cap C_3^C & = \left\{ 2 \right\}\\
    C_1 \cap C_2 \cap C_3 & = \varnothing    
\end{align}
$$

The partitions contains all singletons of elements in $\Omega$. From this, we can generate all 64 element of $\Omega$ by unioning them together. So the smallest $\sigma$-field is the whole power set, $\mathcal P(\Omega)$.

# 4
Let $\Omega = \left\\{ 1,2,3 \right\\}$, $\mathcal F_1 = \left\\{ \varnothing, \left\\{ 1 \right\\}, \left\\{ 2,3, \right\\}, \Omega \right\\}$, $\left\\{ \varnothing, \left\\{ 1,2 \right\\}, \left\\{ 3 \right\\}, \Omega \right\\}$. Show that both $\mathcal F_1$ and $\mathcal F_2$ are $\sigma$-fields, but $\mathcal F_1 \cup \mathcal F_2$ is not a $\sigma$-field.


Let's start with $\mathcal F_1$. 

1. $\varnothing, \Omega \in \mathcal F_1$ ✅
2. $\left\\{ 1 \right\\} \cup \left\\{ 2,3 \right\\} = \Omega \in \mathcal F_1$ ✅
3. * $\varnothing^C = \Omega \in \mathcal F_1$
    * $\left\\{ 1 \right\\}^C = \left\\{ 2,3 \right\\} \in \mathcal F_1$
    * $\left\\{ 2,3 \right\\}^C = \left\\{ 1 \right\\} \in \mathcal F_1$
    * $\Omega^C = \varnothing \in \mathcal F_1$ ✅

Thus, $\mathcal F_1$ is a $\sigma$-field. Now we will look at $\mathcal F_2$


1. $\varnothing, \Omega \in \mathcal F_2$ ✅
2. $\left\\{ 1,2 \right\\} \cup \left\\{ 3 \right\\} = \Omega \in \mathcal F_2$ ✅
3. * $\varnothing^C = \Omega \in \mathcal F_2$
    * $\left\\{ 1,2 \right\\}^C = \left\\{ 3 \right\\} \in \mathcal F_2$
    * $\left\\{ 3 \right\\}^C = \left\\{ 1,2\right\\} \in \mathcal F_2$
    * $\Omega^C = \varnothing \in \mathcal F_2$ ✅

Thus, $\mathcal F_2$ is a $\sigma$-field. Now let's look at $\mathcal F_1 \cup \mathcal F_2$.

$$
\mathcal F_1 \cup \mathcal F_2 = \left\{ \varnothing, \left\{ 1 \right\}, \left\{ 3 \right\}, \left\{ 2,3 \right\}, \left\{ 1,2 \right\}, \Omega \right\}
$$

1. $\varnothing, \Omega \in \mathcal F_1 \cup \mathcal F_2$ ✅
2. $\left\\{ 1 \right\\} \cup \left\\{ 3 \right\\} = \left\\{ 1,3 \right\\} \notin \mathcal F_1 \cup \mathcal F_2$ ❌

Since the union of two elements of $\mathcal F_1 \cup \mathcal F_2$ is not contained in $\mathcal F_1 \cup \mathcal F_2$, it is not a $\sigma$-field.

# 5
**Call a subset $A$ of $\mathbb{R}$ periodic is $x \in A$ and $n \in \mathbb N$ implies that $x \pm n \in A$. Show that the class of all periodic sets forms a $\sigma$-field.**

Take $\mathcal A$ to be the class of all periodic sets.

Notice that if $A = \Omega$ then for any $x \in A$, $x \pm n \in \mathcal A$. If $A = \varnothing$, then $A$ is trivially periodic.

<!--We will show condition 2 by induction. Take $A_1$ and $A_2$ to be periodic with $a_1 \in A_1$ and $a_2 \in A_2$. Then

$$
A_1 \cup A_2 = \left\{ \dots, a_{1}-1, a_{2}-1, a_1, a_2, a_1+1, a_2+1, \dots \right\}
$$

is periodic. Notice that,

$$
\bigcup^n_{i=1}A_i = \left\{ \dots, a_{1}-1, \dots, a_{n}-1, a_1, \dots, a_n, a_1+1, \dots, a_n+1, \dots \right\}
$$

is also periodic. Now if we add another element,

$$
\bigcup^n_{i=1}A_i \cup A_{n+1}=\bigcup^{n+1}_{i=1}A_i = \left\{ \dots, a_{1}-1, \dots, a_{n}-1, a_{n+1}-1, a_1, \dots, a_n, , a_{n+1}, a_1+1, \dots, a_n+1, a_{n+1}+1, \dots \right\}
$$

our union is still periodic. By induction, $\bigcup_{i=1}^\infty A_i \in \mathcal A$.


Finally, if $A$ is periodic with $a \in A$, then

$$
\begin{align}
A & = \left\{ \dots, a-1, a, a+1, \dots \right\} \\
A^C & = \left\{ \dots \cup (a-1, a)\cup (a, a+1) \cup \dots \right\}.
\end{align}
$$

So, $A^C$ is also periodic and $A^C \in \mathcal A$.

Thus, $\mathcal A$ is a $\sigma$-field.-->


Take $A_1, A_2, \dots, \in \mathcal A$ and $x \in \bigcup_{i=1}^\{\infty} A_i$. So, $x \in A_k$ for some $k$. Then $x\pm n \in\bigcup_{i=1}^{\infty} A_i $ for $n \in \mathbb N$. Thus, $\bigcup_{i=1}^{\infty} A_i$ is periodic.


Take $z \in A^C$ for periodic $A$. For sake of contradiction, assume $z \pm n \notin A^C$. Then $z \pm n \in A$. But this would mean that $(z \pm n) \mp n = z \in A$. This contradicts $z \in A^C$, so $A^C$ must be periodic. 

Thus, $\mathcal A$ is a $\sigma$-field.

