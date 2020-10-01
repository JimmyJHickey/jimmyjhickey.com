---
layout: post
comments: false
title: Example Problems on Multiple Treatment Regimes
description: ST790 Homework 2 on Multiple Treatment Regimes
tags: ST790 Treatment Regimes Statistics
category: ST790-Dynamic-Treatment-Regimes
---

* Do not remove this line (it will not be displayed)
{:toc}

Analytical Problems

# 1

## a

First let's simplify the estimator by plugging in $K=1$.

$$
\begin{align}
\widehat{\mathcal V}_{AIPW} & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \Big\{ \prod_{k=2}^K \pi_{d,k}(\overline{ X }_{ki}) \Big\} \pi_{d,1}(X_{1i}) } + \sum_{k=1}^K \Big\{ \frac{ \mathcal C_{\overline{ d }_{k-1} ,i } }{ \overline{ \pi }_{d,k-1}(\overline{ X }_{k-1,i}) } - \frac{ \mathcal C_{\overline{ d }_{k} ,i } }{ \overline{ \pi }_{d,k}(\overline{ X }_{ki}) }\Big\} L_{k}(\overline{ X }_{ki}) \Bigg] \\
    & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \Big\{ \prod_{k=2}^1 \pi_{d,k}(\overline{ X }_{ki}) \Big\} \pi_{d,1}(X_{1i}) } + \sum_{k=1}^1 \Big\{ \frac{ \mathcal C_{\overline{ d }_{k-1} ,i } }{ \overline{ \pi }_{d,k-1}(\overline{ X }_{k-1,i}) } - \frac{ \mathcal C_{\overline{ d }_k}, i }{ \overline{ \pi }_{d,k}(\overline{ X }_{ki}) }\Big\} L_{k}(\overline{ X }_{ki}) \Bigg] \\
    & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \pi_{d,1}(X_{1i}) } + \Big\{  \frac{ \mathcal C_{\overline{ d }_{1-1} ,i } }{ \overline{ \pi }_{d,1-1}(\overline{ X }_{1-1,i}) } - \frac{ \mathcal C_{\overline{ d }_{1} ,i } }{ \overline{ \pi }_{d,1}(\overline{ X }_{1i}) }   \Big\} L_{1}(\overline{ X }_{1i}) \Bigg] \\
    & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \pi_{d,1}(X_{1i}) } + \Big\{  \frac{ 1 }{1 } - \frac{ \mathcal C_{\overline{ d }_{1} ,i } }{ \overline{ \pi }_{d,1}(\overline{ X }_{1i}) }   \Big\} L_{1}(\overline{ X }_{1i}) \Bigg] \\
    & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \pi_{d,1}(X_{1i}) } - \frac{ \mathcal C_{d,i} }{ \pi_{d,1}(H_{1i}; \gamma_1) } L(H_{1i}) + L(H_{1i}) \Bigg] \\
     & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \pi_{d,1}(X_{1i}) } - \frac{ \mathcal C_{d,i} - \pi_{d,1}(H_{1i}; \gamma_1)}{ \pi_{d,1}(H_{1i}; \gamma_1) } L(H_{1i})) \Bigg] \\
\end{align}
$$

Now we can check that the expectation of the summation term is 0.

$$
\begin{align}
\mathbb E \Big[ & \frac{ \mathcal C_{d,i} - \pi_{d,1}(H_{1i}; \gamma)}{ \pi_{d,1}(H_{1i}; \gamma) } L(H_{1i}) \Big] \\
    & = \mathbb E \Big[ \mathbb E\Big(  \frac{ \mathcal C_{d,i} - \pi_{d,1}(H_{1i}; \gamma)}{ \pi_{d,1}(H_{1i}; \gamma) } L(H_{1i}) \lvert H_{1i} \Big) \Big] \\
    & = \mathbb E \Big[ \frac{ \mathbb E(\mathcal C_{d,i} | H_{1i}) - \pi_{d,1}(H_{1i} ; \gamma ) }{ \pi_{d,1}(H_{1i} ; \gamma ) } \Big] \\
    & = \mathbb E \Big[ \frac{ \pi_{d,1}(H_{1i} ; \gamma ) - \pi_{d,1}(H_{1i} ; \gamma ) }{ \pi_{d,1}(H_{1i} ; \gamma ) } \Big] \\
    & = 0 ✅
\end{align}
$$

## b

Now we can expand for $K=2$.

