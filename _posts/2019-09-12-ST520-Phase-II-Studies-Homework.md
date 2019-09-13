---
layout: post
comments: false
title: Example Problems on Stage II Design of Clinic Trials
description: ST520 Homework 2 on Stage II Design
tags: ST520 Statistics Clinical-Trials Study-Design Stage-II
---

Problems: 1, 2, 3, 4


* Do not remove this line (it will not be displayed)
{:toc}

# 1
**In a small phase II clinical trial, 20 patients receive a new treatment and five have a complete response. Find the 80% confidence interval for the probability of a complete response $\pi$ using**

## a.
**normal approximation**
Take our sample proportion $p = \frac{ X }{ n } = \frac{ 2 }{ 20 }$. Then,

$$
	\begin{align}
		(\pi_L, \pi_U) & = p \pm Z_{\alpha / 2}\Big( \frac{ p(1-p) }{ n } \Big))^2 \\
			& = \frac{ 5 }{ 20 } \pm 1.28\cdot \Big( \frac{ \frac{ 5 }{ 20 }(1-\frac{ 5 }{ 20 }) }{ 20 } \Big)^2 \\
			& = (0.126065, 0.373935)
	\end{align}
$$

## b.
**exact confidence intervals**
We can look at our equations for the exact confidence interval and use R to calculate it.

$$
	\begin{align}
		P_{\pi_L(5)} ( X \geq 5) &= \sum_{j=5}^{20} {20 \choose j}\cdot \pi_L(5)^j\cdot (1-\pi_L(5))^{20-j} = \frac{ 1 - 0.80 }{ 2 }\\
		P_{\pi_U(5)} ( X \leq 5) &= \sum_{j=0}^{5} {20 \choose j}\cdot \pi_U(5)^j\cdot (1-\pi_U(5))^{20-j} = \frac{ 1 - 0.80 }{ 2 }
	\end{align}
$$

We can calculate this with the `Hmisc` package in R.

```
library(Hmisc)
binconf(k,n,alpha=.10,method="all")
```

$$
(\pi_L, \pi_U) = (0.10408084, 0.4555824)
$$

## c.
**Compute the probability that the exact confidence interval covers the true value of $\pi$ when**

We can calculate this proportion using R as well.

```
ci_proportion = function(p)
{
  prob = 0
  for(i in 0:20)
  {
    bounds = binconf(i, 20, alpha=0.10, method="exact")

    if( bounds[2] <= p && p <= bounds[3] )
    {
      prob = prob + dbinom(i, 20, p)
    }
  }
  return(prob)
}

ci_proportion(0.2)
# 0.9563281

ci_proportion(0.5)
# 0.9586105
```


### i.
$\pi = 0.2$

For $\pi = 0.2$ we get a probability of 0.9563281.

### ii.
$\pi = 0.5$

For $\pi = 0.5$ we get  a probability of 0.9586105.


#  2
**Suppose the minimal acceptable response rate in a phase II clinical trial is 0.25. Using Gehan's two-stage design, we will declare a new treatment a failure if there is little evidence (say 0.05)  that this treatment will not have a response rate greater than or equal 0.25. If we continue to the second stage, we want the 95% confidence interval for the probability of response to be within $\pm 0.10$.**

**How would you set up this phase II trial? i.e. how many individuals would you study in the first and second stage and what is the decision rule for continuing to the second stage?**

In stage one, we will have $n_0$ individuals.

$$
	\begin{align}
		(1-0.25)^{n_0} \leq 0.05 \\
		n_0 \geq \frac{ \log(0.05) }{ \log(1-0.25) }\\
		n_0 \geq 10.4133 \\
		n_0 = 11
	\end{align}
$$

Thus, we will have 11 participants in stage 1 and as is the rule with Gehan's Design, we will continue into the second stage if one or more of them responds.

Stage two will have $n$ total individuals (including the 11 from stage one).

$$
	\begin{align}
		0.10 & = 1.96 \cdot \Big( \frac{ 0.25 (1-0.25) }{ n } \Big)^{1/2}\\
		n & \geq 72.03\\
		n & = 73
	\end{align}
$$

There will be 73 total individuals in the study, 11 in the first stage and 62 more introduced in stage two.

#  3
**Consider the following two stage decision rule:**

