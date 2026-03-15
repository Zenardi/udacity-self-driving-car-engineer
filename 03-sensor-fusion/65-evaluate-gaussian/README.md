# Evaluate Gaussian

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=4-0nBfsD4jo)

## Summary

**Normal Distribution Calculator**
=====================================

This project calculates the value of a normal distribution function f(x) given certain parameters.

### Key Concepts

* **Normal Distribution**: A probability distribution that is symmetric about the mean, with data points clustering around the average.
* **Mean (μ)**: The average value of the dataset.
* **Variance (σ^2)**: A measure of how spread out the data is from the mean.
* **Standard Deviation (σ)**: The square root of the variance.
* **Exponential Function**: An expression used to calculate the probability density function of a normal distribution.

### Practical Notes

To use this calculator, you will need to provide the following values:

* `mu` (mean): 10
* `sigma_squared` (variance): 4
* `x`: 8

The calculator uses the formula for the normal distribution function f(x) = (1/σ√(2π)) \* e^(-((x-μ)^2)/(2σ^2))

Example output:
f(x) ≈ 0.12

## Transcript

Let me ask you to calculate the value of f(x)-- you will need a calculator for this-- for the following values: mu equals 10, sigma-squared equals 4, and x equals 8.

The approximate answer is 0.12. x minus mu squared is 4, this is 10 minus 8 to the square divided by 4 equals 1. The expression of the exponential is -1/2, which is about 0.6. This guy over here is approximately 0.2, which gives us as a product 0.12 I won't torture you with any more questions like these, because they're really not fun, but we can program this now.

## Images

![Evaluate Gaussian   f of x equals 1 over parentheses squareroot of 2 pi sigma squared parentheses closed. All of this is multiplied by exponent -½ multiplied by parenthesis x-mu parentheses closed squared over sigma squared.  mu equals 10. sigma squared equals 4. x equals 8.  what is f of x?](images/kalman-eval-gaussian.jpg)
*Quiz Information*


