# Parameter Update

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=d8UrbKKlGxI)

## Summary

**Gaussian Multiplication and Kalman Update**

This README file provides a summary of the key concepts and practical steps introduced in the lesson on Gaussian multiplication and the Kalman update step.

### Key Concepts

* **Bayes Rule**: The process of updating a prior probability distribution with new measurement data to obtain a posterior probability distribution.
* **Gaussian Multiplication**: The process of multiplying two Gaussian distributions, resulting in a new Gaussian distribution that represents the updated probability distribution.
* **Weighted Mean**: A formula for calculating the mean of a weighted sum of values, where each value is multiplied by its corresponding weight and then summed.
* **Variance Update**: An equation for updating the variance of a Gaussian distribution after multiplying it with another Gaussian distribution.

### Practical Notes

To practice the equations introduced in this lesson, you can use the following example:

Suppose we have two Gaussians with equal variance but different means: μ = 10, σ^2 = 4, ν = 12, r^2 = 4. We want to compute the new mean and variance after updating these distributions using Bayes rule.

**Code Block**
```python
import numpy as np

# Define the parameters of the Gaussians
mu = 10
sigma_squared = 4
nu = 12
r_squared = 4

# Compute the weights for the weighted mean
weight_mu = r_squared / (r_squared + sigma_squared)
weight_nu = sigma_squared / (r_squared + sigma_squared)

# Compute the new mean
new_mean = weight_mu * mu + weight_nu * nu

# Compute the new variance
new_variance = 1 / (1/r_squared + 1/sigma_squared)

print("New Mean:", new_mean)
print("New Variance:", new_variance)
```
This code block demonstrates how to compute the new mean and variance after updating two Gaussians using Bayes rule.

## Transcript

Suppose we multiply two Gaussians as in Bayes rule-- a prior and a measurement probability. The prior has a mean of mu and a variance of sigma-squared. The measurement has a mean of nu and a covariance of r-squared. Then the new mean, mu prime, is the weighted sum of the old means where mu is weighted by r-squared and nu is weighted by sigma-squared normalized by the sum of the weight factors. The new variance term--I'm going to write sigma-squared prime here for the new one after the update--is given by this equation over here.

Let's put this into action. We have a weighted mean over here. Clearly, the prior Guassian has a much higher uncertainty. Therefore sigma-squared is larger. That means that nu is weighted much, much larger than the mu.

So the mean will be closer to the nu than the mu, which means that it'll be somewhere over here. Interestingly enough, the variance term is unaffected by the actual means. It just uses the previous variances and comes up with a new one that's even peakier. The result might look like this. This is the Kalman situation for the measurement update step where this is the prior, this is the measurement probability, and this is the posterior.

Let's practice these equations with a simple quiz. Here are our equations again. Suppose I use the following Gaussians: [μ = 10, σ^2 = 4, ν = 12, r^2 = 4] These are Gaussians with equal variance but different means that might look as follows. Compute for me the new mean after the update and the new sigma-squared. The answer for the new mean is just the one in the middle, and reason is both weights over here are equivalent, so we take the mean between mu and nu, which is 11.

Then sigma-squared is 2. If you take 1/4 plus 1/4, then you get 1/2, so 1 over 1/2 equals 2, which means the new variance term is half the size of the previous variance terms

## Images

![mu prime equals 1 over sigma squared plus r squared all multiplied by parentheses r squared mu plus sigma squared v parentheses closed.  The second equation is sigma squared prime equals 1 over parentheses 1 over sigma squared parentheses closed added to 1 over r squared.  mu here equals 10.  v equals 12.  sigma squared equals 4.   r squared equals 4.](images/kalman-param-update-1.jpg)
*Quiz Information*

## Additional Content

## Parameter Update

The equations in the video are:

$\LARGE \mu^\prime = \frac{1}{\sigma^2 + r^2} \times (r^2 \times \mu + \sigma^2 \times \nu)$

$\LARGE \sigma^{2\prime} = \frac{1}{\frac{1}{\sigma^2} + \frac{1}{r^2}}$

Where

$\mu^\prime$

("mu prime") is the new mean,

$\sigma^{2\prime}$

("sigma squared prime") is the new variance,

$r^2$

("r squared") is the measurement variance, and

$\nu$

("nu") is the measurement mean (

$\mu$

and

$\sigma^2$

are the mean and variance of the prior, respectively).
### Quiz Image

### Solution
