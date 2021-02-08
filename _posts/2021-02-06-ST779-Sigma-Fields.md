---
layout: post
comments: false
title: Example Problems on $\sigma$-Fields
description: ST779 Homework 2 on $\sigma$-Fields
tags: ST779 Measure-Theory Sigma-Algebra Field
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}


# 1
**Let $\mathcal F$ be a field and suppose that $\mathcal F$ is also closed under countable disjoint unions. Show that $\mathcal F$ is a $\sigma$-field.**

Take $A_1, A_2, \dots \in \mathcal F$. Then define the following disjoint unions

$$
\begin{align}
D_1 & = A_1 \\
D_2 & = A_1 \setminus A_2 \\
D_3 & = A_1 \setminus A_2 \setminus A_3
& \vdots
\end{align}
$$

Since $\mathcal F$ is closed under countable disjoint unions $\bigcup_{i=1}^\infty D_i \in \mathcal F$. But

$$
\bigcup_{i=1}^{\infty}D_i = \bigcup_{i=1}^\infty A_i \in \mathcal F.
$$

So, $\mathcal F$ is closed under countable union and is a $\sigma$-field.
# 2
**Let $\mathcal F$ be a class of subsets of $\Omega$ containing $\Omega$ and having the property that if $A,B \in \mathcal F$, then $A \setminus B = A \cap B^C \in \mathcal F$. Show that $\mathcal F$ is a field.**

_Proof_

Notice that $\Omega \setminus \Omega = \varnothing \in \mathcal F$, so $\Omega, \varnothing \in \mathcal F$. ✅

Now take $A, B \in \mathcal F$. Then $A \setminus B = A \cap B^C \in \mathcal F$. Then,

$$
\begin{align}
A \setminus (A \cap B^C) & = A \cap \left( A \cap B^C \right)^C \\
    & = A \cap \left( A^C \cup B \right) \\
    & = \left( A \cap A^C \right) \cup \left( A \cap B \right) \\
    & = \varnothing \cup A \cap B \\
    & = A \cap B. ✅
\end{align}
$$

Finally, take $A \in \mathcal F$. Then $\Omega \setminus A = A^C \in \mathcal F$. ✅

Thus, $\mathcal F$ is a field.


<div style="text-align: right"> 🐙 </div>


# 3
**Let $\mathcal A$ be a class of subsets of $\Omega$ with properties that (i) $\Omega \in \mathcal A$, (ii) $A \in \mathcal A$ implies that $A^C \in \mathcal A$, and (iii) $\mathcal A$ is closed under finite disjoint unions, i.e., $A_1, \dots A_k \in \mathcal A$, disjoint, then $\bigcup_{i=1}^kA_i \in \mathcal A$. Show by example that $\mathcal A$ need not be a field.**

We want to come up with an example where $A, B \in \mathcal A$. 

Take $\Omega = \left\\{ 1,2,3,4 \right\\}$ and $\mathcal A = \left\\{ \varnothing,  \left\\{ 1,2 \right\\},  \left\\{ 3,4 \right\\}, \left\\{ 1,3 \right\\}, \left\\{ 2,4 \right\\},\Omega \right\\}$. Notice that for all $A \in \mathcal A$ , $A^C \in \mathcal A$ and that $\mathcal A$ is closed under disjoint unions. However, $\left\\{ 1,2 \right\\} \cap \left\\{ 1,3 \right\\} = \left\\{ 1 \right\\} \notin \mathcal A$.


# 4
**Let $\mathcal F_n$, $n = 1, 2, \dots$ be a sequence of fields on $\Omega$ and that $\mathcal F_n \subset \mathcal F_{n+1}$ for all $n$. Show that $\bigcup_{n=1}^\infty \mathcal F_n$ is also a field.**

**If $\mathcal F_n$, $n=1, 2, \dots$, is a sequence of $\sigma$-fields on $\Omega$ and that $\mathcal F_n \subset \mathcal F_{n+1}$ for all $n$, argue that $\bigcup_{n=1}^\infty \mathcal F_n$ is always a field, but construct an example to show that $\bigcup_{n=1}^\infty \mathcal F_n$ need not be a $\sigma$-field.**

_Proof_

Since $\mathcal F_1$ is a field, $\varnothing, \Omega \in \mathcal F_1$. Hence, $\varnothing, \Omega \in $\bigcup_{n=1}^\infty \mathcal F_n$. ✅

Take $A, B \in \bigcup_{n=1}^\infty \mathcal F_n$. Then, without loss of generality, $\exists k$ such that $A \in \mathcal F_k$ and $\exists m \geq k$ such that $B \in \mathcal F_m$. Since $\mathcal F_k \subset \mathcal F_m$, $A \in \mathcal F_m$ and $A \cup B \in \mathcal F_m$. So, $A \cap B \in \bigcup_{n=1}^\infty \mathcal F_n$. ✅

