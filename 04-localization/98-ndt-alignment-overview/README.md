# NDT Alignment Overview

> Part of: **Utilizing Scan Matching**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=NPDFluxAMVU)

## Summary

**Scan Matching with NDT in 3D Scans**
=====================================

This project applies scan matching using Normal Distributions Transform (NDT) to 3D scans. We will continue from the previous lesson where we calculated the probability density function (PDF) and used Newton's method for optimization.

### Key Concepts

* **Probability Density Function (PDF)**: The PDF is a fundamental concept in NDT, which calculates the likelihood of a point belonging to a given distribution. In 3D scans, the PDF is similar to that in 2D scans, with some modifications.
	+ Calculating the centroid (mean) and covariance of points in a cell
	+ Generalizing to any dimension (e.g., from 2D to 3D)
* **Covariance**: A measure of how much the points in a cell deviate from their mean. In 3D, the covariance is a 3x3 matrix.
* **Newton's Method**: An optimization technique used to find the maximum likelihood estimate (MLE) of the parameters. In NDT, Newton's method is applied to update the parameters using the gradient and Hessian matrices.
	+ Gradient vector (`g`) with six elements (change in x, y, z, roll, pitch, and yaw)
	+ Hessian matrix (`H`) with 6x6 elements
* **NDT in 3D**: The NDT algorithm is adapted for 3D scans by considering the additional degrees of freedom (roll, pitch, and yaw).

### Practical Notes

To apply this project, you will need to:

1. Implement the PDF calculation for 3D scans, taking into account the additional dimensions.
2. Modify Newton's method to handle the larger gradient and Hessian matrices in 3D.
3. Test your implementation on sample 3D scan data.

Note: This summary assumes a basic understanding of NDT and optimization techniques. If you are new to these topics, please review the relevant material before proceeding.

## Transcript

In this section, we'll continue talking about applying scan matching. Now, let's talk about applying it with NDT in 3D scans. Now, we're working with a grid space of cubes. Last time it was this grid space of squares, now we have a cube. Remember that first part of NDT was calculating that probability density function.

Now, we're doing that same thing, and the probability density function, it's going to be fundamentally the same where you're calculating that centroid of that cell by taking all those points, summing them up, and finding the mean, and the covariance is very similar to it, the calculation. In fact, this will generalize to any dimension. Now, you have the center of vectors still multiplied with that center of vector transpose, and your covariance ends up being three by three now. Then same with your equation in that cube space. Exact same equation and you end up with a single probability element based of that input point now in 3D.

That's how the PDF now looks in three dimensions. Then, let's talk about that second part of creating NDT, which was doing Newton's method. Before we were talking about that transformed alteration, that was just x, y and Delta, well now, we have this change in x, y, z, roll, pitch, and yaw with the six degrees of freedom. That means that Delta f, that gradient vector now is going to be six by one, and then that Hessian, which was the matrix of the second-order partial derivatives, is going to have total of six by six. Then the calculation for getting that Delta p is exactly the same.

Once you have H and g, so that's how that changes for NDT.

## Additional Content

## NDT Alignment Overview
* In 3D, the grid space is made of cubes instead of squares
* The PDF is now in 3D, as the equation for a PDF generalizes to any dimension.

$q$

becomes 3x1 while the sum of centered vectors becomes 3x3.
*

$g$

is now 6x1 and

$H$

is now 6x6
* The calculation for

$\Delta p$

is still the same from the 2D case
