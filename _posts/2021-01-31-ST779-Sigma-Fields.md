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

We can simplify this problem by creating a mapping between the letters A-Z and binary. For example,
* $A \rightarrow 10000000000000000000000000$
* $B \rightarrow 01000000000000000000000000$
* $\vdots$
* $Z \rightarrow 0000000000000000000000001$.

Now that A-Z is in 1 to 1 correspondence with binary strings, we can use the results previously shown about binary strings. That is, the collection of finite binary strings is countable. Thus, the collection of finite strings of A-Z is countable. Similarly, the collection of all infinite binary strings is uncountable. Thus, the collection of all infinite A-Z strings is uncountable as well.

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

Our partition is

$$
P = \left\{ \left\{ 4 \right\}, \left\{ 1 \right\}, \left\{ 5 \right\}, \left\{ 2 \right\}, \left\{ 3 \right\}, \left\{ 6 \right\} \right\}.
$$

The partitions contains all singletons of elements in $\Omega$. From this, we can generate all 64 element of $\Omega$ by unioning them together. So the smallest $\sigma$-field is the whole set $\Omega$.

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

We will show condition 2 by induction. Take $A_1$ and $A_2$ to be periodic with $a_1 \in A_1$ and $a_2 \in A_2$. Then

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

Thus, $\mathcal A$ is a $\sigma$-field.