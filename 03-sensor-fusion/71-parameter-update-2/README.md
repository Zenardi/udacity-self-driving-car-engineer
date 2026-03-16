# Parameter Update 2

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2BfisMbu86o)

## Summary

**Weighted Mean and Variance Calculation**
=============================================

This project demonstrates how to calculate the weighted mean and variance when dealing with imbalanced distributions.

### Key Concepts
* **Weighted Mean**: A calculation that takes into account the relative importance of each data point, represented by its weight.
* **Variance**: A measure of the spread or dispersion of a dataset.
* **Gaussian Distribution**: A probability distribution that models real-valued random variables with a bell-shaped curve.

### Key Formulas
* Weighted Mean: μ' = (Σw_i \* x_i) / Σw_i
* Variance: σ'^2 = 1 / (∑(1/σ_i^2))
* Normalization Factor: N = ∑w_i

### Practical Notes
To calculate the weighted mean and variance, follow these steps:

1. Identify the weights (w_i) for each data point.
2. Calculate the weighted sum of the data points using the formula μ' = (Σw_i \* x_i) / Σw_i.
3. Calculate the normalization factor N = ∑w_i.
4. Calculate the variance σ'^2 = 1 / (∑(1/σ_i^2)).

Example:
Given a mean of 10 and 13, with variances 8 and 2 respectively, we can calculate the resulting mu prime (μ') and sigma-squared prime (σ'^2) as follows:

* μ' = (2 \* 10 + 8 \* 13) / (2 + 8) = 124 / 10 = 12.4
* σ'^2 = 1 / ((1/8) + (1/2)) = 1 / (5/8) = 8/5 = 1.6

Note that the resulting variance is smaller than each of the two variances, indicating a more peaked distribution centered on 13.

## Transcript

Let's do this again. Suppose our mean is 10 and 13, and the variances are imbalanced--8 and 2-- which corresponds to the following picture. There's a relatively shallow distribution centered on 10 and a much more peaked distribution centered on 13. Compute for me what the resulting mu prime and sigma-squared prime are.

With a little bit of math we find that the new mean is 12.4, and the new sigma-squared is 1.6. 12.4 is much closer to 13 than 10, and that's because the Gaussian centered on 13 has a much narrower variance than the one on 10. We find the resulting variance is smaller than each of the two variances over here. In particular, let's start with the variance. 1 over 1/8 plus 1/2 is the same as 1 over 5/8, which results in 8/5 or 1.6. This is just applying this formula over here. For the weighted average we get 2 times 10 plus 8 times 13. Then we normalize by the sum of those two things over here. So this is 124 divided by 10, which gives us 12.4.

## Images

![Parameter mu prime equals 1 over sigma squared plus r squared all multiplied by parentheses r squared mu plus sigma squared v parentheses closed.  The second equation is sigma squared prime equals 1 over parentheses 1 over sigma squared parentheses closed added to 1 over r squared.  mu here equals 10.  v equals 13.  sigma squared equals 8.   r squared equals 2.](images/kalman-param-update-2.jpg)

### Solution

[Watch on YouTube](https://www.youtube.com/watch?v=_AAkw_fynwc)

