---
layout: post
comments: false
title: Example Problems on Asymptotics
description: ST793 Homework 5 on Asymptotics
tags: ST793 Asymptotics Statistics
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

5.32, 5.33, 5.37, 5.51, 5.52

# 5.32
**Suppose that $\widehat \theta\_1 , \dots \widehat \theta\_k$ each satisfy the assumptions of Theorem 5.23 (p. 242):**

$$
\widehat \theta_i - \theta_i = \frac{ 1 }{ n } \sum_{j=1}^n h_i(X_j) + R_{in},
$$

**where $\sqrt{ n } R\_{in} \stackrel{ \text{p}}{\rightarrow} 0$ as $n \rightarrow \infty$ and $E(h\_i(X\_1))=0$ and $\text{Var}(  h\_i(X\_1) ) = \sigma^2\_{hi}<\infty$. Let $T = \sum\_{i=1}^k c\_i \widehat \theta_i$ for any set of constants $c\_1 , \dots , c\_k$. Find the correct approximating function $h_T$ for $T$, show that Theorem 5.23 may be used (verify directly without using later theorems), and find the limiting distribution of $T$.**

Let's rewrite $T$.

$$
\begin{align}
T & = \sum_{i=1}^k c_i \widehat \theta_i \\
    & = \sum_{i=1}^k c_i(\theta_i + \frac{ 1 }{ n } \sum_{i=1}^n h_i(X_j) + R_{in}) \\
    & = \sum_{i=1}^k c_i \theta_i + \sum_{i=1}^k c_i  \frac{ 1 }{ n } \sum_{i=1}^n h_i(X_j) + \sum_{i=1}^k c_i  R_{in} \\
\end{align}
$$

Now we will show that this is in Bahadur Representation. First take $T\_\infty = \sum\_{i=1}^k c\_i \theta\_i$. Then,

$$
\begin{align}
\sum_{i=1}^k c_i  R_{in} & = c_1 R_{1n} + \dots c_k R_{kn} \\
    & = op(n^{-1/2}) + \dots + op(n^{-1/2}) & \text{CMT} \\
    & = op(n^{-1/2}) & \text{page 234 property 5}
\end{align}
$$

Thus, the last term is asymptotically negligible. Further take $h\_T =\sum\_{i=1}^n c\_i h\_i(X\_j)$.

$$
\begin{align}
E(\sum_{i=1}^k c_i h_i(X_j)) & = \sum_{i=1}^k c_i E(h_i(X_j)) \\
    & = 0 \\
\text{Var}(  \sum_{i=1}^k c_i h_i(X_j) )&  =\sum_{i=1}^k c_i^2  \text{Var}(  h_i(X_j)) \\
    \sum_{i=1}^k c_i^2 \sigma^2_{ih} < \infty
\end{align}
$$

Thus,

$$
T \sim N\Big( \sum_{i=1}^k c_i \theta_i , \frac{ 1 }{ n }\sum_{i=1}^k c_i^2 \sigma_{hi}^2\Big)
$$

# 5.33
**Let $(X\_1, Y\_1) , \dots , (X\_n, Y\_n)$ be iid pairs with $E(X\_1) = \mu\_1$, $E(Y\_1) = \mu\_2$, $\text{Var}(  X\_1 ) = \sigma^2\_1$, $\text{Var}(  Y\_1 ) = \sigma^2\_2$ and $\text{Cov}(  X\_1, Y\_1 ) = \sigma\_{12}$.**


## a
**What can we say about the asymptotic distribution of $(\overline{ X }, \overline{ Y })^T$?**

Take 

$$
\mu = \begin{bmatrix}
\mu_1 \\
\mu_2
\end{bmatrix} \text{ and }
\Sigma = 
\begin{bmatrix}
\sigma_1^2 & \sigma_{12} \\
\sigma_{12} & \sigma_2^2.
\end{bmatrix}.
$$

