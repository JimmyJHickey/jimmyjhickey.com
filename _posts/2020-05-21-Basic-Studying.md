---
layout: post
comments: false
title: Important Theorems for the Basic
description: A list of important theorems and tricks
tags: Basic Tricks 
category: Basic
---

* Do not remove this line (it will not be displayed)
{:toc}


# 701

## 2. Variable Transformation

### Theorem 2.1.5

**CB page 51**

Let $X$ have cdf $F_X(x)$, let $Y = g(X)$ and let $\mathcal X$ and $\mathcal Y$ be defined as in (2.1.7).

$$
\mathcal X =\{ x: f_X(x) > 0 \} \text{ and } \mathcal Y = \{ y: y = g(x) \text{ for some } x \in \mathcal X \}
$$


1. If $g$ is an increasing function of $\mathcal X$, $F_y(y) = F_X(g^{-1}(y))$ for $y \in \mathcal Y$.
2. If $g$ is a decreasing function on $\mathcal X$ and $X$ is a continuous random variable, $F_Y(y) = 1- F_X(g^{-1}(y))$ for $y \in \mathcal Y$.


**Why it's useful**

Can save time doing actual variable transformation if we have these conditions.


**Example problem**

_Casella Berger 4.4 d_

$Z = \frac{ 9 }{ (X+1)^2 }$ is monotone on $0 < x < 2$, so $f(z) = \frac{ 9 }{ 8z^2 }$ on $1 < z < 9$.



# 702




# 703



# 705



