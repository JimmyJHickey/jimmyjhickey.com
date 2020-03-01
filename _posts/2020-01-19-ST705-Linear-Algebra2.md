---
layout: post
comments: false
title: Example Problems on Linear Algebra
description: ST705 Homework 2 on Linear Algebra
tags: ST705 Linear-Algebra Statistics
category: ST705
---


* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $x, \mu_{1}, \mu_{2} \in \mathbb{R}^{p}$ and $\Sigma_{1}, \Sigma_{2} \in \mathbb{R}^{p\times p}$ invertible and symmetric.  Derive expressions for $\widetilde{\mu} \in \mathbb{R}^{p}$, $\widetilde{\Sigma} \in \mathbb{R}^{p\times p}$, and $c \in \mathbb{R}$ that satisfy**

$$
-(x - \mu_{1})'\Sigma_{1}^{-1}(x - \mu_{1}) - (x - \mu_{2})'\Sigma_{2}^{-1}(x - \mu_{2}) = -(x - \widetilde{\mu})'\widetilde{\Sigma}^{-1}(x - \widetilde{\mu}) + c,
$$

**where $c$ does not depend on $x$.**


We will take $\widetilde{\Sigma}^{-1} = \Sigma_{1}^{-1} + \Sigma_{2}^{-1}$ and $\widetilde{\mu} = \widetilde{\Sigma}(\Sigma_1^{-1} \mu_1 + \Sigma_2^{-1} \mu_2)$. Notice we are assuming that $\widetilde{\Sigma}^{-1}$ is invertible. We will start by expanding the left hand side of the equation are regrouping the terms.

$$
	\begin{align}
		\text{LHS} & = \\
			& - \Big[ x^T \Sigma_{1}^{-1} x - x^T \Sigma_{1}^{-1} \mu_1 - \mu_1^T \Sigma_{1}^{-1} x + \mu_1^T \Sigma_{1}^{-1} \mu_1 +  \\
			& x^T \Sigma_{2}^{-1} x - x^T \Sigma_{2}^{-1} \mu_2 - \mu_2^T \Sigma_{2}^{-1} x + \mu_2^T \Sigma_{2}^{-1} \mu_2 \Big] \\
			& = - \Big[ x^T \widetilde{\Sigma}^{-1} x - x^T (\Sigma_{1}^{-1} \mu_1 + \Sigma_{2}^{-1} \mu_2) -  (\mu_1^T \Sigma_{1}^{-1} + \mu_2^T \Sigma_{2}^{-1}) x + c\Big]
	\end{align}
$$

Constants will be added and removed to the $c$ term as needed. Let's look at the second term. Again recall that we are assuming that $\widetilde{\Sigma}^{-1}$ is invertible.

$$
	\begin{align}
		x^T (\Sigma_{1}^{-1} \mu_1 + \Sigma_{2}^{-1} \mu_2) & = x^T \widetilde{\Sigma}^{-1} \widetilde{\Sigma} (\Sigma_{1}^{-1} \mu_1 + \Sigma_{2}^{-1} \mu_2)  \\
			& = x^T \widetilde{\Sigma}^{-1} \widetilde{\mu}
	\end{align}
$$

We can do the same thing to the third term.

$$
	\begin{align}
		(\mu_1^T \Sigma_{1}^{-1} + \mu_2^T \Sigma_{2}^{-1}) x & = (\mu_1^T \Sigma_{1}^{-1} + \mu_2^T \Sigma_{2}^{-1}) \widetilde{\Sigma} \widetilde{\Sigma}^{-1} x \\
			& = \widetilde{\mu} \widetilde{\Sigma}^{-1} x
	\end{align}
$$

Finally, we can add and subtract $\widetilde{\mu} \widetilde{\Sigma}^{-1} \widetilde{\mu}$, keeping one of them in the $c$ term as it is independent of $x$. Thus,

$$
	\begin{align}
		LHS & = - \Big[ x^T \widetilde{\Sigma}^{-1} x - x^T (\Sigma_{1}^{-1} \mu_1 + \Sigma_{2}^{-1} \mu_2) -  (\mu_1^T \Sigma_{1}^{-1} + \mu_2^T \Sigma_{2}^{-1}) x + c\Big] \\
			& = - \Big[ x^T \widetilde{\Sigma}^{-1} x - x^T \widetilde{\Sigma}^{-1} \widetilde{\mu} - \widetilde{\mu} \widetilde{\Sigma}^{-1} x + \widetilde{\mu} \widetilde{\Sigma}^{-1} \widetilde{\mu} + c \Big] \\
			& = -(x - \widetilde{\mu})'\widetilde{\Sigma}^{-1}(x - \widetilde{\mu}) + c
	\end{align}
