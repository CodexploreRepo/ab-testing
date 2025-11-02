# t-test

## t-distribution

- The test statistic, t, follows a t-distribution. t-distributions have a parameter called the **degrees of freedom**, or df for short.
- As we increase the degrees of freedom, the t-distribution gets closer to the normal distribution. In fact, a normal distribution is a t-distribution with infinite degrees of freedom.

<p align="center"><img src="../../assets/img/t-distribution.png" width=500></p>

<p align="center"><img src="../../assets/img/t-distribution-dof.png" width=500></p>

### DoF calculation

- Suppose our dataset has 5 independent observations, and that four of the values are 2, 6, 8, and 5. Suppose we also know the sample mean is 5. With this knowledge, the fifth value is no longer independent.
- In our two sample case, there are as many degrees of freedom as observations (number of childs $n_{child}$ + number of aldult $n_{adult}$), minus 2 because we know two sample statistics, the means for each group.

<p align="center"><img src="../../assets/img/t-distribution-dof-2.png" width=500></p>

## Assumptions of the t-test

- The t-test relies on certain assumptions to provide valid results:
  - **Normality of the Data**: The t-test assumes that the data in each group are approximately normally distributed. This is especially important when dealing with small sample sizes. If the data are not normally distributed, the t-test results may be unreliable.
  - **Homogeneity of Variances**: For an independent two-sample t-test, the variances of the two groups being compared are assumed to be equal. This assumption ensures that the t-test correctly accounts for variability within each group. If the variances are not equal, it can affect the accuracy of the test.
  - **Independence of Observations**: The observations within each group should be independent. This means that the value of one observation should not influence or be related to the value of another observation. Violation of this assumption can lead to incorrect conclusions.

## Two-sample t-test

<p align="center"><img src="../../assets/img/2-sample-test.png" width=700></p>

- In the two sample case, the test statistic, denoted `t`, uses a similar equation as z-score (z-scores are calculated by taking the sample statistic, subtracting the mean of this statistic as the population parameter of interest, then dividing by the standard error).
- We take the difference between the sample statistics for the two groups, subtract the population difference between the two groups, then divide by the standard error.

<p align="center"><img src="../../assets/img/2-sample-test-1.png" width=700></p>
<p align="center"><img src="../../assets/img/2-sample-test-2.png" width=700></p>
<p align="center"><img src="../../assets/img/2-sample-test-3.png" width=700></p>
<p align="center"><img src="../../assets/img/2-sample-test-4.png" width=700></p>

- Degree of freedom minus 2 because we know the 2 sample means of the population.

<p align="center"><img src="../../assets/img/2-sample-test-5-dof.png" width=700></p>
<p align="center"><img src="../../assets/img/2-sample-test-6.png" width=700></p>

## Paired t-test

- For paired analyses, rather than considering the two variables separately, we can consider a single variable of the difference.
<p align="center"><img src="../../assets/img/paired-t-test.png" width=700></p>

<p align="center"><img src="../../assets/img/paired-t-test-1.png" width=700></p>

<p align="center"><img src="../../assets/img/paired-t-test-2.png" width=700></p>

<p align="center"><img src="../../assets/img/paired-t-test-3.png" width=700></p>

- For a converted one sample test like this, y specifies the hypothesized difference value from the null hypothesis, which is zero (y=0).

<p align="center"><img src="../../assets/img/paired-t-test-4.png" width=700></p>
