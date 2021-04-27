---
layout: post
comments: false
title: Example Problems on the Central Limit Theorem
description: ST779 Homework 11 on the Central Limit Theorem
tags: ST779 Measure-Theory CLT
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**If $X_1, X_{2}, \dots$ are iid with expectation zero and finite variance, show that $\sum_{n=2}^{\infty} \frac{ X_{n} }{ \sqrt{ n } \log(n)}$ is a.s. convergent and that $(\sum_{i=2}^{n}X_{i}) / (\sqrt{ n } \log(n)) \rightarrow 0$ a.s.**

Since $X_{i}$ has finite variance, say $Var(X_{i}) = c$. Defined $Y_{n} = \frac{ X_{n} }{ \sqrt{ n }\log(n) }$. Then,

$$
\begin{align}
E(Y_{n}) & = \frac{ 1 }{ \sqrt{ n }\log(n) } E(X_{n}) \\
    & = 0 \\
Var(Y_{n}) & = \frac{ 1 }{ \log(n)^{2} } Var(X_{n}) \\
    & = \frac{ c }{ \log(n)^{2} } \\
\sum_{n=2}^{\infty} c \sum_{n=2}^{\infty} \frac{ 1 }{ n \log(n)^{2} }.
\end{align}
$$

Now we need to show that $\sum_{n=2}^{\infty} \frac{ 1 }{ n \log(n)^{2} }$ is finite. We can do this with the integral rule.

$$
\begin{align}
\int_{2}^{\infty}&  \frac{ 1 }{ x \log(x)^{2} } dx & u = \log(x) \\
    & = \int_{\log(2)}^{\infty} \frac{ 1 }{ x u^{2} } x du \\
    & = \Big[ \frac{ -1 }{ u } \Big]_{\log(2)}^{\infty} \\
    & = \frac{ 1 }{ \log(2) } < \infty.
\end{align}
$$


Thus, the $Y_{n}$'s are iid with zero mean and $\sum_{n=2}^{\infty} E(Y_{n}^{2}) < \infty$, so $\sum_{n=2}^{\infty}Y_{n} = \sum_{n=2}^{\infty} \frac{ X_{n} }{ \sqrt{ n } \log(n)}$ converges a.s. 

Now take $Z_{i} = \frac{ X_{i} \sqrt{ n }}{ \log(n) }$.

$$
\begin{align}
E(Z_{i}) & = E(\frac{ X_{i} \sqrt{ n } }{ \log(n) }) \\
    & = 0 \\
Var(Z_{i}) & = \frac{ n }{ \log(n)^{2} } Var(X_{i}) \\
    & = \frac{ c n  }{ \log(n)^{2} } \\ \\
\sum_{n=2}^{\infty} \frac{ E(Z_{n}^{2}) }{ n^{2} } & = \sum_{n=2}^{\infty} \frac{ n }{ n^{2} \log(n)^{2} } c \\
    & = c \sum_{n=2}^{\infty} \frac{ 1 }{ n \log(2)^{2} } < \infty
\end{align}
$$

Thus, by the strong law for independent sequences

$$
\overline{ Z_{n} } = \lim_{n\rightarrow \infty} \sum_{i=2}^{\infty}\frac{ Y_{i} }{ n } = \lim_{n\rightarrow \infty}\sum_{n=2}^{\infty} \frac{ X_{i} }{ \sqrt{ n } \log(n)  } \stackrel{ \text{a.s.}}{\rightarrow} 0.
$$


# 2
**Let $X_{n}$ be independent uniform $[-a_{n}, a_{n}]$, $n = 1, 2, \dots$, where $\\{ a_{n} \\}$ is a bounded sequence. Show that the Lindeberg condition for the array $\\{ X_1, \dots , X_n \\}$, $n = 1, 2, \dots$ holds if and only if $\sum_{n=1}^{\infty} a_{n}^{2} = \infty$.**

Since $a_{i}$ is bounded, by say $c$, we know that $a_{i}^{2} \leq c^{2} $.


$\Rightarrow$

If the Lindeberg condition holds, then we know that we have uniform asymptotic negligibility. That is,

$$
\lim_{n\rightarrow \infty} \max \Big\{ \frac{ a_{i} }{ \sum_{j=1}^{\infty} a_{j} } \ 1 < i < n \Big\} \leq \lim_{n\rightarrow \infty} \frac{ c^{2} }{ \sum_{j=1}^{\infty} a_{j} } = 0.
$$

