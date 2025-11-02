# AB Testing

## Table of Content

- [Hypothesis Testing Fundamentals](./docs/hypothesis_testing_fundamentals.md)
- **Parametric** Tests: t-test, z-test, ANOVA **assuming a normal distribution** & require sufficiently large sample size
  - [**t-test**](./docs/stats_tests/t_test.md)
    - _Unpaired t-test_ (Test for differences in sample means between two groups) using t-tests & extend this to more than two groups using ANOVA & pairwise t-test
    - _Paired t-test_: test for same group at different periods
  - [Proportion Test (**z-test**)](./docs/stats_tests/proportion_ztest.md): test differences in sample proportions between two groups
  - [**Chi-square**: test of independence & goodness of fit test](./docs/stats_tests/chi_square_test.md)
- [**Non-parametric** Tests](./docs/stats_tests/non-parametric-test.md): used when data is **not normally distributed**
  - Wilcoxon-Mann-Whitney (to compare the mean of two group, an alternative to the t-test when the assumptions of normality or equal variances are not met)
  - Kruskal-Wallis test: ANOVA extends t-tests to more than two groups, the Kruskal-Wallis test extends the Wilcoxon-Mann-Whitney test to more than two groups.
  - Wilcoxon signed-rank test (equil. to paired t-test)

## Appendix

- [Z-score & Standard Normal (z) distribution](./docs/concepts/z_score.md)
- [Bootstrap Sampling](./docs/concepts/boostrap_sampling.md)
- [Confidence Intervals](./docs/concepts/confidence_intervals.md)

## Environment Setup

- Create the new conda environment (if not exist): `conda create -n ab_testing`
- Activate the environment: `conda activate ab_testing`
- Install dependencies:

## Reference

- [Hypothesis Testing in Python](https://app.datacamp.com/learn/courses/hypothesis-testing-in-python)
- [Customer Analytics and A/B Testing in Python](https://app.datacamp.com/learn/courses/customer-analytics-and-ab-testing-in-python)
- [Bayesian Data Analysis in Python](https://app.datacamp.com/learn/courses/bayesian-data-analysis-in-python)
