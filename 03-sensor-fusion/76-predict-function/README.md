# Predict Function

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=DV2cX9W0tT8)

## Summary

**Implementing a One-Dimensional Kalman Filter**
=====================================================

This README file provides an overview of implementing a one-dimensional Kalman filter using Python code.

### Key Concepts
* **Kalman Filter**: A mathematical algorithm used to estimate the state of a system from noisy measurements.
* **Predict Function**: Computes the new updated prediction: mean and variance, given the current estimate and its variance, motion and its uncertainty.
* **Mean and Variance Update**: The predict function updates the mean and variance using the following formulas:
```python
new_mean = prior_mean + motion_mean
new_variance = prior_variance + motion_variance
```
* **One-Dimensional Kalman Filter**: A simplified version of the Kalman filter, used for systems with a single dimension.

### Practical Notes
To implement this code, you will need to:

1. Define the `predict` function, which takes in the current estimate and its variance, motion and its uncertainty as inputs.
2. Use the formulas above to update the mean and variance.
3. Test your implementation using example inputs, such as a prior of 10 and 4, and a motion of 12 and 4.

Note: This code is a simplified version of a Kalman filter and may not be suitable for all applications.

## Transcript

[Thrun] Let's program this. I'm giving you a skeleton code. This is the same update function as before. Now I would like you to do the predict function, which takes our current estimate and its variance and the motion and its uncertainty and computes the new updated prediction: mean and variance. So for example, if our prior is 10 and 4, our motion is 12 and 4, I would like to get out to 22 and 8 according to the formulas I've just given you.

And yes, it's as easy as this. We just add the two means and the two variances. It's amazing, this entire program over here implements a one-dimensional Kalman filter.

## Additional Content

## Predict Function

### Solution