**Three patients are given a new drug. If none respond, they study is terminated and the drug is declared a failure. If all three respond then the study is terminated and declared a success. Otherwise, an additional five patients are treated. If the total number of responses among all eight patients is less than or equal to four then the drug is declared ineffective; otherwise it is considered a success.**


## a.
**Using this decision rule, compute the probability that the drug will be considered a success if the true probability of response is 0.25, 0.50, and 0.75**

Notice that we can succeed in stage one if all 3 patients respond. Similarly, we can respond in stage two if five or more patients (total) respond. Notice that success in stage two takes into account the patients in stage one, thus we must pay close attention to how we can succeed in stage 2. There must be either one or two patients that have responded in stage one for use to succeed in stage two (because if all three respond or if none respond, then we would not have made it into stage two).

$$
	\begin{align}
		P(Success) & = P(Success \ Stage \ 1) + P(Success \ Stage \ 2) \\
		P(Success \ Stage \ 1) & = p^3 \\
		P(Success \ Stage \ 2) & = { 3 \choose 1} p (1-p)^2 \cdot \sum_{k=4}^{5} {5 \choose k} p^k (1-p)^{5-k}\\
			& + { 3 \choose 2} p^2 (1-p) \cdot \sum_{k=3}^{5} {5 \choose k} p^k (1-p)^{5-k}
	\end{align}
$$

We can calculate this in R.

```
p_success_stage_1 = function(p)
{
  return(p^3)
}

p_success_stage_2 = function(p)
{
  return(choose(3, 1) * p * (1-p)^2 * sum(dbinom(4:5, 5, p)) + choose(3,2) * p^2 * (1-p) * sum(dbinom(3:5, 5, p)))
}

p_success = function(p)
{
  return(p_success_stage_1(p) + p_success_stage_2(p))
}

# i.
p_success(p = 0.25)
# 0.03677368

# ii.
p_success( p = 0.50)
# 0.3828125

# iii.
p_success(p = 0.75)
# 0.8890686
```

When the true success rate is 0.25 we get a probability of success of 0.03677368, when it's 0.5 we get a probability of success of 0.3828125, and when it's 0.75 we get a probability of success of 0.8890686.

## b.
**For the same probabilities of response as in part (a), computer the expectd number of patients to be studied using the above two-stage decision rule.**

We can use our decision rule to figure out the expected number of patients to be studied. Note that there are two scenarios that the study can end in stage one: if no patients respond or if all three patients respond.

$$
	\begin{align}
		n_0 (P(End \ Stage \ 1)) + n (P(End \ Stage \ 2)) & = n_0 (P(End \ Stage \ 1)) + n (1 - P(End \ Stage \ 1))\\
		& = n_0( p^3 + (1-p)^3) + n (1 - (p^3 + (1-p)^3))
	\end{align}
$$

We can calculate this for each probability in R.

```
expected_sample_size = function(n, n0, p)
{
  p_stopping_stage_1 = p^3 + (1-p)^3
  return(n0 * p_stopping_stage_1 + n * (1 - p_stopping_stage_1 ))
}

# i.
expected_sample_size(n=8 , n0=3 , p=0.25)
# 5.8125

# ii.
expected_sample_size(n=8 , n0=3 , p=0.5)
# 6.75

# iii.
expected_sample_size(n=8, n0=3, p=0.75)
# 5.8125

```

Thus, for $\pi = 0.25$ and $\pi = 0.75$ we get an expected sample size of 6 and for $\pi = 0.5$ we get an expected sample size of 7.


#  4
**Suppose we are evaluating a new treatment in phase II. If the true response rate is 0.20 or less, then we want to declare the treatment a failure with at least 95% probability; whereas, if the true response rate is at least 0.35, then we want to declare the treatment a success with at least 90% probability. Describe the optimal two-stage design and the corresponding decision rule to achieve these goals. What is the expected sample size of this design when the true response rate is 0.20? (Use the tables provided in the slides.)**


Since $p_1 - p_0 = 0.15$, we will use the second table. With our $p$'s, we will look at the third row and with our probabilities we will look at the third sub-row. This shows us that we should have 37 people in the first stage and reject the drug if fewer than 8 of the respond. In the second stage we will have 83 patients and reject the drug if fewer than 22 of the respond. We have an expected sample size of 51.4 and a probabilty of early termination of 0.69.