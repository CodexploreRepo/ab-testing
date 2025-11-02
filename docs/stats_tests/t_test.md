# t-test

- Reference: [An Introduction to Python T-Tests](https://www.datacamp.com/tutorial/an-introduction-to-python-t-tests)

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
  - **Homogeneity of Variances (Equal variance)**: For an independent two-sample t-test, the variances of the two groups being compared are assumed to be equal. This assumption ensures that the t-test correctly accounts for variability within each group. If the variances are not equal, it can affect the accuracy of the test.
  - **Independence of Observations**: The observations within each group should be independent. This means that the value of one observation should not influence or be related to the value of another observation. Violation of this assumption can lead to incorrect conclusions.

## One-sample t-test

- For example: A company claims to produce ball bearings of 10 cm diameter (null hypothesis), and you decide to audit if that is true. You collect 21 ball bearings from multiple shops around the city and measure their diameter. You must determine if the company’s claim is false (alternate hypothesis) based on the measurements.

<p align="center"><img src="../../assets/img/one-sample-t-test.avif" width=400></p>

- To conduct a one-sample t-test in Python, we use the `scipy.stats.ttest_1samp()` function.

```Python
import numpy as np
from scipy import stats

# Population Mean
mu = 10

# Sample Size
N1 = 21

# Degrees of freedom
dof = N1 - 1

# Generate a random sample with mean = 11 and standard deviation = 1
x = np.random.randn(N1) + 11

# Using the Stats library, compute t-statistic and p-value
t_stat, p_val = stats.ttest_1samp(a=x, popmean = mu)
print("t-statistic = " + str(t_stat))
print("p-value = " + str(p_val))

# t-statistic = 4.689539773390642
# p-value = 0.0001407967502139183
```

- The value of t-statistic comes out to be 4.69 which seems to be very far from the mean of zero in a t-distribution.
- The p-value is less than the default significance level of 0.05, which indicates that the probability of such an extreme outcome is close to zero and that the null hypothesis can be rejected.

## Two-sample t-test

### Example 1

- The company sets up another factory to produce identical ball bearings. We need to find out if the ball bearings from the two factories are of different sizes
- The first factory shares 21 samples of ball bearings where the mean diameter of the sample comes out to be 10.5 cm. On the other hand, the second factory shares 25 samples with a mean diameter of 9.5 cm. Both have a standard deviation of 1 cm.

```Python
# Sample Sizes
N1, N2 = 21, 25

# Degrees of freedom
dof = min(N1,N2) - 1
# Data Generation for this example. In the real world, we will use the actual data instead of synthetic data
# Gaussian distributed data with mean = 10.5 and var = 1
x = np.random.randn(N1) + 10.5

# Gaussian distributed data with mean = 9.5 and var = 1
y = np.random.randn(N2) + 9.5

## Using the internal function from SciPy Package
t_stat, p_val = stats.ttest_ind(x, y)
print("t-statistic = " + str(t_stat))
print("p-value = " + str(p_val))

# t-statistic = 3.18913308431476
# p-value = 0.0026296199823557754
```

- Referring to the p-value of 0.0026 which is less than the significance level of 0.05, we reject the null hypothesis stating that the bearings from the two factories are not identical.

### Example 2

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

### Welch’s t-test

- The company needs to identify if the ball bearings from the two factories are different by comparing 21 samples from the first factory and 25 from the second factory.
- The mean diameter of bearings from the first factory turns out to be 9.9 cm with a standard deviation of 1 cm, whereas the mean diameter from the second factory turns out to be 10 cm with a standard deviation of 3 cm.
- As the standard deviation of the two samples is different, we will use Welch’s t-test.

```Python
# Sample Sizes
N1, N2 = 21, 25

# Degrees of freedom
dof = min(N1,N2) - 1

# Gaussian distributed data with mean = 9.9 and var = 1
x = np.random.randn(N1) + 9.9

# Gaussian distributed data with mean = 10 and var = 3
y = 3*np.random.randn(N2) + 10

## Using SciPy Package
t_stat, p_val = stats.ttest_ind(x, y, equal_var = False)
print("t-statistic = " + str(t_stat))
print("p-value = " + str(p_val))
```

## Paired t-test

### Example 1

- Upon sharing these results with the company, it decides to improve its manufacturing technology by introducing a new casting machine.
- It starts this pilot from one of the factories and conducts a test to identify if the new casting machine leads to a change in the diameter of the bearings by comparing two samples of 25 bearings – one **before** the new machine was introduced and the other sample **after** it.
- The mean diameter comes out to be 10.5cm and 9.9cm, respectively.

```Python
# Sample Sizes
N = 25

# Degrees of freedom
dof = N - 1

# Gaussian distributed data with mean = 10.5 and var = 1
x = np.random.randn(N) + 10.5

# Gaussian distributed data with mean = 9.9 and var = 1
y = np.random.randn(N) + 9.9

t_stat, p_val = stats.ttest_rel(x,y)
print("t-statistic = " + str(t_stat))
print("p-value = " + str(p_val))

# t-statistic = 3.446152658909739
# p-value = 0.0021043953630465787
```

### Example 2

- For paired analyses, rather than considering the two variables separately, we can consider a single variable of the difference.
<p align="center"><img src="../../assets/img/paired-t-test.png" width=700></p>

<p align="center"><img src="../../assets/img/paired-t-test-1.png" width=700></p>

<p align="center"><img src="../../assets/img/paired-t-test-2.png" width=700></p>

<p align="center"><img src="../../assets/img/paired-t-test-3.png" width=700></p>

- For a converted one sample test like this, y specifies the hypothesized difference value from the null hypothesis, which is zero (y=0).

<p align="center"><img src="../../assets/img/paired-t-test-4.png" width=700></p>
