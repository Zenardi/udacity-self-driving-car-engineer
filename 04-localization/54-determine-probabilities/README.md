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

<v English>In common features the distribution is given by what's called a Gaussian.</v> <v English>Gaussian is a continuous function over the space of</v> <v English>locations in the area underneath sums up to one.</v> <v English>So use our Gaussian again and if we call</v> <v English>the space X then the Gaussian is characterized by two parameters.</v> <v English>The mean, often abbreviated with the Greek letter Mu,</v> <v English>and the width of the Gaussian,</v> <v English>often called the variance.</v> <v English>And for reasons that I don't want to go into,</v> <v English>it's often written as a quadratic variable,</v> <v English>Sigma square so any Gaussian is 1-D,</v> <v English>which means the parameter space of a year is one dimensional,</v> <v English>is characterized by Mu and Sigma squared.</v> <v English>Our task in common spaces is to maintain a Mu and a Sigma squared</v> <v English>as our best estimate of the location of the option we are trying to find.</v> <v English>The exact formula is an exponential of a quadratic function.</v> <v English>If we take the exponent of this complicated expression over here,</v> <v English>the quadratic difference of our query point X relative to</v> <v English>the mean Mu divided by Sigma square by [inaudible] minus a half.</v> <v English>Now if X equals Mu then the enumerator becomes 0 and we have exp of zero which is one.</v> <v English>It turns out we have to normalize this by a constant,</v> <v English>one over the squared root of two Pi Sigma squared.</v> <v English>But for every thing we talked about today this constant won't matter so ignore it.</v> <v English>What matters is we have an exponential of a quadratic function over here.</v> <v English>So let me draw you a couple of functions and you tell me</v> <v English>which one you believe are Gaussian by checking the box on the right side.</v> <v English>And please excuse my poor drawing skills here.</v>

## Additional Content

To implement these models in code, we need a function to which we can pass model parameters/values and return a probability.  Fortunately, we can use a normalized probability density function (PDF).  Let's revisit Sebastian's discussion of this topic.

We have implemented this Gaussian Distribution as a C++ function, ```normpdf```, and will practice using it at the end of this concept.  ```normpdf``` accepts a value, a parameter, and a standard deviation, returning a probability.  

## Additional Resources for Gaussian Distributions
- [Udacity's Statistics Course content on PDF](https://classroom.udacity.com/courses/st095/lessons/86217921/concepts/1020887710923)
- [Normal Distributions](http://mathworld.wolfram.com/NormalDistribution.html)
- [Probability Density Functions](http://stattrek.com/statistics/dictionary.aspx?definition=Probability_density_function)
Let's practice using ```normpdf``` to determine transition model probabilities.  Specifically, we need to determine the probability of moving from

$x_{t-1}$

-->

$x_t$

.  The value entered into ```normpdf``` will be the distance between these two positions.  We will refer to potential values of these positions as pseudo position and pre-pseudo position.  For example, if our pseudo position x is 8 and our pre-pseudo position is 5, our sample value will be 3, and our transition will be from x - 3 --> x.  

To calculate our transition model probability, pass any difference in distances into ```normpdf``` using our control parameter and position standard deviation.
