# Non-parametric Tests

## Wilcoxon-Mann-Whitney Test

- Wilcoxon-Mann-Whitney (to compare the mean of two group, an alternative to the t-test when the assumptions of normality or equal variances are not met)

### How to perform the hypothesis test using SciPy

- `scipy.stats.mannwhitneyu()` can be used to perform a Wilcoxon-Mann-Whitney test.
- The function takes three arguments: `x`, the values you suspect are higher from the hypotheses, `y`, the values to compare against, and `alternative`, a string indicating whether the test is left-tailed (`less`), right-tailed (`greater`), or two-tailed (`two-sided` the distributions are not equal)

```Python
from scipy.stats import mannwhitneyu
import numpy as np

# Sample data
sample_x = np.array([10, 12, 15, 18, 20])
sample_y = np.array([5, 7, 9, 11, 13])

# Perform Mann-Whitney U test with 'greater' alternative
statistic, pvalue = mannwhitneyu(sample_x, sample_y, alternative='greater')

print(f"Mann-Whitney U statistic: {statistic}")
print(f"P-value (alternative='greater'): {pvalue}")

# Interpret the results
alpha = 0.05
if pvalue < alpha:
    print("Reject the null hypothesis: Sample X is stochastically greater than Sample Y.")
else:
    print("Fail to reject the null hypothesis: No evidence that Sample X is stochastically greater than Sample Y.")
```

- Explanation of `alternative='greater'`:
  - When `alternative='greater'`, the null hypothesis is that the distribution underlying `sample_x` is not stochastically greater than the distribution underlying `sample_y`.
  - The alternative hypothesis is that the distribution underlying `sample_x` is stochastically greater than the distribution underlying `sample_y`.
  - The mannwhitneyu function calculates the **U statistic** and the corresponding p-value based on this one-sided hypothesis. If the p-value is below your chosen significance level (e.g., 0.05), you would reject the null hypothesis and conclude that sample_x is indeed stochastically greater than sample_y.

## Kruskal-Wallis Test

- Kruskal-Wallis test: ANOVA extends t-tests to more than two groups, the Kruskal-Wallis test extends the Wilcoxon-Mann-Whitney test to more than two groups.
- The Kruskal-Wallis test is a non-parametric version of ANOVA.

## Wilcoxon Signed-Rank Test

- Wilcoxon signed-rank test (equil. to paired t-test)
