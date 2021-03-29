---
layout: post
comments: false
title: Example Problems on Convergence of Random Variables
description: ST779 Homework 7 on Convergence of Random Variables
tags: ST779 Measure-Theory Convergences Random-Variables
category: ST779
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Let $X_{n}$, $X$, $Y$ be random variables on a probability space $(\Omega, \mathcal{A}, P)$ satisfying $ \mid X_{n} \mid \leq Y$ for all $n$, $X_{n} \rightarrow X$ and $E(Y^{2})< \infty$. Then show that $E[(X_{n}-X)^2] \rightarrow 0$.**

Notice that $\mid X_{n} \mid \leq Y \Rightarrow X_{n}^{2} \leq Y^{2}$. Then $E(X_{n}^{2}) \leq E(Y^{2}) \leq \infty$ $\forall n$. Since this holds for all $n$, $\sup_{n} E(X_{n}^{2}) \leq E(Y^{2}) \leq \infty$. Now take $\psi(\mid X_{n} \mid) = X_{n}^{2}$. Then, $\frac{ \psi( \mid X_n \mid) }{ \mid X_n \mid } \uparrow \infty$ as $\mid X_{n} \mid \rightarrow \infty$. Thus, $X_{n}^{n}$ is uniformly integrable.

Now, since $X_{n} \rightarrow X$ almost surely, and $g(X) =X^{2}$ is a continuous function, by the Continuous Mapping Theorem $X_{n}^{2} \rightarrow X^{2}$ almost surely.

Finally, by since $X_{n}^{2}$ is uniformly integrable, 

$$
E( \mid (X_{n} - X)^2 \mid) = E((X_{n} - X)^{2}) \rightarrow 0.
$$
 

# 2
**Let $X$ be a random variable on a probability space $(\Omega, \mathcal{A}, P)$. Define the moment generating function fo $X$ by $\phi(\lambda) = E(e^{\lambda X})$. Let $\Lambda = \\{ \lambda \in \mathcal{R} : \phi(\lambda) < \infty \\}$. Show that $\phi(\lambda)$ is continuous at any interior point of $\Lambda$.**

We want to show that for $\lambda_{n} \uparrow \lambda_{0} \in \Lambda$ $\exists \delta$,

$$
\mid \lambda_{n} - \lambda_{0} \mid < \delta \rightarrow \mid \phi(\lambda_{n}) - \phi (\lambda_{0}) \mid < \varepsilon
$$

for some $n> N$ and $\varepsilon > 0$. Notice $\lambda_{n} \uparrow \lambda_{0} \Rightarrow \lambda_{n} X \uparrow \lambda_{0} X \Rightarrow e^{\lambda_{n} X} \uparrow e^{\lambda_{0} X}$.

Since $\lambda_{0} \in \Lambda$, $E[e^{\lambda_0 X}] < \infty$. Thus, $\sup_{n} E[e^{\lambda_{n} X}] < \infty$. So, $e^{\lambda_{n} X}$ is uniformly integrable. Thus,

