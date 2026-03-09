# Separated Gaussians 2

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=0FmTokjoRgo)

## Summary

**Understanding Gaussian Distributions and Variance**

This README file provides a summary of key concepts related to Gaussian distributions and variance. It covers the intuition behind choosing the correct type of Gaussian distribution for a given problem.

### Key Concepts

* **Gaussian Distribution**: A probability distribution that is symmetric about its mean, showing that data near the mean are more common and data far from the mean are less common.
* **Variance**: A measure of how spread out the values in a dataset are. In this context, it's used to determine the width of the Gaussian distribution.
* **Sigma-squared (σ^2)**: The variance of a Gaussian distribution. It's calculated using the formula `1 / (1/σ^2)`, which simplifies to `σ^2 / 2`.
* **Peakedness**: A measure of how focused or spread out a Gaussian distribution is. A more peaked distribution has less variance and is more certain.

### Practical Notes

When faced with multiple possible Gaussian distributions, consider the following:

* If you have two initial measurement probabilities with different means, choose a wider Gaussian distribution to account for the uncertainty.
* However, if both means are the same, the new variance squared will be half of the old one, resulting in a narrower and more peaked Gaussian distribution.

Remember that this is a counter-intuitive concept, but understanding it can help you make more informed decisions when working with Gaussian distributions.

## Transcript

<v English>Let me ask the hard question now.</v> <v English>Will it be a Gaussian like this where the variance is larger,</v> <v English>a Guassian with the exact same variance,</v> <v English>or an even more peaked Guassian that's more certain</v> <v English>than the two original factors in this calculation.</v> <v English>Please check exactly one of the three boxes over here.</v>

<v English>The answer is it's the more peaked Gaussian.</v> <v English>That is somewhat counter-intuitive.</v> <v English>You'd think if this was your initial measurement probability</v> <v English>you really don't know where you are, and you should pick a very wide Gaussian.</v> <v English>But the truth is our new sigma-squared is obtained independent of the means.</v> <v English>It's this formula over here.</v> <v English>Now because both means are the same, this resolves to 1 over 1/σ^2.</v> <v English>That's the same as σ^2 over 2,</v> <v English>which means a new variance squared is half of the old one.</v> <v English>That makes it a narrower Gaussian,</v> <v English>so the green one here that's the most peaked is indeed the correct answer.</v> <v English>This is very counter-intuitive, but now we understand why.</v> <v English>I hope you feel comfortable with the fact that we have actually gotten</v> <v English>more information about the location, which is manifest by a more focused estimate.</v>

## Images

![There are two gaussians sitting at an unspecified distance from one another. Both have the same covariance. How "peaky"/confident will the new gaussian be? ](images/kalman-separated-gauss-2.jpg)
*Quiz Options*

## Additional Content

## Separated Gaussians 2

### Quiz Image

### Solution

Correction: Sebastian says "because both means are the same" at 0:24, it should be "because both **variances** are the same".
