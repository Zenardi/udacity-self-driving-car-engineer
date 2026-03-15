# Separated Gaussians

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=QAqsIWVVX0Y)

## Summary

**Bayesian Update: Averaging Means with Equal Variances**
===========================================================

This README file summarizes the key concepts and practical notes from a lesson on Bayesian update, specifically when dealing with equal variances.

### Key Concepts

* **Prior Distribution**: The initial probability distribution that represents our prior knowledge or beliefs about a parameter.
* **Measurement Probability**: The probability distribution of a measurement or observation, which updates our prior knowledge.
* **Covariance**: A measure of how much two variables change together. In this case, both the prior and measurement probabilities have the same covariance.
* **Bayesian Update**: The process of updating our prior distribution with new information from measurements to obtain a posterior distribution.

### Practical Notes

When updating our mean using Bayesian update, if the variances of the prior and measurement distributions are equal, we can simply average the means. This is because the two distributions have the same spread or dispersion, making them equally informative about the true mean.

**Example Code**
```python
# Define the prior mean and variance
prior_mean = 10
prior_variance = 1

# Define the measurement mean and variance (same as prior)
measurement_mean = 15
measurement_variance = 1

# Calculate the new mean by averaging the means
new_mean = (prior_mean + measurement_mean) / 2
```
Note that this is a simplified example, and in practice, you would need to consider more complex scenarios and handle edge cases.

## Transcript

Let me ask you a different quiz, which from the math, but it tests your intuition. Suppose we have a prior that sits over here and a measurement probability that sits over here--really far away-- and both have the same covariance. Let me first quiz you where the new mean would be. Is it going to be here, here, here, or here? Please check the corresponding check mark.

<v English>The answer is here. It's in the middle.</v> <v English>It's in the straight middle, because these two variances are the same,</v> <v English>so we just average the means.</v>

## Images

![There are two gaussians sitting at an unspecified distance from one another. Both have the same covariance. Where would the new mean be? Option A is closer to the first gaussian, option B is in between, option C is closer to the second gaussian, and option D is not between either.](images/kalman-separated-gauss.jpg)

