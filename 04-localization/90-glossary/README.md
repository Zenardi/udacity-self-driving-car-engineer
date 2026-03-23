# Glossary

> Part of: **Creating Scan Matching Algorithms**

## Additional Content

## Glossary

- **Iterative Closest Point (ICP)**: A scan matching algorithm that iterates between: 1) associating source points with target points, and 2) finding a transform that minimizes the sum of association distances. These steps repeat until convergence (no changes in association) or a maximum number of iterations is reached.
- **KDTree**: A data structure used to quickly associate source points to target points. It is similar to a binary tree, but designed for points in multi-dimensional space (for example, point clouds).
- **Probability Density Function (PDF)**: A function used to specify the probability that a value falls within a given range.
- **Singular Value Decomposition (SVD)**: A matrix factorization into singular vectors and singular values.
- **Normal Distributions Transform (NDT)**: NDT finds centroids and covariances for clustered regions and uses them to define a PDF. Using that PDF, Newton's Method is used to find function roots and build gradient and Hessian matrices. Scans are partitioned into grid cells, each with its own PDF. The total transform is then computed by summing the gradient and Hessian terms.
- **Newton's Method**: A method for finding roots (or optimization directions) of a function. For multivariable functions, it uses gradient and Hessian matrices.
- **Point Cloud Library (PCL)**: A [powerful library](https://pointclouds.org/documentation/) for working with point clouds.

### ICP Equations

The goal is to estimate rotation $R$ and translation $t$ from source and target point sets.

$$
S = X Y^T
$$

$$
\mathrm{SVD}(S) = U, V
$$

$$
R = V \begin{pmatrix} 1 & 0 \\ 0 & \det(VU^T) \end{pmatrix} U^T
$$

$$
t = c_T - R c_S
$$

Where $c_T$ and $c_S$ are the target and source centroids, respectively.

### Create a Probability Density Function (PDF) Equations

$$
q = \frac{1}{n} \sum_{i=1}^{n} x^i = \text{mean}
$$

$$
\Sigma = \frac{1}{n} \sum_{i=1}^{n} (x^i-q)(x^i-q)^T
$$

$$
p(x) = e^{-\frac{(x-q)^T\Sigma^{-1}(x-q)}{2}}
$$

### Newton's Method (2D) Equations

The gradient vector $g$ is:

$$
\nabla f =
\begin{pmatrix}
\frac{\partial f}{\partial x_1} \\
\frac{\partial f}{\partial x_2} \\
\vdots \\
\frac{\partial f}{\partial x_n}
\end{pmatrix}
$$

The Hessian matrix $H$ is:

$$
\nabla^2 f =
\begin{pmatrix}
\frac{\partial^2 f}{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1 \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_1 \partial x_n} \\
\frac{\partial^2 f}{\partial x_2 \partial x_1} & \frac{\partial^2 f}{\partial x_2^2} & \cdots & \frac{\partial^2 f}{\partial x_2 \partial x_n} \\
\vdots & \enspace & \ddots & \vdots \\
\frac{\partial^2 f}{\partial x_n \partial x_1} & \frac{\partial^2 f}{\partial x_n \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_n^2}
\end{pmatrix}
$$

If $H$ is [positive definite](https://www.math.utah.edu/~zwick/Classes/Fall2012_2270/Lectures/Lecture33_with_Examples.pdf), we can solve for the position update $\Delta p$ using:

$$
H\Delta p = -g
$$

### Resources

- [Using ICP in PCL](https://pointclouds.org/documentation/tutorials/iterative_closest_point.html)
- [Full list of ICP Parameters](http://docs.ros.org/en/hydro/api/pcl/html/classpcl_1_1IterativeClosestPoint.html)
- [Creating and Using a KDTree in PCL](https://pointclouds.org/documentation/tutorials/kdtree_search.html)
- [Paper: Least-Squares Rigid Motion Using SVD](https://igl.ethz.ch/projects/ARAP/svd_rot.pdf)
- [Paper: The Normal Distributions Transform: A New Approach to Laser Scan Matching](https://www.researchgate.net/publication/4045903_The_Normal_Distributions_Transform_A_New_Approach_to_Laser_Scan_Matching)
- [Using Newton's Method](https://www.math24.net/newtons-method)
