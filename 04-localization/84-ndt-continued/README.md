# NDT Continued

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ZwAVNeug3VM)

## Summary

**README: Understanding h and g in NDT**

This project focuses on implementing Normal Distributions Transform (NDT) for point cloud registration. The key concepts introduced in this lesson include calculating **h** and **g**, which are essential components of the NDT algorithm.

### Key Concepts

* **Hessian Matrix**: A square matrix used to describe the curvature of a function at a given point.
* **Jacobian Matrix**: A matrix that describes the partial derivatives of a vector-valued function with respect to its input variables.
* **Gaussian Distribution**: A probability distribution used in NDT for modeling the transformation between two point clouds.
* **Mean and Covariance**: Parameters used to describe the Gaussian distribution, where the mean represents the expected value and the covariance represents the spread or dispersion of the data.
* **Partial Derivatives**: The rate of change of a function with respect to one of its variables.
* **Associative Property**: A mathematical property that allows us to split up complex functions into simpler components and calculate their derivatives separately.

### Practical Notes

To implement NDT, you need to:

1. Calculate the mean and covariance for each cell in the point cloud.
2. Compute the partial derivatives of the Gaussian distribution with respect to its parameters (mean and covariance).
3. Use the Jacobian matrix to compute the Hessian matrix.
4. Ensure that the Hessian matrix is positive definite by adding a multiple of the identity matrix, if necessary.

Note: The provided code in the classroom notes includes an implementation of NDT using PCL (Point Cloud Library). You can refer to this code for guidance on implementing the algorithm.

## Transcript

Let's look at what h and g are dependent on. It's dependent on that current x value, that test point, as well as the mean and covariance. That's the mean and covariance of the cell region that's in. We also have these partial derivatives, and we have a partial derivative of the x and this is 1, 0, for the y, 0, 1. Then for this data, and this is just coming out of the Jacobian, we also have this exp part, so e to the power of that shows up quite a bit in the Hessian calculation.

It's using this queue, which is that centered vector from that x transform, so the x transform minus that mean value and plug it into here. Then we have this second-order partial derivative, but you don't really have to worry about it. It's going to be 0, 0 most of the time, but when i and j are both three, so in the Hessian, very last part of it, you have this, which is dependent. You can see on your initial data that from current. It's x and y as well.

Now, here are the actual equations for finding g and h. Dependent on all those portions and we're just seeing them here. We see that q, that centered vector, which is that x transform minus the mean, we add that inverse of the covariance which is coming from that specific cell that the point is in. We have that partial derivative, and we saw each of those components there. There's one for x, one for y, one for theta depending on your i, and then that exp part.

What's nice is you only have to calculate this once and then you can use it throughout. Then you can see it for the Hessian as well. Seeing a lot of those same parts, and you also have this second-order partial derivative as well, but only have to worry about it when i and j are both three, otherwise it's 0, 0. Now let's take a look at how this applies to our problem that we've been working with where we have a target point cloud and we have the source point cloud. Now we're talking before about this as single cell and that single PDF, well, using it on a target point cloud, we're going to break up our space into many cells and each cell has its own PDF.

All right, so each cell has its own 2D Gaussian here that we can see. Then when we're looking at the source points, you can see each source point, it's a lookup table. See what cell it belongs to. Then that's what PDF is affecting it. In this case here, any of these source points that are falling within a cell are going to have an H and a g that's going to be able to influence the final transform that this is going to make.

In this case, we have just these four points that are falling within a cell then we can find a respective g and H for them by using their respective covariance and mean and doing the calculations for g and H. We do that for each of these four cells that are falling in here and then just ignoring the others, and we add up all these respective H and g's. We can do this because of the associative property that we can split up if you're looking for the derivative of function, and if that function is made up of two functions, you can calculate the derivative for each of those parts and then add them up. That's what allows us to just take the H's and g's, add them up, get the overall H's and g's, and then just calculate that Delta p, that change in the x, y data that we need. Then this step right here, we want to do a specific step size.

Then in the exercise, you'll see there's a function helping you do this. But it's also interesting to take a look at some of the source code from PCL for doing NDT, which is included in the classroom notes as well. But we take this small step in our transform, they'd get our new transform. Also, here's a note as well about making sure the Hessian is positive definite. This is from the attached research paper in the classroom.

You can take the Hessian and add the identity matrix times some Lambda constant. If Lambda is big enough, then it can make H positive definite. That's important just to make sure that we go in the right direction.

## Additional Content

### PDF Characteristics & NDT Equations
* The Gradient and Hessian are dependent on current point, mean, and covariance
* The

$exp$

variable can be computed once and then shows up quite a few times in

$g$

and

$H$

equations
* Both the gradient and hessian use the partial derivatives
* The Hessian uses a second order partial derivative which is <0,0> unless both

$i$

and

$j$

are 3, meaning both are theta term
### Applying Newton's Method
* Each cell has its own PDF being defined by which target points lie inside of it
* Each source point is assigned to a PDF depending on which cell it is in
* Each source point that has a PDF leads to a

$g, H$

calculation
* All the

$g$

, and

$H$

matrices are summed up and then the overall transform is computed
* Step size and ensuring

$H$

is positive definite are needed to get the final transform
