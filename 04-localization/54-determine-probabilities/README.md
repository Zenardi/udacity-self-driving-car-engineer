# Determine Probabilities

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6IhtnM1e0IY)

## Summary

**Gaussian Distribution in Common Spaces**
=============================================

This README file summarizes the key concepts and practical notes from a lesson on Gaussian distribution in common spaces.

### Key Concepts

* **Gaussian**: A continuous function over the space of locations that sums up to one.
* **Parameters**: Two parameters characterize a Gaussian: **mean (μ)** and **variance (σ²)**, also known as the width of the Gaussian.
* **Quadratic variable**: The variance is often written as σ², which is a quadratic variable.
* **1-D parameter space**: A 1-dimensional parameter space means that any Gaussian is characterized by μ and σ².
* **Formula**: The exact formula for a Gaussian is an exponential of a quadratic function: `exp(- (x - μ)² / (2σ²))`.
* **Normalization constant**: To normalize the Gaussian, we divide by the square root of 2πσ². However, this constant is not relevant to our discussion.

### Practical Notes

To understand how a Gaussian distribution works in common spaces, let's consider an example:

* If `X` equals `μ`, then the numerator becomes 0 and we have `exp(0) = 1`.
* The formula for a Gaussian can be used to calculate the probability density of a location `X` given its mean `μ` and variance `σ²`.

Note: This summary focuses on the key concepts and practical notes from the lesson. For more information, please refer to the original transcript or additional resources provided by Udacity.

## Transcript

In common features the distribution is given by what's called a Gaussian. Gaussian is a continuous function over the space of locations in the area underneath sums up to one. So use our Gaussian again and if we call the space X then the Gaussian is characterized by two parameters. The mean, often abbreviated with the Greek letter Mu, and the width of the Gaussian, often called the variance. And for reasons that I don't want to go into, it's often written as a quadratic variable, Sigma square so any Gaussian is 1-D, which means the parameter space of a year is one dimensional, is characterized by Mu and Sigma squared. Our task in common spaces is to maintain a Mu and a Sigma squared as our best estimate of the location of the option we are trying to find. The exact formula is an exponential of a quadratic function. If we take the exponent of this complicated expression over here, the quadratic difference of our query point X relative to the mean Mu divided by Sigma square by [inaudible] minus a half. Now if X equals Mu then the enumerator becomes 0 and we have exp of zero which is one. It turns out we have to normalize this by a constant, one over the squared root of two Pi Sigma squared. But for every thing we talked about today this constant won't matter so ignore it. What matters is we have an exponential of a quadratic function over here. So let me draw you a couple of functions and you tell me which one you believe are Gaussian by checking the box on the right side. And please excuse my poor drawing skills here.

## Additional Content

To implement these models in code, we need a function to which we can pass model parameters/values and return a probability.  Fortunately, we can use a normalized probability density function (PDF).  Let's revisit Sebastian's discussion of this topic.

We have implemented this Gaussian Distribution as a C++ function, ```normpdf```, and will practice using it at the end of this concept.  ```normpdf``` accepts a value, a parameter, and a standard deviation, returning a probability.  

## Additional Resources for Gaussian Distributions
- [Udacity's Statistics Course content on PDF](https://classroom.udacity.com/courses/st095/lessons/86217921/concepts/1020887710923)
- [Normal Distributions](http://mathworld.wolfram.com/NormalDistribution.html)
- [Probability Density Functions](http://stattrek.com/statistics/dictionary.aspx?definition=Probability_density_function)
Let's practice using ```normpdf``` to determine transition model probabilities.  Specifically, we need to determine the probability of moving from $x_{t-1}$ --> $x_t$ .  The value entered into ```normpdf``` will be the distance between these two positions.  We will refer to potential values of these positions as pseudo position and pre-pseudo position.  For example, if our pseudo position x is 8 and our pre-pseudo position is 5, our sample value will be 3, and our transition will be from x - 3 --> x.  

To calculate our transition model probability, pass any difference in distances into ```normpdf``` using our control parameter and position standard deviation.
