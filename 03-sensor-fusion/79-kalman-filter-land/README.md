# Kalman Filter Land

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=LXJ5jrvDuEk)

## Summary

**High Dimensional Gaussians and Multivariate Estimation**

This README file provides a summary of key concepts related to high dimensional Gaussians, also known as multivariate Gaussians, which are used in estimation problems. These concepts are essential for understanding how the Kalman filter works.

### Key Concepts

* **Multivariate Gaussian**: A probability distribution with a mean vector and co-variance matrix that describes the uncertainty in multiple dimensions.
* **Mean Vector**: A vector with one element for each dimension, representing the expected value of the variables.
* **Co-Variance Matrix**: A D x D matrix that represents the covariance between different dimensions. It is used to describe the spread of the Gaussian and the correlation between variables.
* **Uncertainty**: The amount of variability in a variable or system. In high dimensional Gaussians, uncertainty can be correlated across different dimensions.
* **Correlation**: The relationship between two or more variables. If the co-variance matrix shows that there is a strong correlation between variables, it means that knowing one variable provides information about the other.

### Practical Notes

The Kalman filter uses multivariate Gaussians to estimate the state of a system based on noisy measurements. In this lesson, we saw how high dimensional Gaussians can be used to model 1-dimensional motion and infer velocity from discrete locations. The Kalman filter addresses estimation problems by using a combination of prediction and correction steps to update the state estimate.

**Example Code**
```python
import numpy as np

# Define a multivariate Gaussian with mean vector and co-variance matrix
mean = np.array([1, 2])
cov = np.array([[1, 0.5], [0.5, 1]])

# Generate samples from the multivariate Gaussian
samples = np.random.multivariate_normal(mean, cov, size=100)
```
Note: This code snippet is a simple example and may not be directly applicable to real-world problems.

## Transcript

To explain how this works, I have to talk about high dimesional Gaussians. These are often called multivariate Gaussians. The mean is now a vector with 1 element for each of the dimensions. The variance here is replaced by what's called a co-variance, and it's a matrix with D rows and D columns, if the dimensionality of the estimate is D. The formula is something you have to get used to.

I'm writing it out for you, but you never get to see this again. To tell you the truth, even I have to look up the formula for this class, so I don't have it in my head, and please, don't get confused. Let me explain it to you more intuitively. Here's a 2-dimensional space. A 2-dimensional Gaussian is defined over that space, and it's possible to draw the contour lines of the Gaussian.

It might look like this. The mean of this Gaussian is this x0, y0 pair, and the co-variance now defines the spread of the Gaussian as indicated by these contour lines. A Gaussian with a small amount of uncertainty might look like this. It might be possible to have a fairly small uncertainty in 1 dimension, but a huge uncertainty in the other. Huge uncertainty in the x-dimension is small, and the y- dimension is large.

When the Gaussian is tilted as showed over here, then the uncertainty of x and y is correlated, which means if I get information about x-- it actually sits over here--that would make me believe that y probably sits somewhere over here. That's called correlation. I can explain to you the entire effect of estimating velocity and using it in filtering using Gaussians like these, and it becomes really simple. The problem I'm going to choose is a 1-dimensional motion example. Let's assume at t = 1, we see our object over here.

A t = 2 right over here. A t = 3 over here. Then you would assume that at t = 4, the object sits over here, and the reason why you would assume this is--even though it's just seen these different discrete locations, you can infer from it there is actually velocity that drives the object to the right side to the point over here. Now how does the Kalman filter address this? This is the true beauty of the Kalman filter.