$$
\begin{align}
\widehat{\mathcal V}_{AIPW} & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \Big\{ \prod_{k=2}^2 \pi_{d,k}(\overline{ X }_{ki}) \Big\} \pi_{d,1}(X_{1i}) } + \sum_{k=1}^2 \Big\{ \frac{ \mathcal C_{\overline{ d }_{k-1} ,i } }{ \overline{ \pi }_{d,k-1}(\overline{ X }_{k-1,i}) } - \frac{ \mathcal C_{\overline{ d }_{k} ,i } }{ \overline{ \pi }_{d,k}(\overline{ X }_{ki}) }\Big\} L_{k}(\overline{ X }_{ki}) \Bigg] \\
    & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \Big\{  \pi_{d,2}(\overline{ X }_{2i}) \pi_{d,1}(X_{1i}) } +  \frac{ \mathcal C_{d,i} - \pi_{d,1}(H_{1i}; \gamma)}{ \pi_{d,1}(H_{1i}; \gamma) } L(H_{1i}) + \Big\{ \frac{ \mathcal C_{\overline{ d }_{2-1} ,i } }{ \overline{ \pi }_{d,2-1}(\overline{ X }_{2-1,i}) } - \frac{ \mathcal C_{\overline{ d }_{2} ,i } }{ \overline{ \pi }_{d,2}(\overline{ X }_{2i}) }\Big\} L_{k}(\overline{ X }_{2i}) \Bigg] \\
    & = \frac{ 1 }{ n }\sum_{i=1}^{n}  \Bigg[ \frac{ \mathcal C_{d,i} Y_i }{ \Big\{  \pi_{d,2}(\overline{ X }_{2i}) \pi_{d,1}(X_{1i}) } +  \frac{ \mathcal C_{d,i} - \pi_{d,1}(H_{1i}; \gamma)}{ \pi_{d,1}(H_{1i}; \gamma) } L(H_{1i}) + \Big\{ \frac{ \mathcal C_{\overline{ d }_{1} ,i } }{ \overline{ \pi }_{d,1}(\overline{ X }_{1,i}) } - \frac{ \mathcal C_{\overline{ d }_{2} ,i } }{ \overline{ \pi }_{d,2}(\overline{ X }_{2i}) }\Big\} L_{k}(\overline{ X }_{2i}) \Bigg] \\
\end{align}
$$

Recall in part (a) we showed that the expectation of the $k=1$ term of the summation was equal to 0. By the linearity of expectation, we only need to show that the $k=2$ term is 0.

$$
\begin{align}
\mathbb E \Bigg[ & \Big\{ \frac{ \mathcal C_{\overline{ d }_{1} ,i } }{ \overline{ \pi }_{d,1}(\overline{ X }_{1,i}) } - \frac{ \mathcal C_{\overline{ d }_{2} ,i } }{ \overline{ \pi }_{d,2}(\overline{ X }_{2i}) }\Big\} L_{k}(\overline{ X }_{2i}) \Bigg] \\
& = \mathbb E \Bigg[ \mathbb E \Big( \Big\{ \frac{ \mathcal C_{\overline{ d }_{1} ,i } }{ \overline{ \pi }_{d,1}(\overline{ X }_{1,i}) } - \frac{ \mathcal C_{\overline{ d }_{2} ,i } }{ \overline{ \pi }_{d,2}(\overline{ X }_{2i}) }\Big\} L_{k}(\overline{ X }_{2i}) | H_2 \Big) \Bigg] \\
    & = \mathbb E \Bigg[ \mathbb E \Big( \Big\{ 1- \frac{ \mathcal C_{\overline{ d }_{2} ,i } }{ \overline{ \pi }_{d,2}(\overline{ X }_{2i}) }\Big\} L_{k}(\overline{ X }_{2i}) | H_2 \Big) \Bigg] & \text{from (a)}\\
    & = \mathbb E \Bigg[ \mathbb E \Big( \Big\{ 1- \frac{ \mathbb I ([a_1, a_2] = [d_1(H_1), d_2(H_2)]) }{\pi_{d,1}(H_1) \pi_{d,2}(\overline{ X_2 }) }\Big\} L_{k}(\overline{ X }_{2i}) | H_2 \Big) \Bigg] \\
    & = \mathbb E \Bigg[  \Big( \Big\{ 1- \frac{ \mathbb E (\mathbb I ([a_1, a_2] = [d_1(H_1), d_2(H_2)]|H_2) }{ P(A_1 =1 | H_1) P(A_2 = 1| H_2) }\Big\} L_{k}(\overline{ X }_{2i})  \Bigg] \\
    & = \mathbb E \Bigg[  \Big( \Big\{ 1- \frac{ P(A_1 = 1, A_2 = 1 | H_1, H_2) }{ P(A_1 =1 | H_1) P(A_2 = 1| H_2) }\Big\} L_{k}(\overline{ X }_{2i})  \Bigg] \\
    & = \mathbb E \Bigg[  \Big( \Big\{ 1- \frac{ P(A_2= 1,| H_1, H_2, A_1) P(A_1 = 1| H_1, H_2) }{ P(A_1 =1 | H_1) P(A_2 = 1| H_2) }\Big\} L_{k}(\overline{ X }_{2i})  \Bigg] \\
    & = \mathbb E \Bigg[  \Big( \Big\{ 1- \frac{ P(A_2= 1,| H_2) P(A_1 = 1| H_1 }{ P(A_1 =1 | H_1) P(A_2 = 1| H_2) }\Big\} L_{k}(\overline{ X }_{2i})  \Bigg] \\
    & = \mathbb E \Bigg[  \Big( \Big\{ 1- 1 \Big\} L_{k}(\overline{ X }_{2i})  \Bigg] \\
    & = 0 ✅
\end{align}
$$


## c

$$
\begin{align}
\widehat{\mathcal V}_{AIPW}(d) & = \frac{ 1 }{ n } \sum_{i=1}^{n} \Bigg[ \frac{ \mathbb I(D_i = \infty) Y_i }{ \overline{ \pi }_{d,K}(\overline{ X }_{K,i}) } + \sum_{k=1}^K \Big( \frac{ \mathbb I(D_i = k) - \lambda_k(\overline{ X }_{ki}) \mathbb I(D_i \geq k)  }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) } \Big) L_k(\overline{  X}_{ki}) \Bigg] \\
    & = \frac{ 1 }{ n } \sum_{i=1}^{n} \Bigg[ \frac{ \mathbb I(D_i = \infty) Y_i }{ \overline{ \pi }_{d,K}(\overline{ X }_{K,i}) } + \sum_{k=1}^K \Big( \frac{ \mathbb I(D_i = k) - \lambda_k(\overline{ X }_{ki}) \mathbb I(D_i \geq k)  }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) } \Big) L_k(\overline{  X}_{ki}) \Bigg] \\
    & = \frac{ 1 }{ n } \sum_{i=1}^{n} \Bigg[ \frac{ \mathbb I(D_i = \infty) Y_i }{ \overline{ \pi }_{d,K}(\overline{ X }_{K,i}) } + \sum_{k=1}^K \Big( \frac{ \mathbb I(D_i = k) - \lambda_k(\overline{ X }_{ki}) \mathbb I(D_i \geq k)  }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) } \Big) L_k(\overline{  X}_{ki}) \Bigg] \\
\end{align}
$$

Let's look at the IPW term in the summation.

$$
\begin{align}
\frac{ \mathbb I(D_i = \infty) Y_i }{ \overline{ \pi }_{d,K}(\overline{ X }_{K,i}) }  & = \frac{ \mathbb I(\overline{ A } = \overline{ d }(\overline{ X })) Y_i }{ \overline{ \pi }_{d,K}(\overline{ X }_{K,i}) } \\
    & = \frac{ \mathcal C_{d,i} Y_i }{ \overline{ \pi }_{d,K}(\overline{ X }_{K,i}) } & \text{slide 327} \\
    & = \frac{ \mathcal C_{d,i} Y_i }{ \Big[ \prod_{k=2}^K \pi_{d,k}(\overline{ X }_{k,i}) \Big] \pi_{d,i}(X_1) } & \text{slide 327}
\end{align}
$$

This form now matches equation (2). Now let's look at the augmentation part of the summation. To start, we know that $\mathbb I(D_i \geq k) = \mathcal C_{\overline{ d }_{k-1,i}}$ and $\mathbb I(D_i = k) = \mathbb I(D_i \geq k) - \mathbb I(D_i \geq k+1)$. Then,

$$
\begin{align}
\frac{ \mathbb I(D_i = k) - \lambda_k(\overline{ X }_{k,i}) \mathbb I(D_i \geq k)  }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) } & = \frac{ \mathcal C_{\overline{ d }_{k-1,i}} - \mathcal C_{\overline{ d }_{k,i}} - \lambda_k(\overline{ X }_{ki}) \mathcal C_{\overline{ d }_{k-1,i}}  }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) } \\
    & = \frac{ \mathcal C_{\overline{ d }_{k-1,i}} - \mathcal C_{\overline{ d }_{k,i}} - (1 - \pi_{d,k}(\overline{ X }_{k,i}))\mathcal C_{\overline{ d }_{k-1,i}}  }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) } \\
    & = \frac{ \pi_{d,k}(\overline{ X }_{k,i}) \mathcal C_{\overline{ d }_{k-1,i}} }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) } - \frac{ \mathcal C_{\overline{ d }_{k,i}} }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) }\\
    & = \frac{ \mathcal C_{\overline{ d }_{k-1,i}} }{ \overline{ \pi }_{d,k-1}(\overline{ X }_{k-1,i}) } - \frac{ \mathcal C_{\overline{ d }_{k,i}} }{ \overline{ \pi }_{d,k}(\overline{ X }_{k,i}) }& \text{slide 327}\\
\end{align}
$$

This matches the form in (2) that we expected.