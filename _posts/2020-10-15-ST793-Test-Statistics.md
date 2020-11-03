---
layout: post
comments: false
title: Example Problems on Test Statistics
description: ST793 Homework 7 on Test Statistics
tags: ST793 Testing Asymptotics Statistics
category: ST793
---

* Do not remove this line (it will not be displayed)
{:toc}

# 1
**Consider $Y_1, \dots , Y_n$ are IID from a model $f(y; \theta)$ where $\theta \in \mathbb{R}^b$. Let $\theta_1$ be the component of interest and denote by $\theta_2$ the remaining nuisance component; thus $\theta^T = (\theta_1^T, \theta_2^T)$. Suppose you are interested in testing the hypothesis**


$$
H_0: \theta_1 = \theta_{10} \text{ vs. } H_1: \theta_1 \neq \theta_{10}
$$

**using the likelihood ratio test statistic. Using techniques we employed to prove the asymptotic null distribution of the Wald and score, show in detail that the asymptotic distribution of $T_{LR}$ has a chi-square with $r$ degrees of freedom.**

_Proof_

Recall the form of the likelihood ratio test statistic.

$$
T_{LR} = -2 (\ell(\widetilde \theta) - \ell(\widehat \theta))
$$

Where $\widehat \theta$ is the unrestricted MLE and $\widetilde \theta$ is the restricted MLE under the null hypothesis. Recall that $\widehat \theta, \widetilde \theta \stackrel{ \text{p}}{\rightarrow} \theta_0$. Thus,

$$
\begin{align}
P(|\widehat \theta - \widetilde \theta | \geq \epsilon) & = P(|\widehat \theta - \theta_0 + \theta_0 - \widetilde \theta | \geq \epsilon) \\
    & \leq P(|\widehat \theta - \theta_0| + |  \widetilde \theta - \theta_0 | \geq \epsilon) & \text{Triangle Inequality} \\
    & \leq P(|\widehat \theta - \theta_0| \geq \epsilon / 2) + P(|  \widetilde \theta - \theta_0 | \geq \epsilon/2) & \text{Boole's Inequality} \\
    & \stackrel{ \text{p}}{\rightarrow} 0 + 0 = 0
\end{align}
$$

Now that we know that these MLEs are close, let us take a Taylor expansion of $\ell(\widetilde \theta)$ about $\widehat \theta$. Note that $\theta^*$ is between $\widetilde \theta$ and $\widehat \theta$.


$$
\begin{align}
\ell(\widetilde \theta) & = \ell(\widehat \theta) + (\widetilde \theta - \widehat \theta)^T \frac{ \partial \ell(\widehat \theta) }{\partial \theta} + \frac{1 }{ 2 } (\widetilde \theta - \widehat \theta)^T \frac{ \partial ^2 \ell(\theta^*) }{\partial \theta \partial \theta^T } (\widetilde \theta - \widehat \theta) \\
-2(\ell(\widetilde \theta) - \ell(\widehat \theta)) & = (\widetilde \theta - \widehat \theta)^T \frac{ \partial ^2 \ell(\theta^*) }{\partial \theta \partial \theta^T } (\widetilde \theta - \widehat \theta) \\
T_{LR} & =\sqrt{ n } (\widetilde \theta - \widehat \theta)^T \frac{ 1 }{ n  } \frac{ \partial ^2 \ell(\theta^*) }{\partial \theta \partial \theta^T } \sqrt{ n }(\widetilde \theta - \widehat \theta)
\end{align}
$$

Since both $\widetilde \theta$ and $\widehat \theta$ converge to $\theta_0$ and $\theta^*$ is between them, we can say

$$
\frac{ 1 }{ n } \frac{ \partial ^2 \ell(\theta^*) }{\partial \theta \partial \theta^T } \stackrel{ \text{p}}{\rightarrow} I(\theta_0).
$$


Now we need to examine the convergence in distriubtion of $\sqrt{ n } (\widetilde \theta - \widehat theta)$. Notice,

$$
S(\widetilde \theta) = S(\widehat \theta) - n \widetilde I_n^*( \widetilde \theta - \widehat \theta)
$$

where $\widetilde I\_n^* \stackrel{ \text{p}}{\rightarrow} I(\theta\_0)$. Recall our score at the full MLE, $S(\widehat \theta) = 0$. Also, we only care about the $\theta_1$ component, so $S\_2(\widetilde \theta) = 0$. We can make the above expansion by applying the mean value theorem to each element of the score statistic individually.

$$
S_j(\widetilde \theta) = S_j (\widehat \theta) + S'_j(\theta^{**}_j) (\widetilde \theta - \widehat \theta)
$$


where $\theta^{\* \*}\_j$ is on the line connecting $\widetilde \theta$ and $\widehat \theta$. Now we have a system of equations equivalent to the vector form we used before. Because $\theta^{\* \*}\_j \stackrel{ \text{p}}{\rightarrow}\theta\_0$ for each $j$, it follows that $S'(\theta^{\* \*}\_j) \stackrel{ \text{p}}{\rightarrow} E(S'\_j(\theta\_0))$ and $\widetilde I^*\_n \stackrel{ \text{p}}{\rightarrow} I(\theta\_0)$.

