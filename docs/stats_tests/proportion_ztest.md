# Proportion Test (Z test)

## One-sample Proportion Test (Z test)

- A one-sample proportion test is used to determine whether the observed sample proportion of successes significantly differs from a hypothesized population proportion.
- [For example](https://stataiml.com/posts/52_one_sample_prop_test_py/): A company wanted to test the impact of marketing on a product sale. The current sale is 60%. A survey was completed on 500 individuals and 350 individuals purchased the product. The company wanted to check whether there is enough evidence to show that the proportion of sales of products is different than the current sales.
  - The number of successes (product sales) is 350 out of 500 (~70%)
  - Null Hypothesis (H0): Sample proportion is equal to the hypothesized population proportion of 60% (two-tailed)
  - Alternative Hypothesis (Ha): Sample proportion is not equal to the hypothesized population proportion of 60%
  - For a one-sample proportion Z test, there are a total of 500 observations, 350 successes (product sales), and 0.6 is the hypothesized population proportion.

```Python
# import package
import statsmodels.api as sm

# perform one-sample proportion Z test
stat, pval = sm.stats.proportions_ztest(count=350, nobs=500, value=0.6)

print(stat, pval)

# output
# 4.879500364742665 1.0635492679527416e-06
# The Z Statistic: 4.87; and p value: < 0.05

```

## Two-sample Proportion Test (Z test)

- Two-sample proportion test is used for comparing the proportions (e.g. number of successes) in two groups to determine if there are significant differences between the two groups.
- This is useful in scenarios such as comparing the success rates of two different treatments or the preferences of two different groups.
- In Python, you can use `proportions_ztest` function from `statsmodels` package to perform a two-sample proportion Z test.
- [For example](https://stataiml.com/posts/53_two_sample_prop_test_py/): Suppose a marketing survey is completed in two cities (A and B) with 500 individuals for a purchase of the product. In city A, 300 individuals purchased the product and in city B, 400 individuals purchased the product. The number of successes in cities A and B are 300 and 400, respectively.

```Python
# import package
import numpy as np
import statsmodels.api as sm

# number of successes in each city
count = np.array([300, 400])

# total number of observations in each city
nobs = np.array([500, 500])


# perform Two-proportion Z test package
stat, pval = sm.stats.proportions_ztest(count, nobs, alternative="two-sided")

print(stat, pval)

# output
# (-6.900655593423544, 5.176309056990089e-12)
```

- In addition to Z test, you can also perform the two-sample proportion test using the **chi-squared** test

### Chi Square Test

- Suppose a marketing survey is completed in two cities (A and B) with 500 individuals for a purchase of the product.
  - In city A, 300 individuals purchased the product, and
  - In city B, 400 individuals purchased the product.
- The number of successes in cities A and B are 300 and 400, respectively.

```Python
# import package
import numpy as np

# Create the contingency table
contingency_table = np.array([[300, 200],
                 [400, 100]])
# import package
from scipy.stats import chi2_contingency

# perform the chi-square test for proportion
chi2, p, dof, exp_prop = chi2_contingency(contingency_table)

print(chi2, p, dof, exp_prop)

# output
# 46.67142857142857 8.394401757688147e-12 1 [[350. 150.][350. 150.]]
```