$$

# 2
**Let $A$ be a positive definite matrix, and show that**

$$
\text{tr}(I - A^{-1}) \le \log\det(A) \le \text{tr}(A - I).
$$



Take $A$ to be $n \times n$. Recall that if $A$ is a positive definite matrix that $A^{-1}$ is also positive definite, they both have positive eigenvalues, the trace of them is the sum of their eigenvalues, and the determinant of $A$ is the product of those eigenvalues. If $A$ has eigenvalues $\\{ \lambda_1, \dots, \lambda_n\\}$ then $A^{-1}$ has eigenvalues $\\{ \frac{ 1 }{ \lambda_1 }, \dots, \frac{ 1 }{ \lambda_n }  \\}$. 

$$
tr(I - A^{-1}) = tr(I) - tr(A^{-1}) = n - \sum_{ i=1 }^{ n }\frac{ 1 }{ \lambda_i }
$$


$$
\log(\det(A)) = \log(\prod_{ i=1 }^{ n } \lambda_i) = \sum_{ i=1 }^{ n } \log(\lambda_i)
$$


$$
tr(A - I) = tr(A) - tr(I) = \sum_{ i=1 }^{ n } (\lambda_i) - n = \sum_{ i=1 }^{ n } (\lambda_i - 1)
$$


Recall that $\log( x ) \leq x - 1 \ \forall x \geq 0$. This gives us $\log\det(A) \le \text{tr}(A - I)$. Then,

$$
\log( x ) \leq x - 1 \Rightarrow \log( 1/x ) \leq 1/x - 1 \Rightarrow \log(x) \geq 1 - \frac{ 1 }{ x }.
$$

This gives us $\text{tr}(I - A^{-1}) \le \log\det(A)$. Thus,

$$
\text{tr}(I - A^{-1}) \le \log\det(A) \le \text{tr}(A - I).
$$


# 3
**Suppose you do not know that the rank of a matrix is equal to the number of nonzero eigenvalues.  Show that the rank of a projection matrix is equal to its trace.  First think about how to show this in the symmetric case, and then consider the more general case of a non-symmetric idempotent matrix.**

We know that $A = A^T$ since $A$ is a projection matrix. Let's first examine the symmetric case. We know that $A$ is diagonalizable.

$$
A = Q^T D Q
$$

Where $D$ is a matrix of eigenvalues. We know that these are all either 0 or 1. We also know that $Q$ is and orthogonal basis of eigenvectors, so $Q^TQ = I$. Thus,

$$
tr(A) = tr(Q^T D Q) = tr(Q^T Q D) = tr(D).
$$

The trace of $D$ is the sum of the eigenvalues of $A$. So, the trace of $A$ is the number of nonzero eigenvalues, say $k$. This is also the $\text{rank}(D)$. Since $A$ is symmetric, we also know that $\text{tr}( D ) = \text{tr}( A )$. Thus,

$$
\text{tr}( A ) = k = \text{rank}( D ) = \text{rank}( A ).
$$



Now let's think about a general projection matrix $P \in \mathbb{R}^{n\times n}$. Assume that $\text{rank}( P ) = k$ and that $\\{ u_1, \dots , u_{n-k} \\}$ is a basis for the null space of $P$. Then,

$$
P u_i = 0 = 0 u_i.
$$

Since $u_i$ is a basis vector we know that $u_i \neq 0$. From this, we know that there must be $n-k$ 0 eigenvalues and thus, $k$ nonzero eigenvalues. Since $P$ is a projection matrix, we know that these nonzero eigenvalues are all 1. So,

$$
\text{tr}( P ) = \sum_{ i=0 }^{ n } \lambda_i = k.
$$

Earlier we defined $\text{rank}( P ) = k$, so $\text{rank}( P ) = k = \text{tr}( P )$.

# 4
**Show that if $\text{rank}(BC) = \text{rank}(B)$, then $\text{column}(BC) = \text{column}(B)$, where column$(\cdot)$ denotes the column space.**

Take

$$
	\begin{align}
		B : & \mathbb{R}^q \rightarrow \mathbb{R}^p \\
		C : & \mathbb{R}^l \rightarrow \mathbb{R}^q.
	\end{align}
$$

First we will show that $\text{ column }( BC ) \subset \text{ column }( B )$. We know that $\text{rank}(BC) = \text{rank}(B) = k$. This means that there exists a basis $ \\{u_1, \dots , u_k \\} \subset \text{ column }( BC )$. Thus $\exists x_i \in \mathbb{R}^l$ such that