Thus,

$$
\sqrt{ n }(\widetilde \theta - \widehat \theta) \stackrel{ \text{d}}{\rightarrow} I(\theta_0)^{-1} \begin{bmatrix}
Z \\ 0
\end{bmatrix}
$$

where $Z \sim N_r(0, I^{11}(\theta_0)^{-1})$. Thus we have

$$
T_{LR} \stackrel{ \text{d}}{\rightarrow} Z^T I^{11}(\theta_0) Z \sim \chi^2_r.
$$

Since the covariance matrix of $Z$ is $I^{11}(\theta_0)^{-1}$. We will show the $\chi^2_r$ distribution part in question 2.

<div style="text-align: right"> 🐙 </div>


# 2
**Prove that if $X_n$ is a sequence of random vectors such that $X_n \stackrel{ \text{d}}{\rightarrow} N(0 , \Sigma)$ and $D_n \stackrel{ \text{p}}{\rightarrow} D$ and $D$ is symmetric, then if**

$$
D \Sigma \text{ is idempotent and } \text{rank}( D\Sigma ) = r \text{ we have: } X_n^TD_n X_n \stackrel{ \text{d}}{\rightarrow} \chi^2_r
$$

_Proof_

We will first show that $X_n^T D_n X_n \stackrel{ \text{d}}{\rightarrow} X^T D X$ and then we will show that this follows a $\chi^2_r$ distribution. 

Notice that 

$$
X_n^T(D_n - D ) X_n = X_n^T D_n X_n - X_n^T D X_n.
$$

Since $D_n \stackrel{ \text{p}}{\rightarrow} D$, then $D_n - D \stackrel{ \text{p}}{\rightarrow}0$.

By Examples 5.18 in Boos Stefanski we have the convergence of quadratic forms through the Continuous Mapping Theorem  

$$
X_n^T D X \stackrel{ \text{d}}{\rightarrow}X^T D X.
$$

Then take $Y_n = (D_n - D)X_n$. By Slutsky's theorem, $Y_n \stackrel{ \text{d}}{\rightarrow} 0$ which is the same as $Y_n \stackrel{ \text{p}}{\rightarrow}0$. Then we can apply Slutsky's again to say

$$
X^T_n (D_n - D ) X_n = X^T_n Y_n \stackrel{ \text{p}}{\rightarrow} 0.
$$

Thus, we must have $X^T_n D_n X_n \stackrel{ \text{d}}{\rightarrow} X^T D X$. 

Now we can show the second part of the proof, $X^T D X \sim \chi^2_r$. Since $\Sigma$ is positive definite, we can perform a Cholesky decomposition $\Sigma = \Gamma \Gamma^T$. Notice that $Y = \Gamma^{-1} X$, then $Y \sim N(0, I)$. Then take $B = \Gamma^T D \Gamma$. Thus, $Y^T B Y = X^T D X$.  

Since $D \Sigma$ is idempotent, we know $D \Sigma = D \Sigma D \Sigma$ and $D = D \Sigma D$. Further notice that $B$ is idemptotent. 

$$
\begin{align}
B^2 & = \Gamma^T D \Gamma \Gamma^T D \Gamma \\
    & = \Gamma^T D \Sigma D \Gamma \\\
    & = \Gamma^T D \Gamma \\
    & = B
\end{align}
$$

Also, 

$$rank(B) = \text{tr}( B ) = \text{tr}( \Gamma^T D \Gamma ) = \text{tr}( D \Sigma) = \text{rank}( D\Sigma ) = r.$$

Now we have $B$ is symmetric, idempotent, and has rank $r$. Thus there exists a matrix $G$ with orthonormal columns such that $B = G G^T$.  Thus, 