Since $c$ is a constant, it must be the case that $\sum_{n=1}^{\infty} a_{n}^{2} = \infty$.



$\Leftarrow$

Notice that since the Lindeberg condition implies uniform asymptotic negligibility, the contrapositive is also true. That is, the failure of uniform asymptotic negligibility implies the failure of the Lindeberg condition.

So, assume that $\sum_{i=1}^{\infty} a_{i}^{2} \neq \infty$. Then,

$$
\lim_{n\rightarrow \infty} \max \Big\{ \frac{ a_{i} }{ \sum_{j=1}^{\infty} a_{j} } \ 1 < i < n \Big\} \leq \lim_{n\rightarrow \infty} \frac{ c^{2} }{ \sum_{j=1}^{\infty} a_{j} } \neq 0.
$$

Thus, $\sum_{i=1}^{\infty} a_{i}^{2} = \infty$ implies the Lindeberg condition.


# 3
**Let $X_{n}$ be independent gamma distributed with shape parameter $2^{-n}$ and scale parameter 1, and $S_{n} = \sum_{i=1}^{n} X_{i}$, $n = 1, 2, \dots $. Show that the Lindeberg condition fails for the array $\\{X_{1}, \dots , X_{n} \\}$, $n = 1, 2, \dots$ and the central limit theorem does not hold, i.e. $(S_{n} - E(S_{n}))/\sqrt{ \text{var}(S_{n}) }$ doe not go to $N(0,1)$ in distribution.**

Notice that $S_{n} \sim Gamma(\sum_{i=1}^{n} 2^{-i} , 1)$. Then $E(S_{n}) = Var(S_{n}) = \sum_{i=1}^{n} 2^{-i} = \sigma_{n}^{2}$. Thus, $\lim_{n\rightarrow \infty}\sigma_{n}^{2} = 1$. Now we can again show that uniform asymptotic negligibility fails.

$$
\lim_{n\rightarrow \infty} \max \Big\{  \frac{ \tau_{n,i}^{2} }{ \sigma_{n}^{2} }  \ 1 < i < k_{n} \Big\} = \frac{ 1/2 }{ 1 } = \frac{ 1 }{ 2 } \neq 0
$$

As before, the Lindeberg condition does not hold.

Now we will show that the central limit theorem does not hold. Define 

$$
T_{n} = S_{n} - E(S_{n}) = \sum_{i=1}^{n} X_{i} - \sum_{i=1}^{n} 2^{-i} = \sum_{i=1}^{n} X_{i} - 2^{-i} =\sum_{i=1}^{n} X_{i} - E(X_{i}).
$$ 

Then $E(T_{n}) = 0$ and $Var(T_{n}) = Var(S_{n})$. Again, with this variance uniform asymptotic negligibility does not hold and thus neither does the Lindeberg condition. So,

$$
 \frac{ S_{n} - E(S_{n}) }{ \sqrt{ Var(S_{n}) } } = \frac{ T_{n} }{  \sqrt{ Var(T_{n}) } } \not \stackrel{ \text{d}}{\rightarrow}N(0,1).
$$


