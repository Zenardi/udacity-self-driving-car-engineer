# Variance Comparison

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=TGdMG81hXc8)

## Summary

**Understanding Covariance in Gaussian Distributions**
=====================================================

This README file provides an overview of key concepts related to covariance in Gaussian distributions, including its calculation and interpretation.

### Key Concepts

* **Covariance**: A measure of the spread or dispersion of a probability distribution. It represents how much the data points are scattered around the mean value.
* **Sigma-squared (σ²)**: The variance of a Gaussian distribution, which is related to the covariance. A larger σ² indicates more uncertainty in the actual state.
* **Normalization**: The process of scaling the difference between x and y values by the covariance, which affects the spread of the function.
* **Uncertainty**: Covariance is a measure of uncertainty, with larger values indicating greater uncertainty about the actual state.

### Practical Notes

When working with Gaussian distributions, consider the following:

* Functions with a wide spread have large covariance, while functions with small spread have small covariance.
* The formula for calculating covariance involves normalizing the difference between x and y values by the covariance.
* A larger σ² value indicates more uncertainty in the actual state, while a smaller value suggests greater certainty.

This summary provides a concise overview of key concepts related to covariance in Gaussian distributions. By understanding these principles, you can better interpret and work with probability distributions in various applications.

## Transcript

Let me ask you again about your intuition and draw three more Gaussians, and, again, excuse my poor drawing skills here. Now I'm going to ask you about the covariance. For each of those check exactly one box. Is the covariance large, medium, or small? Obviously, one of those is the largest, one is a medium, and one is small.

The answer is this is the largest covariance. It's the widest spread. This is the smallest, and this is medium. To see how this is being found in the formula over here, the difference between x and y is being normalized by the covariance. The larger this value, the less the difference over here matters, and, as a result, the more the function is spread out.

So functions with a very wide spread have the largest covariance, whereas functions with small spread have the smallest covariance. Put differently, the sigma-squared covariance is a measure of uncertainty. The larger sigma-squared, the more uncertain we are about the actual state. This is a very certain distribution where expected deviation is small. This is a relative uncertain distribution where we know very little.

## Images

![There are three graphs, each that can be large, medium or small.   The first graph starts at (1,0) and ends at (7,0). It slopes upwards, hits a maximum point at about (4,5) and then slopes down again. The second graph starts at (0,0), has a sharp upward curve, hits a maximum point at about (3, 7) and quickly slopes down and ends at (5,0).  The third graph starts at (0,0), curves upwards at (3, 2) and curves downward until (8, 0).](images/kalman-variance-comparison.jpg)
*Quiz Options*

## Additional Content

## Variance Comparison

This question asks about the

variance

of each Gaussian (not its covariance).

### Quiz Image

### Solution

[Watch on YouTube](https://www.youtube.com/watch?v=rczAG7meAY4)

Correction: In the solution video, it should be "x and u" at 00:15.