$$
u_i = BC x_i = B (C x_i ), \ \forall i \in \{1, \dots , k \}.
$$

Notice that $C x_i \in \mathbb{R}^q$. Since $u_i$ is a basis vector, we know that we can find its preimage and that it is unique from $u_j, \ i \neq j$. Thus, $u_i \in \text{ column }( B ) \ \forall i \in \\{1, \dots , k \\}$.


Now we will show $\text{ column }( B ) \subset \text{ column }( BC )$. Take $x \in \mathbb{R}^p$ such that $x = Bv$. Since $\text{rank}( B ) = \text{rank}( BC )$, we can say that $v = Cu$ for $u \in \mathbb{R}^l$. Therefore $x = Bv = BCu$, or $x \in C(BC)$.

# 5
**The _singular value decomposition_ of a matrix $A$ arises from the relationship of the eigenproblems of $A^TA$ and $AA^T$. The spectral decompositions of $A^T A$ and $AA^T$, both nonnegative definite with nonnegative eigenvalues, lead to the expressions**


$$
A^T A = V \begin{bmatrix} \Lambda^2 & 0 \\ 0 & 0 \end{bmatrix} V^T \text{ and } AA^T = U  \begin{bmatrix} \Lambda^2 & 0 \\ 0 & 0 \end{bmatrix} U^T
$$

**where $U$ and $V$ are orthogonal matrices with eigenvectors as columns, and $\Lambda^2$ is the ($rxr$) diagonal matrix of nonzero eigenvalues with $\text{rank}(\Lambda) = \text{rank}( A ) = r$. The diagonal elements of $\Lambda$, square roots of eigenvalues of the inner and outer product matrices, are known as _singular values_ of the matrix $A$. Note that the blocks of $0$ above are sized to fit the appropriate dimensions.**

## a
**Show that if $v^{(j)}$ is a column of $V$ and an eigenvector of $A^TA$, then $Av^{(j)}$ is an (unnormalized) eigenvector of $AA^T$.**

Since $v^{(j)} = v$ is an eigenvector we know

$$
A^T A v = \lambda v.
$$

We can left multiply by $A$.

$$
A A^T A v = A \lambda v \rightarrow A A^T (Av) = \lambda (Av)
$$


Thus, $Av$ is an (unnormalized) eigenvector of $A A^T$.

## b
**Show that $AV = U \Sigma$ where $\Sigma$ is some diagonal matrix.**

Say $\text{rank}( A ) = p$. Then we can write 

$$
AV = [Av_1 \ Av_2 \ \dots \ Av_p \ 0 \dots \ 0].
$$


Notice that

$$
	\begin{align}
		A A^T (A v_j ) & = \lambda_j A v_j \\
		v_j^T A^T A A^T A v_j & = \lambda_j v_j^T A^T A v_j \\
		||A^T A v_j || ^2 & = \lambda_j ||Av_j||^2 \\
		\lambda_j & = \frac{ ||A^T A v_j || ^2 }{ ||Av_j||^2 } \\
		\lambda_j & = || A v_j ||^2 \\
		\sqrt{ \lambda_j } & = || A v_j ||
	\end{align}
$$

We can use will divide each column in $AV$ by its corresponding eigenvalue, but we must also multiply it back in (in essence, we are multiplying by 1).

$$
AV = \underbrace{\Big[\frac{ A v_1 }{ \sqrt{ \lambda_1 } } \ \frac{ A v_2 }{ \sqrt{ \lambda_2 } } \ \dots \frac{ A v_p }{ \sqrt{ \lambda_p } } \ 0 \dots \ 0 \Big]}_{U} \cdot 
\underbrace{
\begin{bmatrix}
\sqrt{ \lambda_1 } &  &  & & & \\
 & \sqrt{ \lambda_2 } &  &   \\
 & & \ddots & & & \\
& &  & \sqrt{ \lambda_p } &   &  \\
& & &  & 0 &  \\
& & & & & \ddots 
\end{bmatrix}
}_{\Sigma}
$$

Notice that all of the empty cells in $\Sigma$ are 0.

## c
**Show that**

$$
\Sigma = 
\begin{bmatrix}
	\Lambda & 0 \\
	0 & 0
\end{bmatrix}
$$

See the derivation in (b).




## d
**Show that we can write the singular value decomposition as**

$$
U^T A V = 
\begin{bmatrix}
	\Lambda & 0 \\
	0 & 0