# 4
**Let $(U_{1,n} , \dots , U_{n,n})$ be a sequence of random vectors uniformly distributed over the set $\\{ (u_{1}, \dots u_{n} : \sum_{i=1}^{n} u_{i}^{2} = n \\}$. Show that $U_{1,n} \stackrel{ \text{d}}{\rightarrow} N(0,1)$.**

**Hint: Represent $(U_{1,n}, \dots , U_{n,n}$ as $(X_{1}, \dots , X_{n} / \sqrt{ n^{-1} \sum_{i=1}^{n} X_{i}^{2} }$, where $X_{1}, X_{2}. \dots$ is a sequence of iid $N(0,1)$ random variables.**


We can first look at the denominator. Notice that

$$
E\Big[ \frac{ 1 }{ n } \sum_{i=1}^{n} X_{i}^{2} \Big] = \frac{ n }{ n} = 1.
$$

Thus, the denominator goes to 1 in probability. Also, $X_{1} \sim N(0,1) \stackrel{ \text{d}}{\rightarrow} N(0,1)$. Now we can apply Slutsky's Theorem.

$$
U_{1,n} = \frac{ X_{1} }{ \sqrt{ n^{-1} \sum_{i=1}^{n} X_{i}^{2} } } \stackrel{ \text{d}}{\rightarrow} \frac{ N(0,1) }{ \sqrt{ 1 } } = N(0,1)
$$


# 5
**Let $X_{1}, X_{2}, \dots $ be iid with pdf $f(x) = \mid x \mid ^{-3}$, $\mid x \mid > 1$. Show that $X$ has infinite variance, but $\sum_{i=1}^{n} X_{i} / \sqrt{ n \log(n) } \stackrel{ \text{d}}{\rightarrow} N(0,1)$.**

We will start by finding the expected value and variance of $X_{i}$.

$$
\begin{align}
E(X_{i}) & = \int_{-\infty}^{-1} x\cdot -x^{-3} dx + \int_{1}^{\infty} x \cdot x^{-3} dx \\
    & = \int_{-\infty}^{-1} -x^{-2} dx + \int_{1}^{\infty}  x^{-2} dx \\
    & = -1 + 1 \\
    & = 0 \\ \\
E(X_{i}^{2}) & = \int_{-\infty}^{-1} x^{2}\cdot -x^{-3} dx + \int_{1}^{\infty} x^{2} \cdot x^{-3} dx \\
    & = 2 \log(x) \mid_{1}^{\infty} \\
    & = \infty \\ \\ 
Var(X_{i}) & = \infty
\end{align}
$$

Now define $Y_{n} = X_{n} 1\left\\{ \mid X_{n} \mid \leq \sqrt{ n } \right\\}$. Then $E(Y_{n}) = 0$ and 

$$
\begin{align}
Var(Y_{n}) & = E(X_{n}^{2} 1\left\{ \mid X_{n} \mid \leq \sqrt{ n } \right\} ) \\
    & = \int_{-\sqrt{ n }}^{-1} x^{2} \cdot -x^{3} dx + \int_{1}^{\sqrt{ n }} x^{2} \cdot x^{-3} dx \\
    & = 2 \log(x) \mid_{1}^{\sqrt{ n }} \\
    & = \log(n) < \infty.
\end{align}
$$

Then we have $\sigma_{n}^{2} =\sum_{i=1}^{n} E(Y_{i}) = \sum_{i=1}^{n} \log(i)$.

Now we can check Lyapunov's condition for $Y_{n}$. Take $\delta = 1$. Then we need to show that 

$$
\sigma_{n}^{-3} \sum_{i=1}^{n} E( \mid Y_{n} \mid^{3}) \rightarrow 0.
$$

First, let's calculate the expectation

$$
\begin{align}
E(\mid Y_{n} \mid ^{3}) & = E( \mid X_{n} \mid^{3} 1\left\{ \mid X_{n} \mid \leq \sqrt{ n } \right\}) \\
    & = \int_{-\sqrt{ n }}^{-1} x^{3} \cdot -x^{3} dx + \int_{1}^{-\sqrt{ n }} x^{3} \cdot x^{3} dx \\
    & = 2 \int_{1}^{\sqrt{ n }} 1 dx \\
    & = 2 (\sqrt{ n } - 1)
\end{align}
$$

Now we can plug this in.

$$
\begin{align}
\sigma_{n}^{-3} \sum_{i=1}^{n} E( \mid Y_{n} \mid^{3}) & = \Big[ \sum_{i=1}^{n} \log(i) \Big]^{-3} \sum_{i=1}^{n} 2(\sqrt{ i } - 1) \\
    & \leq (n \log(n))^{-3} \Big[ 2 \sum_{i=1}^{n} (\sqrt{ i }) - 2 n \Big]
    & \leq (n \log(n))^{-3} \Big[ 2 n \sqrt{ n } - 2 n \Big] \\
    & = \frac{ 2 n \sqrt{ n } - 2n }{ n^{3} \log(n)^{3} } \rightarrow 0
\end{align}
$$

Thus, Lyapunov's condition holds and 

$$
\frac{ \sum_{i=1}^{n} Y_{i} }{ \sigma_{n} } = \frac{ \sum_{i=1}^{n} Y_{i} }{ \sqrt{ \sum_{i=1}^{\infty} \log(i) } } = \frac{ \sum_{i=1}^{n} Y_{i} }{ \sqrt{ \log(n!) } } \stackrel{ \text{d}}{\rightarrow} N(0,1).
$$ 

Notice that 

$$
\frac{ \log(n!) }{ n \log(n) } \rightarrow 1 \text{ and } \frac{ n \log(n) }{ \log(n!) } \rightarrow 1.
$$

Thus, by Slutsky's Theorem

$$
\frac{ \sum_{i=1}^{n} Y_{i} }{ \sqrt{ n \log(n)} } \cdot \frac{ \sqrt{  n \log(n)} }{ \sqrt{ \log(n!) } } \stackrel{ \text{d}}{\rightarrow} N(0,1).
$$

Now we want to show $\frac{ \sum_{i=1}^{n} X_{i} - Y_{i} }{ \sqrt{ n  \log(n)} } \stackrel{ \text{p}}{\rightarrow}0$. Notice that 

$$
X_{i} - Y_{i} = X_{i} - X_{i} 1 \left\{ \mid X_{i} \leq \sqrt{ i } \right\} = X_{i}1 \left\{ \mid X_{i} > \sqrt{ i } \right\} \rightarrow 0.
$$

Then,

$$
\begin{align}
E( X_{i} 1 \left\{ \mid X_{i} > \sqrt{ i } \right\}) 
    & = \int_{1}^{\infty} \mid x \mid \cdot \mid x \mid^{-3} 1 \left\{ \mid X_{i} > \sqrt{ i } \right\} dx \\
    & = \int_{1}^{\infty} x^{-2} 1 \left\{ \mid X_{i} > \sqrt{ i } \right\} dx \\
    & = \int_{-\infty}^{-\sqrt{ i }} x^{-2} dx + \int_{\sqrt{ i }}^{\infty} x^{-2} dx \\
    & = -x^{-1} \mid_{-\infty}^{-\sqrt{ i }} + -x^{-1} \mid_{\sqrt{ i }}^{\infty} \\
    & = \frac{ 2 }{ \sqrt{ i } }.
\end{align}
$$


Then we can use the triangle inequality to bound our probability.


$$
\begin{align}
P & \Big( \mid \frac{ \sum_{i=1}^{n} X_{i} - Y_{i} }{ \sqrt{ n \log(n) } } > \varepsilon \Big) \\
    & \leq P\Big( \sum_{i=1}^{n} \mid X_{i} - Y_{i} \mid > \sqrt{ n \log(n) } \varepsilon\Big) \\
    & = P \Big( \sum_{i=1}^{n} \mid X_{i} \mid 1(\mid X_{i} \mid > \sqrt{ i }) > \sqrt{ n \log(n) } \varepsilon \Big)
\end{align}
$$


We can again bound our probability using Markov's inequality.

$$
\begin{align}
P & \Big( \sum_{i=1}^{n} \mid X_{i} \mid 1(\mid X_{i} \mid > \sqrt{ i }) > \sqrt{ n \log(n) } \varepsilon \Big)\\
    & \leq \frac{ \sum_{i=1}^{n} E(\mid X_{i} \mid 1(\mid X_{i} \mid > \sqrt{ i })) }{ \sqrt{ n \log(n) } \varepsilon } \\
    & = \frac{ 2 \sum_{i=1}^{n} i^{-1/2} }{ \sqrt{ n \log(n) } \varepsilon} \\
    & \approx \frac{ 2 \cdot 2 \sqrt{ n } }{ \sqrt{ n \log(n) } \varepsilon } \rightarrow 0
\end{align}
$$

Thus $\frac{ \sum_{i=1}^{n} X_{i} - Y_{i} }{ \sqrt{ n \log(n) } } \stackrel{ \text{p}}{\rightarrow}0$.

Now we can combine these results using Slutsky's theorem.

$$
\frac{ \sum_{i=1}^{n} X_{i} }{ \sqrt{ n \log(n) } } = \frac{ \sum_{i=1}^{n} X_{i} +Y_{i} - Y_{i} }{ \sqrt{ n \log(n) } } = \frac{ \sum_{i=1}^{n} Y_{i} }{ \sqrt{ n \log(n) } } + \frac{ \sum_{i=1}^{n} X_{i} - Y_{i} }{ \sqrt{ n \log(n) } } \stackrel{ \text{d}}{\rightarrow} N(0,1) + 0 = N(0,1)
$$