Take $A \in \bigcup_{n=1}^\infty \mathcal F_n$. Then $\exists k$ such that $A \in \mathcal F_k$. Since $\mathcal F_k$ is a field, $A^C \in \mathcal F_k$. Thus, $A^C \in \bigcup_{n=1}^\infty \mathcal F_n$.


<div style="text-align: right"> 🐙 </div>

We need a counter example where $\bigcup_{n=1}^\infty \mathcal F_n$ is closed under intersection, but not under countable union. Take $\mathcal \Omega = \mathbb N$. Define $\mathcal F_i$ as

$$
\begin{align}
\mathcal F_1 & = \left\{ \varnothing, \left\{ 1 \right\}, \mathbb N - \left\{ 1 \right\}, \Omega \right\} \\
\mathcal F_2 & = \left\{ \varnothing, \left\{ 1 \right\}, \left\{ 2 \right\}, \mathbb N - \left\{ 1 \right\}, \mathbb N - \left\{ 2 \right\}, \Omega \right\} \\
& \vdots
\end{align}
$$


Notice that these are all fields. Then take $A_i \in \bigcup_{n=1}^\infty \mathcal F_n$ to be

$$
\begin{align}
A_1 & = \left\{ 3 \right\} \\
A_2 & = \left\{ 4 \right\} \\
& \vdots
\end{align}
$$

Now, $\bigcup_{i=1}^\infty \mathcal A_i = \mathcal N - \left\\{ 1,2 \right\\} \notin \bigcup_{n=1}^\infty \mathcal F_n$.

# 5
**Let $\mathcal B_1$, $\mathcal B_2$ be $\sigma$-fields on $\Omega$. Then show that**

$$
\sigma \langle \mathcal B_1 \cup \mathcal B_2 \rangle = \sigma \langle  \left\{ B_1 \cap B_2: B_1 \in \mathcal B_1, B_2 \in \mathcal B_2  \right\}  \rangle
$$


We will first show that

$$
\sigma \langle \mathcal B_1 \cup \mathcal B_2 \rangle \subset \sigma \langle  \left\{ B_1 \cap B_2: B_1 \in \mathcal B_1, B_2 \in \mathcal B_2  \right\}  \rangle.
$$


Since $\mathcal B_1$ is a \sigma field, $B_1 \in \mathcal B_1 \Rightarrow \mathcal B_1$. Similarly for $\mathcal B_2$. Thus,

$$
\sigma \langle  \left\{ B_1 \cap B_2: B_1 \in \mathcal B_1, B_2 \in \mathcal B_2  \right\}  \rangle = \langle \dots, \left\{ B_1 \cap B_2 \right\} , \left\{ B_1 \cup B_2^C \right\} , \left\{ B_1^C \cap B_2 \right\} \rangle. 
$$

Notice that these first two sets contain all of $B_1$ and the first and third set contain all of $B_2$. Thus, for any $B_1 \in \mathcal B_1$ and $B_2 \in \mathcal B_2$, 

$$B_1 \cup B_2 \in \sigma \langle  \left\{ B_1 \cap B_2: B_1 \in \mathcal B_1, B_2 \in \mathcal B_2  \right\}  \rangle$$ 

since $\sigma$-fields are closed under countable unions.


Now we must show

$$
\sigma \langle \mathcal B_1 \cup \mathcal B_2 \rangle \supset \sigma \langle  \left\{ B_1 \cap B_2: B_1 \in \mathcal B_1, B_2 \in \mathcal B_2  \right\}  \rangle.
$$


Again take $B_1 \in \mathcal B_1 \Rightarrow B_1^C \in \mathcal B_1$ and $B_2, B_2^C \in \mathcal B_2$. Then $B_1^C \cup B_2^C \in \mathcal B_1 \cup \mathcal B_2$ and  $(B_1^C \cup B_2^C)^C = B_1 \cap B_2  \in \mathcal B_1 \cup \mathcal B_2$. Thus, 

$$
\sigma \langle \mathcal B_1 \cup \mathcal B_2 \rangle \supset \sigma \langle  \left\{ B_1 \cap B_2: B_1 \in \mathcal B_1, B_2 \in \mathcal B_2  \right\}  \rangle.
$$

Hence,

$$
\sigma \langle \mathcal B_1 \cup \mathcal B_2 \rangle = \sigma \langle  \left\{ B_1 \cap B_2: B_1 \in \mathcal B_1, B_2 \in \mathcal B_2  \right\}  \rangle.
$$
