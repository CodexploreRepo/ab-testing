# Daily Knowledge

## Day 1

- **Parametric** vs **Non-Parameteric**:
  - Parametric: `t-test`
  - Non-Parameteric: `Mann-Whitney U`
  - When to use ?
    - Normal data distribution and homogeneity of variances: Parametric tests
    - Otherwise: Non-parametric tests
- **Homogeneous** vs **Heterogeneous**:
  - **Heterogeneous** mixtures have visually distinguishable components
  - **Homogeneous**: mixtures appear uniform throughout.
    - Example 1: to check whether the variances are **homogeneous**, i.e. whether there is equality of variance.
- **Bootstrap** sample is taken from the original by using **sampling with replacement** (`replace=True`)

```python
sample_size=400

df.sample(n=sample_size, replace=True)
```

### AB Testing Assumption

- It is also important to ensure assumptions such as **data distribution** and **homogeneity** of **variances**.
- To test the normal distribution: use the **Shapiro-Wilk** test
- When these assumptions are met, parametric tests (e.g: t-test) can be used
- Otherwise: non-parametric tests (e.g Mann-Whitney U) are preferred.