$$
X^T D X = Y^T B Y = Y^T G G^T Y = (G^T Y) (G^T Y). 
$$


Where $G^T Y \sim N_r(G^T 0,G^T I G) = N_r(0,I)$. Thus we are multiplying two standard normals, so 

$$
X^T D X = (G^T Y) (G^T Y) \sim N_r(0, I)^2 = \chi^2_r.
$$

<div style="text-align: right"> 🐙 </div>

# 3
**Assume the data are $\{ (y\_i, x\_i), i = 1, \dots, n\}$ and arise from the regression model**

$$
Y_i = x_i^T \beta + epsilon_i, \ \epsilon_i \stackrel{ \text{iid}}{\sim} N(0, \sigma^2)
$$

**where $\beta^T = (\beta_1^T, \beta_2^T)$ is a $p$-dimensional parameter and $\beta_1$ is the component corresponding to covariates that are of interest. Using the three classical tests. Relate these tests ot other commmon testing procedures that are used in this setting.**


Take $\beta = \begin{bmatrix} \beta_1^T & \beta_2^T \end{bmatrix}$. We are also taking $\sigma^2$ to be unknown. So take $\theta = \begin{bmatrix}
\beta & \sigma^2
\end{bmatrix}^T$. We will be testing

$$
H_0: \beta_1 = \beta_{10} \text{ vs. } H_1: \beta_1 \neq \beta_{10}.
$$

 Let's start by finding the log likelihood.

$$
\begin{align}
\ell(\theta) &= - n \log(2 \pi) - \frac{ n }{ 2 } \log(\sigma^2) - \frac{ 1 }{ 2 \sigma^2 } \Big[ (Y- X\beta)^T(Y - X\beta) \Big] \\
    & = - n \log(2 \pi) - \frac{ n }{ 2 } \log(\sigma^2) - \frac{ 1 }{ 2 \sigma^2 } \Big[ Y^T Y - 2 Y^T X \beta + \beta^T X^T X \beta \Big]
\end{align}
$$

In order to find our Wald test statistic, we need to find the unrestricted MLE and information matrix. Derivative time!

$$
\begin{align}
\frac{ \partial \ell }{\partial \beta} & = \frac{ 1 }{ \sigma^2 }(X^T Y - X^T X \beta) \\
\frac{ \partial \ell }{\partial \sigma^2} & = \frac{ -n }{ 2 } \frac{ 1 }{  \sigma^2} + \frac{ 1 }{ 2 (\sigma^2)^2 } \Big[ (Y- X\beta)^T(Y - X\beta) \Big] \\
\frac{ \partial ^2 \ell }{\partial \beta \beta^T} & = -\frac{ 1 }{ \sigma^2 } X^T X \\
\frac{ \partial ^2 \ell }{\partial (\sigma^2)^2} & = \frac{ n }{ 2 } \frac{ 1 }{ (\sigma^2)^2} - \frac{ 1 }{ (\sigma^2)^3 } \Big[ (Y- X\beta)^T(Y - X\beta) \Big] \\
\frac{ \partial^2 \ell }{\partial \beta \ell } & = -\frac{ 1 }{ 2 (\sigma^2)^2 }(-2X^T Y + 2(X^T X)\beta)
\end{align}
$$

Solving the first derivative with respect to $\beta$ gives $\widehat \beta = (X^TX)^{-1}X^T Y$. Similarly, $ \widehat \sigma^2 = \frac{ 1 }{ n} (Y-X^T \beta)^T (Y - X^T \beta)$.

Notice that $\frac{ (Y-X\beta)^T(Y-X\beta) }{ \sigma^2 } \sim \chi^2_n$. This will make our expectations easier. Now we can find our information matrix.