We have appropriate conditions to apply the multivariate central limit theorem.

$$
\begin{align}
\sqrt{ n } \Big( \begin{bmatrix}
\overline{ X } \\ \overline{ Y }
\end{bmatrix} - \begin{bmatrix}
\mu_1 \\
\mu_2
\end{bmatrix}\Big)
& \stackrel{ \text{d}}{\rightarrow} N_2(0 \Sigma) \\
\begin{bmatrix}
\overline{ X } \\
\overline{ Y }
\end{bmatrix} & \sim AN_2(\mu, \Sigma)
\end{align}
$$

## b
**Suppose that $\mu\_1 = \mu\_2 = 0$ and let $T=(\overline{ X })(\overline{ Y })$. Show that**

$$
\begin{align}
nT & \stackrel{ \text{d}}{\rightarrow} Q & \text{as } n \rightarrow \infty,
\end{align}
$$

**describe the random variable $Q$.**

By the WLLN we know

$$
\overline{ X } \rightarrow \mu_1 = 0 , \ \overline{ Y } \rightarrow \mu_2 = 0.
$$

Take $g(\overline{ X }, \overline{ Y }) = n \overline{ X } \overline{ Y }$ Then by the CMT,

$$
g(\overline{ X }, \overline{ Y }) \stackrel{ \text{p}}{\rightarrow} n \mu_1 \mu_2 = 0.
$$

Since convergence in probability implies convergence in distribution, $n T \stackrel{ \text{d}}{\rightarrow} Q = 0$


## c
**Suppose that $\mu\_1 =0,  \mu\_2 \neq 0$ and let $T=(\overline{ X })(\overline{ Y })$. Show that**

$$
\begin{align}
\sqrt{ n }T & \stackrel{ \text{d}}{\rightarrow} R & \text{as } n \rightarrow \infty,
\end{align}
$$

**describe the random variable $R$.**

Choose $b_n = \frac{ 1 }{ \sqrt{ n } }$. Then we can apply the Delta Method (Theorem 5.19). Take 

$$
\begin{align}
g\Big(
\begin{bmatrix}
\overline{ X } \\
\overline{ Y }
\end{bmatrix}
\Big) & = \sqrt{ n } \overline{ X } \overline{ Y }\\
g'\Big(
\begin{bmatrix}
\overline{ X } \\
\overline{ Y }
\end{bmatrix}
\Big) & = \sqrt{ n }
\begin{bmatrix}
\overline{ Y } \\
\overline{ X }
\end{bmatrix}.
\end{align}
$$

Thus,

$$
g\Big(
\begin{bmatrix}
\overline{ X } \\
\overline{ Y }
\end{bmatrix} \Big) \sim AN\Bigg(0 \mu_2,\frac{ 1 }{ n } \begin{bmatrix}
\sqrt{ n } \mu_2 & 0
\end{bmatrix}) \Sigma
\begin{bmatrix}
\sqrt{ n } \mu_2 \\
0
\end{bmatrix}\Bigg)
= AN(0, \mu_2^2 \sigma_1^2).
$$

# 5.37
**Find the approximating $h\_T$ function for the sample skewness $T = m\_3 / (m\_2)^{3/2}$**

Take $m\_2'$ and $m\_3'$ be the sample noncentral moments. Then,

