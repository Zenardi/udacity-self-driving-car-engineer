# Maximize Gaussian

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=fRYtUP0P4Lg)

## Summary

**Gaussian Function Completion and Optimization**
=====================================================

This README file summarizes the key concepts and practical steps from a lesson on completing and optimizing the Gaussian function.

### Key Concepts
* **Gaussian Function**: A mathematical function that describes the probability distribution of a normal distribution, given by the formula: `f(x) = 1/sqrt(2*pi*sigma^2) * exp(-0.5*(x-mu)^2/sigma^2)`
* **Mu (μ)**: The mean or expected value of the normal distribution
* **Sigma (σ)**: The standard deviation of the normal distribution
* **X**: The input value for which the Gaussian function is evaluated

### Practical Notes
To complete the given source code, you need to modify the expression to return the Gaussian function with arguments `mu = 10`, `sigma^2 = 4`, and `x = 8`. The correct formula is:
```python
1/sqrt(2*pi*sigma**2) * exp(-0.5*(x-mu)**2/sigma**2)
```
To optimize the function for maximum return value, you need to set `x` equal to `mu`, which in this case is 10. This will result in a peak value of approximately 0.2.

Note: The code snippet provided in the lesson is incomplete and only shows the constant term of the Gaussian function. You need to modify it to include the exponential term as well.

## Transcript

Starting with the following source code, I'm looking for a completion of this one line over here that returns the Gaussian function with arguments mu = 10, sigma2 = 4, and x = 8, and I want the output to be approximately 0.12. Here's my solution. This is the constant: 1/sprt(2pisigma2). Then I multiply with the exponential of (-.5(x-mu)*2/sigma2). Applying that to the following numbers over here gives me 0.12.

Now, here's a question for you. How do I have to modify x the 8 to get the maximum return value for this function f? The answer is assess with the same value as mu, in which case this expression over here becomes zero, and we get the maximum. We get the peak of the Gaussian. We set x to the same value as mu, to 10, and the output is 0.2 approximately.

## Additional Content

## Maximize Gaussians

Note: Sebastian is still using Python 2 in the video, but the workspace below will use Python 3.

### Solution
