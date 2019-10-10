---
layout: post
comments: false
title: Example Problems on Sample Size Calculations
description: ST520 Homework 4 on Sample Size Calculations
tags: ST520 Statistics Clinical-Trials Sample-Size Calculations
---

Problems: 1, 2, 3, 4

* Do not remove this line (it will not be displayed)
{:toc}


# 1
**You are asked to help design a clinical trial to assess a new anti-hypertensive drug that is targeted for patients with mild hypertension (high blood pressure). After discussions with the clinical investigator it is decided to conduct a randomized clinical trial where patients with mild hypertension are randomized to either placebo or the new anti-hypertensive drug. Because the investigator would like to get more experience on the possible side effects of the new drug it is also decided that patients will be randomized to the new drug with probability 2/3 so that twice as many patients will receive the new drug as compared to placebo. The primary outcome will be systolic blood pressure three months after randomization. You are specifically asked to determine the appropriate sample size. After discussions with the clinical investigator you determine that the standard deviation of systolic blood pressure (based on prior data) is roughly 25mm. The investigator feels that if the new drug can decrease the population mean systolic blood pressure for such mildly hypertensive patients by 5mm or more than this would be an important difference that we would want to find significant with at least 80% power using a one-sided test at the .025 level of significance. For planning purposes you
should assume the standard deviation of systolic blood pressure on the new drug is the same as on placebo (i.e., 25mm).**


## (a)
**Using clear notation state the null hypothesis and alternative hypothesis that will be tested.**

$$
	\begin{align}
		H_0: & \mu_1 - \mu_2 \leq 5 \\
		H_A: & \mu_1 - \mu_2 > 5
	\end{align}
$$

## (b)
**What test statistic would you use?**

Since we are assuming that the variances are the same, we can use a Pooled Two Sample T-Test.


$$
T = \frac{ \bar{Y_1} - \bar{Y_2} }{ S_P	\sqrt{\frac{ 1 }{ n1 } + \frac{ 1 }{ n_2 }} }
$$


## (c)
**What sample size would you recommend based on the considerations above (i.e., the number of patients on placebo and new drug).**


$$
	\begin{align}
		z_{\alpha} + z_{\beta} & = \frac{ \Delta }{ \sigma \cdot \sqrt{\frac{ 1 }{ n_1 } + \frac{ 1 }{ n_2 }} }\\
		z_{\alpha} + z_{\beta} & = \frac{ \Delta }{ \sigma \cdot \sqrt{\frac{ 1 }{ 2/3 n } + \frac{ 1 }{ 1/3 n }} }\\
		z_{\alpha} + z_{\beta} & = \frac{ \Delta }{ \sigma \cdot \sqrt{\frac{ 9 }{ 2n }} }\\
		n & = \Big( \frac{ \sigma \cdot (z_{\alpha} + z_{\beta}) }{ \Delta } \Big)^2\cdot \frac{ 9 }{ 2 } \\
			& = \frac{9}{2} \left(\frac{25}{5} (1.96\, +2.05)\right)^2 \\
			& = 1809.01 \approx 1812 \\ \\
		n_1 = 1812 \cdot 2/3 & = 1208  \\
		n_2 = 1812 \cdot 1/3 & = 604
	\end{align}
$$

## (d)
**What sample size would you recommend if you were to randomize with equal probability (equal allocation) to the two treatments (placebo and new drug)?**

$$
	\begin{align}
		\frac{ 1 }{ 2n } + \frac{ 1 }{ 2n } & = \Big( \frac{ \sigma \cdot (z_{\alpha} + z_{\beta}) }{ \Delta } \Big)^2 \\
		n & = \Big( \frac{ \sigma \cdot (z_{\alpha} + z_{\beta}) }{ \Delta } \Big)^2 \cdot 4 \\
			& = 4 \left(\frac{25}{5} (1.96\, +2.05)\right)^2 \\
			& = 1608.01 \approx 1610\\
		n_1 = n_2 & = 1/2 n = 805
	\end{align}
$$


#  2
**Another randomized clinical trial comparing another anti-hypertensive drug (coded as treatment 1) to placebo (coded as treatment 2) was completed. In this trial patients were randomized with probability .5 on placebo and drug respectively. The results of this clinical trial are summarized in the following table. Note that the sample sizes used are not related to the design considerations of question 1.**


$$
	\begin{array}{c c c c}
		\text{treatment} & \text{sample average} & \text{sample standard deviation} & \text{sample size} \\
		1 & 135.8 & 24.6 & 200 \\
		2 & 142.5 & 23.7 & 195
	\end{array}
$$

**If we denote $Y_{ij}$ the response (systolic blood pressure after three months) for the $i$-th individual treatment $j$, where $j=1,2$ and $i=1,\dots, n_j$, then the treatment-specific  sample average is**

$$
\bar{Y_j} = \frac{ \sum_{i=1}^{n_j} Y_{ij} }{ n_j }, \ j=1,2
$$

**and the sample standard deviation is**

$$
s_j = \sqrt{\frac{ \sum_{i=1}^{n_j} \Big( Y_{ij} - \bar{Y_j} \Big)^2 }{ n_j-1 }}, \ j=1,2
$$


## (a)
**What test statistic would you use to test for treatment difference and compute the value of this statistic using the data above.**


## (b)
**Compute the p-value and use this to make conclusions on whether or not the anti-hypertensive drug is effective.**


#  3
**You are also consulted to help design yet another clinical trial, in this case, comparing two treatments for patients after a myocardial infarction (heart attack) with the goal of increasing survival after a heart attack. The primary outcome is the binary outcome of whether a patient survives six months after randomization where time is measured after the randomized treatment is administered to the patient after his/her myocardial infraction. Based on current information for such patients it is expected that roughly 80% will survive six months after treatment for their heart attack. If one of these two treatments is effective then it is felt that it would be important to detect an increase of 10% in six month survival (i.e., from .80 to .90) with 90% power using a two-sided test at the .05 level of significance. Randomization to the two treatments will be with equal probability and all patients will be followed for at least six months so there will be no issue of censored observations. Consequently, the primary outcome is the binary outcome of
whether a patient survives six months or not.**


## (a)
**Using the design considerations above compute the sample size that you would recommend if you were to use the proportions test to test for significance. Show all your calculations.**



## (b)
**Using the design considerations above compute the sample size that you would recommend if you were to use the test based on the arc sine square root transformation test to test for significance. Show all your calculations.**


#  4
**Another group of investigators went ahead and conducted such a clinical trial without consulting a statistician. In this clinical trial a total of 150 patients were randomized. Of the 73 patients randomized to treatment 1, 54 survived six months; and among the 77 patients randomized to treatment 2, 63 survived six months.**

## (a)
**Compute the two-sided p-value using the proportions test.**



## (b)
**Compute the two-sided p-value using the arc sine square-root transformation.**


## (c)
**Based on these results what would you conclude?**



## (d)
**In view of the answer you gave on question 3 what would you conclude regarding whether there is truly a treatment difference?**