$$
\begin{align}
I_T & = \begin{bmatrix}
-E(\frac{ \partial ^2 }{\partial \beta^T \partial \beta}) & -E(\frac{ \partial ^2 \ell }{\partial \beta \partial \sigma^2}) \\
-E(\frac{ \partial ^2 \ell }{\partial \beta \partial \sigma^2}) \\ & -E(\frac{ \partial ^2 \ell }{\partial (\sigma^2})^2 \\
\end{bmatrix} \\
    & = \begin{bmatrix}
    \frac{ 1 }{ \sigma^2 } X^T X & 0 \\
    0 & \frac{n }{ 2(\sigma^2)^2 }
    \end{bmatrix} \\
    & = \frac{ 1 }{ \sigma^2 } 
    \left[\begin{array}{c | c c}
    [X^T X]_{11} & [X^T X]_{12} & 0 \\ \hline
    [X^T X]_{21} & [X^T X]_{22} & 0 \\
    0 & 0 & \frac{ n }{ \sigma^2 }
    \end{array} \right] \\
       & = \frac{ 1 }{ \sigma^2 } 
    \left[\begin{array}{c c}
    I_{11} & I_{12} \\ 
    I_{21} & I_{22}
    \end{array} \right]
\end{align}
$$

Then our Wald test statistics is

$$
\begin{align}
T_W & = ( \widehat \beta_1 - \beta_{10})^T (I_T^{11}(\widehat \theta))^{-1}( \widehat \beta_1 - \beta_{10}) \\
    & = ( [(X^TX)^{-1}X^T Y]_1 - \beta_{10})^T (I_T^{11}(\widehat \theta))^{-1}( [(X^TX)^{-1}X^T Y]_1 - \beta_{10}) \\ \\
(I_T^{11}(\widehat \theta))^{-1} & = I_{T , 11}( \widehat \theta) - I_{T , 12}( \widehat \theta) I_{T , 22}( \widehat \theta)^{-1} I_{T , 21}( \widehat \theta) \\
    & = \frac{ 1 }{ \widehat \sigma^2 } \Bigg([X^T X]_{11} - \begin{bmatrix}
    [X^T X]_{12} & 0
    \end{bmatrix} 
    \begin{bmatrix}
    [X^T X]_{22} & 0 \\
    0 & \frac{ n }{ 2 \widehat \sigma^2 }
    \end{bmatrix}^{-1}\begin{bmatrix}
    [X^T X]_{12} \\ 0
    \end{bmatrix} 
    \Bigg) \\
    & = \frac{ 1 }{ \widehat \sigma^2 } \Bigg([X^T X]_{11} - [X^T X]_{12} [X^T X]_{22}^{-1} [X^T X]_{12} \Bigg) \\
\end{align}
$$

Notice that $T_W$ looks like the numerator of an F-test of the form $H_0: K^T b = m$. 

Now we can find our score statistic. We will need to find our restricted MLEs. For this, we will split $X\beta = X_1 \beta_1 + X_2 \beta_2$ where $X_1$ is the columns in $X$ corresponding to the covariates of $\beta_1$ and simialry for $X_2$. Our restricted MLE is

$$
\widetilde \theta = \begin{bmatrix}
\beta_{10} \\ \widetilde \beta_2 \\ \widetilde \sigma^2
\end{bmatrix}
\text{ such that }
\begin{bmatrix}
\text{something} \\ 0 \\ 0
\end{bmatrix}.
$$

We can rewrite our likelihood as 

$$
\begin{align}
\ell(\theta) & = c + \frac{ -n }{ 2 } \log (\sigma^2) - \frac{ 1 }{ 2 \sigma^2 } (Y - X_1 \beta_1 - X_2 \beta_2)^T(Y - X_1 \beta_1 - X_2 \beta_2) \\
    & = c + \frac{ -n }{ 2 } \log (\sigma^2) - \frac{ 1 }{ 2 \sigma^2 } \Big( Y^T Y - Y^T X_1 \beta_1 - Y^T X_2 \beta_2 - \beta^T_1 X_1^T X_1 \beta_1 + \beta_1^T X_1^T X_2 \beta_2 - \beta_2^T X_2^T Y + \beta_2^T X_2 X_1 \beta_1 + \beta_2^T X_2^T X_2 \beta_2 \Big)\\
\end{align}
$$

Now we can take our derivatives again.

$$
\begin{align}
\frac{ \partial \ell }{\partial \beta_1} & = -\frac{ 1 }{ 2\sigma^2 }(-2X_1^T Y + 2 X_1^T X_1 \beta_1 + 2 X_1^T X_2 \beta_2) \\
\frac{ \partial \ell }{\partial \beta_2} & = -\frac{ 1 }{ 2\sigma^2 }(-2X_2^T Y + 2 X_2^T X_2 \beta_2 + 2 X_2^T X_1 \beta_1) \\
\frac{ \partial \ell }{\partial \sigma^2} & = \frac{ -n }{ 2 (\sigma^2) } +\frac{ 1 }{ 2 (\sigma^2)^2 } (Y - X_1 \beta_1 - X_2 \beta_2)^T(Y - X_1 \beta_1 - X_2 \beta_2) \\ 
\frac{ \partial^2 \ell }{\partial \beta_1^T \beta_1} & = \frac{ -1 }{ \sigma^2 } X_1^T X_1 \\
\frac{ \partial^2 \ell }{\partial \beta_2^T \beta_2} & = \frac{ -1 }{ \sigma^2 } X_2^T X_2 \\
\frac{ \partial^2 \ell }{\partial (\sigma^2)^2} & = \frac{ n }{ 2 (\sigma^2)^2 } -\frac{ 1 }{  (\sigma^2)^3 } (Y - X_1 \beta_1 - X_2 \beta_2)^T(Y - X_1 \beta_1 - X_2 \beta_2) \\
\frac{ \partial^2 \ell }{\partial \beta_1^T \beta_2} & = \frac{ -1 }{ \sigma^2 } X_1^T X_2 \\
\frac{ \partial^2 \ell }{\partial \beta_2^T \beta_1} & = \frac{ -1 }{ \sigma^2 } X_2^T X_1 \\
\end{align}
$$

Solving the first order equations gives $\widetilde \beta_2 = (X_2^T X_2)^{-1}(X_2^T Y - X_2^T X_1 \beta_{10}$ and $\widetilde \sigma^2 = \widehat \sigma^2$. Now we can calculate our information matrix.

$$
\begin{align}
I_T & = \frac{ 1 }{ \widetilde \sigma^2 } \left[ 
\begin{array}{ c | c c  }
X_1 ^T X_1 & X_1^T X_2 & 0 \\ \hline
X_2^T X_1 & X_2 X_2 & 0 \\
0 & 0 & \frac{n }{ 2 \sigma^2 }
\end{array}
\right] \\
       & = \frac{ 1 }{ \widetilde \sigma^2 } 
    \left[\begin{array}{c c}
    I_{11} & I_{12} \\ 
    I_{21} & I_{22}
    \end{array} \right]
\end{align}
$$

Thus our score statistic is

$$
\begin{align}
T_S & = S_1(\widetilde \theta)^T (I_{T , 11}( \widetilde  \theta) - I_{T , 12}( \widetilde \theta) I_{T , 22}( \widetilde \theta)^{-1} I_{T , 21}( \widetilde \theta))^{-1} S_1(\widetilde \theta) \\
    &= \Big[ \frac{ -1 }{ 2 \widetilde \sigma^2 } (-2X_1^T Y + 2 X_1^T X_1 \beta_{10} + 2 X_1^T X_2 \widetilde \beta_2\Big]^T \\
    & \cdot \Big[ \frac{ 1 }{ \widetilde \sigma^2 } - \frac{ 1 }{ \widetilde \sigma^2 } X_2^T X_1 (X_2^T X_2)^{-1} X_1^T X_2 \Big]^{-1} \\
    & \cdot \Big[ \frac{ -1 }{ 2 \widetilde \sigma^2 } (-2X_1^T Y + 2 X_1^T X_1 \beta_{10} + 2 X_1^T X_2 \widetilde \beta_2\Big].
\end{align}
$$

Finally, we can put these together to get the likelihood ratio test statistic.

$$
\begin{align}
T_{LR} & = -2(\ell(\widetilde \theta) - \ell(\widehat \theta)) \\
    & = -2 \Big[ \frac{ -n }{ 2 } \log( \widetilde \sigma^2) - \frac{ 1 }{ 2 \widetilde \sigma^2 } \Big( (Y - X_1 \beta_{10} - X_2 \widetilde \beta_2)^T (Y - X_1 \beta_{10} - X_2 \widetilde \beta_2)\Big) - n\log(2\pi) + \frac{ -n }{ 2 } \log( \widehat  \sigma^2)+ \frac{ 1 }{ 2 \widehat \sigma^2 }\Big( (Y-X \widehat \beta)^T(Y-X \widehat \beta) \Big) + n\log(2\pi)\Big] \\
    & = -2 \Big[ - \frac{ 1 }{ 2 \widetilde \sigma^2 } \Big( (Y - X_1 \beta_{10} - X_2 \widetilde \beta_2)^T (Y - X_1 \beta_{10} - X_2 \widetilde \beta_2)\Big) + \frac{ 1 }{ 2 \widehat \sigma^2 }\Big( (Y-X \widehat \beta)^T(Y-X \widehat \beta) \Big) \Big]
\end{align}
$$
