# Glossary

> Part of: **Creating Scan Matching Algorithms**

## Additional Content

## Glossary

* **Iterative Closest Point (ICP)**: A scan matching algorithm that does repeating iterations of 1) making associations between the source points and target points, and 2) finds a transform that minimizes the sum of associations' distances. These iterations of 1&2 repeat until convergence (no changes in association) or a desired number of iterations are performed.
* **KDTree**: A data structure to quickly associate source points to target points; it is similar to a binary tree, but helpful for points in a multi-dimensional space, such as a point cloud.
* **Probability Density Function (PDF)**: Used to specify the probability that something falls within a range of values.
* **Singular Value Decomposition (SVD)**: Factorizes matrices into singular vectors or values.
* **Normal Distributions Transform (NDT)**: NDT finds centroids of cluster regions and their covariances, and uses those to define a PDF. Using that PDF, Newton's Method is then used to find the root of the function, helping to create gradient and Hessian matrices. The scans can then be broken up into "cells" in a grid, where each cell has its own PDF. All the gradient and Hessian matrices are then summed up to calculate a total transform, to match the source and target scans.
* **Newton's Method**: Gives a direction to take to get to the root of a function or a higher/smaller value. With a multi-variable function, the gradient and hessian matrices are used to do Newton's method.
* **Point Cloud Library (PCL)**: A [powerful library](https://pointclouds.org/documentation/) for working with point clouds.
### ICP Equations

Here, the point is to go from the vectors adding up to total

$X$

and

$Y$

and get the Rotation

$R$

and Translation

$t$

.

$S = XY^T$

$SVD(S) = U, V$

(the singular value decomposition)

$R = V({^1}_{det(VU^T)})U^T$

$t = c_T - Rc_S$

where

$c_T$

and

$c_S$

are the target and source centroids, respectively.
### Create a Probability Density Function (PDF) Equations

$q = \frac{1}{n} \sum_{i}^{n}x^i = mean$

$\sum = \frac{1}{n} \sum_{i}^{n}(x^i-q)(x^i-q)^t$

$\Large p(x) = e^\frac{-(x-q)^t\sum^{-1}(x-q)}{2}$

### Newton's Method (2D) Equations

$g$

is the gradient vector:

$\Large \triangledown f = \begin{pmatrix} \frac{\partial f}{\partial x_1} \ \frac{\partial f}{\partial x_2} \ \vdots \ \frac{\partial f}{\partial x_n} \end{pmatrix}$

while the

$H$

matrix is the Hessian matrix:

$\Large \triangledown^2 f = \begin{pmatrix} \frac{\partial^2 f}{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1 \partial x_2} & \cdots  & \frac{\partial^2 f}{\partial x_1 \partial x_n} \\
\frac{\partial^2 f}{\partial x_2 \partial x_1} & \frac{\partial^2 f}{\partial x_2^2} & \cdots & \frac{\partial^2 f}{\partial x_2 \partial x_n} \\
\vdots & \enspace & \ddots & \vdots \\
\frac{\partial^2 f}{\partial x_n \partial x_1} & \frac{\partial^2 f}{\partial x_n \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_n^2} \end{pmatrix}$

If

$H$

is a

[positive definite](https://www.math.utah.edu/~zwick/Classes/Fall2012_2270/Lectures/Lecture33_with_Examples.pdf)

, we can use the gradient and Hessian matrix to calculate the change in position

$p$

:

$H \Delta p = -g$

### Resources
* [Using ICP in PCL](https://pointclouds.org/documentation/tutorials/iterative_closest_point.html)
* [Full list of ICP Parameters](http://docs.ros.org/en/hydro/api/pcl/html/classpcl_1_1IterativeClosestPoint.html)
* [Creating and Using a KDTree in PCL](https://pointclouds.org/documentation/tutorials/kdtree_search.html)
* [Paper: Least-Squares Rigid Motion Using SVD](https://igl.ethz.ch/projects/ARAP/svd_rot.pdf)
* [Paper: The Normal Distributions Transform: A New Approach to Laser Scan Matching](https://www.researchgate.net/publication/4045903_The_Normal_Distributions_Transform_A_New_Approach_to_Laser_Scan_Matching)
* [Using Newton's Method](https://www.math24.net/newtons-method)