$$
\begin{align}
T & = \frac{ \frac{ 1 }{ 2 } \sum_{i=1}^n (X_i - \overline{ X })^3}{ \Big( \frac{ 1 }{ n } \sum_{i=1}^n (X_i - \overline{ X })^2\Big)^{3/2} } \\
    & = \frac{ m_3' - 3 m_2' \overline{ X } + 2 \overline{ X }^3 }{ \Big( \frac{ 1 }{ n } \sum_{i=1}^n X_i^2 - 2X_i \overline{ X } + \overline{ X }^2 \Big)^{3/2} } \\
    & = \frac{ m_3' - 3 m_2' \overline{ X } + 2 \overline{ X }^3 }{ \Big( m_2' - \overline{ X }^2 \Big)^{3/2} } \\
    & = g(\overline{ X }, m_2', m_3').
\end{align}
$$

Now we will take the derivatives of $g$

$$
\begin{align}
\frac{ \partial g(y_1, y_2, y_3) }{\partial y_1} & = \frac{ 3 y_1 y_3 - 3 y_2^2}{ (y_2 - y_1^2)^{5/2} } \\
\frac{ \partial g(y_1, y_2, y_3) }{\partial y_2} & = \frac{ 3(y_1 y_2 - y_3) }{ 2 (y_2 - y_1^2)^{5/2} } \\ 
\frac{ \partial g(y_1, y_2, y_3) }{\partial y_3} & = \frac{ 1 }{ (y_2 - y_1^2)^{3/2} }.
\end{align}
$$

Now take $\mu_1$, $\mu_2'$, and $\mu_3'$ to be the population noncentral moments.

$$
h_T = \frac{ 3 \mu_1 \mu'_3 - 3 \mu_2 ' ^2}{ (\mu'_2 - \mu_1^2)^{5/2} } (X_i - \mu_1) +  \frac{ 3(\mu_1 \mu'_2 - \mu'_3) }{ 2 (\mu'_2 - \mu_1^2)^{5/2} } (X_i^2 - \mu'_2) + \frac{ 1 }{ (\mu'_2 - \mu_1^2)^{3/2} } (X_i^3 - \mu_3')
$$

# 5.51
**Suppose that $B, B\_1, B\_2, \dots $ are iid random variables with $P(B = -1) = P(B = 1) = 1/2$. Define $X\_i = 2^{-i/2}B\_i$ and $S\_n = X\_1 + \dots + X\_n$. Prove that the standardized sum $S\_n / \sqrt{ \text{Var}(  S\_n ) }$ does not converge in distribution to a standard normal. In doing so show that $\text{Var}(  X_1 )$ contributes to one-half the of the variability of $S_n$ asymptotically. Hint: Show that $S\_{n-1}$ and $\sqrt{ 2 }(X\_2 + \dots + X\_n)$ are identically distributed.**

We will start by showing the hint.

$$
\begin{align}
P(\sqrt{ 2 } (X_2 + \dots + X_n) \leq y) & =P ( \sqrt{ 2 }(\frac{ 1 }{ 2 }B_2 + \dots + (\frac{ 1 }{ 2 })^{n/2} B_n  )\leq y ) \\
    & = P ( (\frac{ 1 }{ 2 })^{1/2} B_2 + \dots + (\frac{ 1 }{ 2 })^{(n-1)/2} B_n  \leq y ) \\
    & = P ( (\frac{ 1 }{ 2 })^{1/2} B_1 + \dots + (\frac{ 1 }{ 2 })^{(n-1)/2} B_{n-1}  \leq y ) & B_i \text{ iid} \\
    & = P(X_1 + \dots + X_{n-1} \leq y) \\
    & = P(S_{n-1} \leq y)
\end{align}
$$

Notice that

$$
E(X_i) = 0 \ \text{Var}(  X_i ) = 2^{-i}.
$$


Now $E(S_n) = 0$ and we can find the variance of $S_n$ using a finite geometric sum.

$$
\text{Var}( S_n  ) = \sum_{i=1}^n 2^{-i} = \frac{ 1-(1/2)^{n+1} }{ 1-1/2 } - 1 = 1-2^{-n} = \nu_n^2
$$

Notice that 

$$
\lim_{n \rightarrow \infty} \frac{ \text{Var}(  X_1 ) }{ \text{Var}(  S_n ) } = \frac{ 1/2 }{ 1- 2^{-n}  } = \frac{ 1/2 }{ 1 } = \frac{ 1 }{ 2 }.
$$

This shows that asymptotically $X_1$ contributes half of the variance of $S_n$.

Take $S_{2:n} = S_n - X_1$ and $Y_n = S_n / \nu_n$ is the standardized sum.


We will proceed by contradiction. Assume that $Y_n$ does converge in distribution to $N(0,1)$. Then $Y_{n-1}$ must also converge in distribution of $N(0,1)$.

$$
\begin{align}
Y_n & = \frac{ S_n }{ \nu_n } \\
    & = \frac{ X_1 }{ \nu_n } + \frac{ S_{2:n} }{ \nu_n } \\
    & = \frac{ X_1 }{ \nu_n } + \frac{ \frac{ 1 }{ \sqrt{ 2 } } S_{n-1} }{ \nu_n } & \text{by the hint} \\
    & = \frac{ \frac{ 1 }{ \sqrt{ 2 } } B_1}{ \nu_n } + \frac{ 1 }{ \sqrt{ 2 } } \frac{ \nu_{n-1} }{ \nu_n } Y_{n-1} \\
    & = \frac{ 1 }{ \sqrt{ 2 } } B + \frac{ 1 }{ \sqrt{ 2 } } \frac{ \nu_{n-1} }{ \nu_n } Y_{n-1}
\end{align}
$$

Notice that $\lim_{n\rightarrow \infty}  \frac{ \nu_{n-1} }{ \nu_n } = 1$. Thus,

$$
Y_n \stackrel{ \text{d}}{\rightarrow} \frac{ 1 }{ \sqrt{ 2 } } B + \frac{ 1 }{ \sqrt{ 2 } } Z
$$

where $Z$ and $B$ are independent and $Z \sim N(0,1)$. However, the sum of a normal random variable $Z / \sqrt{ 2 }$ and a discrete random variable $B / \sqrt{ 2 }$  does not have a normal distribution. This contradicts the assumption that $Y_n \stackrel{ \text{d}}{\rightarrow}N(0,1)$.


# 5.52
**Consider a Gauss-Markov linear model**

$$
Y = X \overline{ \beta } + \epsilon
$$

**where $Y$ and $n \times 1$, the components of $e = (e\_1, \dots e\_n)^T$ are iid$(0, \sigma^2)$, and $X$ is $n \times p\_{n}$. Note that the number of predictors $p\_n$ depends on $n$. Let $H = X(X^TX)^{-1} X^T$ denote the projection (or "hat") matrix with entries $h\_{i,j}$. Note that the $h\_{i,j}$ also depend on $n$. We are interested in the asymptotic properties $n \rightarrow \infty $ or the $i$th residual $Y\_i - \widehat Y\_i$, from this regression model, for a fixed $i$. Prove that if $n$ and $p\_n \rightarrow \infty$ such that**

$$
\begin{align}
h_{i,i} \rightarrow c_i & \text{ for some } 0 \leq c_i < 1 & \text{ and } & \max_{1 \leq j \leq n ,\  j\neq 1} | h_{i,j} \rightarrow 0,
\end{align}
$$

**then**

$$
Y_i - \widehat Y_i \stackrel{ \text{d}}{\rightarrow} (1-c_i)e_i + [ (1-c_i)c_i ]^{1/2} \sigma Z,
$$

**where $Z$ is a standard normal random variable independent of $e_i$. Hint: First prove that $\text{Var}(  \sum\_{j = 1, j \neq i}^n h\_{i,j} e\_j ) = (h\_{i,i} - h\_{i,i}^2) \sigma^2$. Then formulate and verify the appropriate Lindeberg condition. (This result illustrates that least square residuals tend to have a distribution closer to a normal distribution than that of the original error distribution is not normal. Thus, tests for nonnormality may have little power when many predictors are used.)**

First, let's expand $Y_i - \widehat Y_i$.

$$
\begin{align}
Y_i - \widehat Y_i & = Y_i - (HY)_i \\
    & = Y_i - \begin{bmatrix}
    h_{11} & \dots & h_{1n} \\
    \vdots \\
    h_{n1} & \dots & h_{nn}
    \end{bmatrix} \begin{bmatrix}
    Y_{1} \\
    \vdots \\
    Y_n
    \end{bmatrix}_i \\
    & = Y_i - \sum_{j=1}^n h_{ij} Y_i \\
    & = Y_i - h_{ii} Y_i - \sum_{j\neq i} h_{ij} Y_j \\
    & = (1- h_{ii}) Y_i - \sum_{j\neq i} h_{ij} Y_j \\
    & = (1- h_{ii}) (X_i\beta + e_i) - \sum_{j\neq i} h_{ij} (X_j\beta + e_j) \\
    & = (1-h_{ii}) X_i \beta + (1-h_{ii})  e_i -\sum_{j \neq i} h_{ij} X_j \beta - \sum_{j \neq i} h_{ij} e_j
\end{align}
$$

Notice

$$
\begin{align}
\lim_{n\rightarrow \infty} (1-h_{ii})  e_i & = (1-c_i) e_i.
\end{align}
$$

Now let's group two terms together,

$$
\begin{align}
(1- h_{ii}) X_i \beta - \sum_{j \neq i} h_{ij} X_j \beta & =  X_i \beta - h_{ii} X_i \beta - \sum_{j \neq i} h_{ij} X_j \beta \\
    & = X_i \beta - \sum_{j=1}^n h_{ij} X_j \beta \\
    & = X_i \beta - \Big( \sum_{j=1}^n h_{ij} X_j \Big) \beta \\
    & =  X_i \beta - \Big( H_i X\Big) \beta \\
    & =  X_i \beta - \Big( H X\Big)_i \beta \\
    & = X_i \beta - X_i \beta \\
    & = 0
\end{align}
$$

Recall that $H$ is idempotent, or $H = H^2$.

$$
\begin{align}
H & =  \begin{bmatrix}
    h_{11} & \dots & h_{1n} \\
    \vdots \\
    h_{n1} & \dots & h_{nn}
    \end{bmatrix} \\
    & = 
 \begin{bmatrix}
    h_{11} & \dots & h_{1n} \\
    \vdots \\
    h_{n1} & \dots & h_{nn}
    \end{bmatrix}
     \begin{bmatrix}
    h_{11} & \dots & h_{1n} \\
    \vdots \\
    h_{n1} & \dots & h_{nn}
    \end{bmatrix} \\
    & =
     \begin{bmatrix}
        \sum_{j=1}^n h_{1j}^2 & \sum_{j=1}^n h_{1j} h_{2j} & \dots & \sum_{j=1}^n h_{1j} h_{nj} \\
        \vdots  \\
        \sum_{j=1}^n h_{nj} h_{1j} & \dots & & \sum_{j=1}^n h_{nj}^2
    \end{bmatrix} \\
    & = H^2
\end{align}
$$

Thus,

$$
\sum_{j=1}^n h_{ij}^2 = h_{ii} \Rightarrow \sum_{j\neq i}^n h_{ij}^2 + h_{ii}^2 = h_{ii} \Rightarrow \sum_{j\neq i}^n h_{ij}^2 = h_{ii} - h_{ii}^2.
$$

This gives us that

$$
Var(\sum_{j \neq i} h_{ij} e_j) = (h_{ii} - h_{ii}^2) \sigma^2.
$$

Since $e_i$ has mean 0 and they are iid (and we no longer have any cross terms of $H$), by the CLT

$$
\sum_{j \neq i} h_{ij} e_{j} \stackrel{ \text{d}}{\rightarrow} \sqrt{ (1-c_i)c_i } \sigma Z
$$

where $Z\sim N(0,1)$.

Thus,

$$
Y_i - \widehat Y_i \stackrel{ \text{d}}{\rightarrow} (1-c_i)e_i + [ (1-c_i)c_i ]^{1/2} \sigma Z.
$$