\end{bmatrix}
$$


Remember that $U$ is orthogonal, so $U^T U = U U^T = I$.

$$
	\begin{align}
		AV & = U \Sigma \\
		U^T A V & = U^T U \Sigma \\
		U^T A V & = \Sigma 
	\end{align}
$$

## e
**Show that the following is the Moore-Penrose generalized inverse for $A$:**

$$
A^+ =  V
\begin{bmatrix}
	\Lambda^{-1} & 0 \\
	0 & 0
\end{bmatrix}
U^T
$$

To show that $A^+$ is the generalized inverse of $A$, we must show that $AA^+A = A$, $A^+ A A^+ = A^+$, and that $A A^+$ and $A^+A$ are symmetric.

$$
	\begin{align}
		A A^+ A & = A \Big[ V \Sigma^{-1} U^T U \Sigma V^T \Big] \\
			& = A \Big[ V \Sigma^{-1} I \Sigma V^T \Big] \\
			& = A \Big[ V I V^T \Big] \\
			& = A \Big[ I \Big] \\
			& = A
	\end{align}
$$


$$
	\begin{align}
		A^+ A A^+ & = A^+ \Big[ U \Sigma V^T V \Sigma^{-1} U^T \Big] \\
			& = A^+ \Big[ U \Sigma I \Sigma^{-1} U^T \Big] \\
			& = A^+ \Big[ U I U^T \Big] \\
			& = A^+ \Big[ I \Big] \\
			& = A^+
	\end{align}
$$

Notice that from the derivations above, $A A^+ = I = A^+ A$. Thus, they are symmetric.

# 6
**Let $A$, $B$, $C$, and $D$ be real valued matrices of dimension $p\times p$, $p\times q$, $q\times p$, and $q\times q$, respectively.  Show that if $D$ is invertible, then**

$$
\det
\begin{pmatrix}
A & B \\
C & D \\
\end{pmatrix} = \det(D) \cdot \det(A - BD^{-1}C).
$$

Recall that if $X, Y \in \mathbb{R}^{z \times z}$ then $\det(X Y) = \det(X) \det(Y)$. Also recall that the multiplication of two block matrices (of appropriate dimensions) looks like

$$
\begin{pmatrix}
A_1 & B_1 \\
C_1 & D_1 \\
\end{pmatrix} 

\begin{pmatrix}
A_2 & B_2 \\
C_2 & D_2 \\
\end{pmatrix} 

=

\begin{pmatrix}
A_1 A_2 + B_1 C_2 & A_1 B_2 + B_1 D_2 \\
C_1 A_2 + D_1 C_2 & C_1 B_2 + D_1 D_2 \\
\end{pmatrix}.
$$


Now say

$$
M = \begin{pmatrix}
A & B \\
C & D \\
\end{pmatrix}.
$$


Notice that $M$ has dimensions

$$
\begin{pmatrix}
p \times p & p \times q \\
q \times p & q \times q \\
\end{pmatrix}

= (p+q) \times (p+q).
$$


Now take

$$
L = 
\begin{pmatrix}
I_p & 0 \\
-D^{-1}C & I_q \\
\end{pmatrix}.
$$

Notice that $L$ also has dimensions $(p+q) \times (p+q)$. Also notice that $L$ is a lower triangular matrix; thus, its determinant is the product of the diagonal entries, which are all 1. So, $\det(L) = 1$. Thus,

$$
	\begin{align}
		M L & = 
			\begin{pmatrix}
				A & B \\
				C & D \\
			\end{pmatrix}
			\begin{pmatrix}
				I_p & 0 \\
				-D^{-1}C & I_q \\
			\end{pmatrix} \\
		& = 
			\begin{pmatrix}
				A I_p + B(-D^{-1} C) & A 0 + B I_q \\
				C I_p + D(-D^{-1} C) & C 0 + D I_q \\
			\end{pmatrix} \\
		& = 
			\begin{pmatrix}
				A - B D^{-1} C & B \\
				0 & D \\
			\end{pmatrix}.
	\end{align}
$$


Now we can take the determinant. Notice that $\det(ML) = \det(M)\det(L) = \det(M) 1 = \det(M)$. Thus,

$$
	\begin{align}
		\det(M) & = \det 
			\begin{pmatrix}
				A - B D^{-1} C & B \\
				0 & D \\
			\end{pmatrix} \\
			& = \det(D) \det(A - B D^{-1} C) - \det(B ) 0 \\
			& = \det(D) \det(A - B D^{-1} C)
	\end{align}
$$