$$
\begin{align}
\mid \phi(\lambda_{n} X) - \phi (\lambda_{0} X) \mid & = \mid E[e^{\lambda_{n} X}] - E[e^{\lambda_{0} X}] \mid \\
    & = \mid E[e^{\lambda_{n} X} - e^{\lambda_{0} X}] \mid \\
    & \leq E(\mid e^{\lambda_{n} X} - e^{\lambda_{0} X} \mid) & \text{Jensen's} \\
    & \rightarrow 0 & \text{uniform integrability}
\end{align}
$$

Then, for $n$ large enough, $\mid E[e^{\lambda_{n} X}] - E[e^{\lambda_{0} X}]\mid  < \varepsilon$. So take $\delta = \mid e^{\lambda_{n+1} X} - e^{\lambda_{0} X}\mid$.

# 3
**Let $X_{n}$ and $Y_{n}$ be random variables independent of each other for all $n$, and that $X_{n} \rightarrow X$, $Y_{n} \rightarrow Y$ (pointwise convergence). Show that $X$ and $Y$ are independent.**

Define $g(X) = e^{i t X}$. We know that $g(X_{n}) \rightarrow g(X)$ and $g(Y_{n}) \rightarrow g(Y)$. Also, $e^{itX} = \cos(tX) + i \sin(tX)$ and $\mid e^{itX} \mid \leq 1$ $\forall t$.

So, we can use the DCT. Since $g(X_{n}) \rightarrow g(X)$ pointwise and $\mid g(X_{n}) \leq 1$ and $E(1) < \infty$, then $E(g(X_{n})) \rightarrow E(g(X))$. Thus we have the characteristic function of $X_{n}$ converging to the characteristic function of $X$. The same holds for $Y_{n}$ and $Y$.

Then,

$$
\begin{align}
\phi(X_{n}, Y_{n}) & = E\Big( e^{i t X_{n} + i u Y_{n}} \Big) \\
    &= E\Big( e^{i t X_{n}}\Big) E \Big(e^{i u Y_{n}} \Big) \\
    & = \phi(X_{n}) \phi(Y_{n}) \\
\lim_{n\rightarrow \infty} \phi(X_{n}, Y_{n}) &= \lim_{n\rightarrow \infty}\phi(X_{n}) \phi(Y_{n}) \\
    & = \phi(X) \phi(Y) \\
    & = E\Big( e^{i t X}\Big) E \Big(e^{i u Y} \Big) \\
    & = E\Big( e^{i t X + i u Y} \Big) \\
    & = \phi(X, Y)
\end{align}
$$

Thus, $X$ and $Y$ are independent.

# 4
**Let $X$ b an integrable random variable on a probability space $(\Omega, \mathcal{A}, P)$ and $A_{n}, A \in \mathcal{A}$ such that $P(A_{n} \Delta A) \rightarrow 0$ as $n \rightarrow \infty$. Show that $\int_{A_{n}} X dP \rightarrow \int_{A} X dP$.**

Since $P(A_{n} \Delta A) \rightarrow 0$, we know

$$
P(A_{n} \Delta A) = P((A_{n} \setminus A) \cup (A \setminus A_{n})) =  P((A_{n} \setminus A)) + P((A \setminus A_{n})) \rightarrow 0.
$$

Thus, $P(A_{n} \setminus A) \rightarrow 0$ and $P(A \setminus A_{n}) \rightarrow 0$. Now we can look at $\int_{A_{n}} X dP$.


$$
\begin{align}
\int_{A_{n}} X dP & = \int_{(A_{n} \cap A) \cup (A_{n} \cap A^{C})} X dP \\
    & =  \int_{(A \setminus (A \setminus A_{n})) \cup (A_{n} \setminus A)} X dP \\
    & = \int_{A} X dP - \int_{A_{n} \setminus A} X dP + \int_{A \setminus A_{n}} X dP\\
    & = E[X 1_{A}] - E[X 1_{A\setminus A_{n}}] + E[X 1_{A_{n} \setminus A}]
\end{align}
$$

Since $X$ is integrable, we know that $\exists M$ such that $\forall \varepsilon > 0$, $\int_{\mid X \mid > M} X dP < \varepsilon$. Now we can look at one of the expectations.

$$
\begin{align}
E[X 1_{A \setminus A_{n}}] & = E[X 1_{A \setminus A_{n}} \cap \mid X \mid > M] + E[X 1_{A \setminus A_{n}} \cap \mid X \mid \leq M] \\ 
    & = \int_{A \setminus A_{n} \cap \cap \mid X \mid > M} X dP + \int_{A \setminus A_{n} \cap \cap \mid X \mid 
    \leq M} X dP \\
    & < \int_{ \mid X \mid > M} X dP + M \int_{A \setminus A_{n}} dP \\
    & \rightarrow 0
\end{align}
$$

Since, $\int_{A \setminus A_{n}} dP \rightarrow 0$. Similarly, $E[X 1\_{A_{n} \setminus A}] \rightarrow 0$. Thus,

$$
\int_{A_{n}} X dP = \int_{A} X dP - \int_{A_{n} \setminus A} X dP + \int_{A \setminus A_{n}} X dP \rightarrow \int_{A} X dP -0 + 0 = \int_{A} X dP.
$$


# 5
**Let $X_{n}$, $Y_{n}$, $X$, $Y$ be random variables on a probability space $(\Omega, \mathcal{A}, P)$ satisfying $0 \leq X_{n} \leq Y_{n}$ for all $n$, $X_{n} \rightarrow X$, $Y_{n} \rightarrow Y$ (pointwise convergence) and $E(Y_{n}) \rightarrow E(Y) < \infty$. Then show that $E(X_{n}) \rightarrow E(X)$.**


Notice $X_{n} - Y_{n} \leq 0$ and $E(0) = 0 < \infty$. Then by Fatou's Lemma,

$$
\begin{align}
E[\limsup X_{n} - Y_{n}] & \geq \limsup E[X_{n} - Y_{n}] \\
E[\limsup X_{n}] - E[\limsup Y_{n}] & \geq \limsup E[X_{n}] - \limsup E[Y_{n}] \\
E[X] - E[Y] & \geq \limsup E[X_{n}] - E[Y] \\
E[X] & \geq \limsup E[X_{n}].
\end{align}
$$


Notice $0 \leq X_{n}$ and $E[0] = 0 < \infty$. Again, by Fatou's Lemma,

$$
E[X] = E[\liminf X_{n}] \leq \liminf E[X_{n}].
$$

Then,

$$
E[X] \leq \liminf E[X_{n}] \leq \limsup E[X_{n}] \leq E[X].
$$

Thus, $E[X_{n}] \rightarrow E[X]$.