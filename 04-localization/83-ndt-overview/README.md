# NDT Overview

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=-wuIuMR9Ssw)

## Summary

**Normal Distribution Transform (NDT) README**

The Normal Distribution Transform (NDT) is a continuous, differentiable function used to model the probability distribution of data points in a cluster. It is defined by its mean (centroid) and covariance, which determine the shape of the 2D Gaussian.

### Key Concepts

* **Probability Density Function (PDF)**: A mathematical function that describes the probability distribution of a random variable.
* **Centroid**: The mean of the cluster points, representing the central point of the data.
* **Covariance**: Measures the spread and orientation of the data points around the centroid.
* **2D Gaussian**: A bell-shaped curve used to model the probability distribution of the data points.
* **Newton's Method**: An iterative algorithm for finding the roots (or peaks) of a function by following tangent lines.

### Practical Notes

To implement the NDT, you will need to:

1. Calculate the centroid and covariance from your cluster points.
2. Use the equation for the 2D Gaussian to calculate the probability density at any given point.
3. Apply Newton's Method in 2D to find the peak of the 2D Gaussian.

**Example Code**

```python
import numpy as np

def calculate_centroid(points):
    return np.mean(points, axis=0)

def calculate_covariance(points, centroid):
    centered_vectors = points - centroid
    covariance = np.dot(centered_vectors.T, centered_vectors) / len(points)
    return covariance

def ndt_probability_density(point, centroid, covariance):
    # Calculate the 2D Gaussian probability density at the given point
    return np.exp(-0.5 * np.dot(np.dot(point - centroid, np.linalg.inv(covariance)), (point - centroid).T))

def newtons_method_2d(f, x0, epsilon=1e-6):
    # Implement Newton's Method in 2D to find the peak of the 2D Gaussian
    while True:
        gradient = f.gradient(x0)
        hessian = f.hessian(x0)
        delta_p = np.dot(np.linalg.inv(hessian), -gradient)
        x1 = x0 + delta_p
        if np.linalg.norm(delta_p) < epsilon:
            break
        x0 = x1
    return x1
```

Note that this is a simplified example code and may require modifications to suit your specific use case.

## Transcript

In this next section, let's talk about creating NDT, the normal distribution transform. For the NDT, we want to define this continuous, differentiable function, and this will be our probability density function. It's defined by these input points in the cluster. The characteristics that we need to define this PDF are the centroids, that's going to be the mean of our cluster points, and that's our centroid here. Then we have the covariance and the covariance is defining what the shape of this 2D Gaussian looks like.

Here's the equation for it. We can see that it's using these centered vectors again. So we have the centered vector for each of these input points in the cluster that's originating out of the centroid. To calculate this, we're just summing up all these centered vectors multiplied by their transpose and then dividing by the total number of points. Then once we have the mean and the covariance, we have this function that allows us to see what the probability of finding a point is within this region, and that's defined right here.

You can see that it's using that input point minus q, the centroid, and multiplied by the inverse covariance times that centered vector, all divided by 2, and we have that negative. So it's e to the power of all of these. You can see that if x is the same as the centroid, we just get zero and then we get e to the power zero, which is going to be one, so that's going to be the highest probabilities if you're right here on the centroid. They'll be the peak of this 2D Gaussian. Then if you have a point that's going further out, you'll just get e to the power of this higher negative number and that'll fall down toward zero.

That's what this looks like here, this probability score. For right at the mean, we have one, then as we go away from the mean, will this fall down towards zero. Then this isn't the exact probability because it's not normalized so that the volume under it is equal to one, but it's good enough as a score function that we can use for working with this function that's continuous and differentiable. Once we have that function, we need to be able to move along it, and find the peak of that 2D Gaussian. In order to do that, we'll use Newton's method.

Let's just take a look at Newton's method in this classical approach, where we're using it to find the root of a function. Just working in this single dimension here in x, and let's say we have this f of x, and we want to find the root. Well, we can use Newton's method to do this, and the key is using that derivative, we'll use a derivative to find tangent lines. Let's say we have the starting point. We're at zero, we want to get closer to the root.

We can use the derivative of f of x to find this tangent line. We can follow that tangent line to its intersection of the x-axis, and this will be our new point, and then just repeat this process. We'll look at where the derivative is here, use it to the find that tangent line and follow it. You can see we're getting closer and closer. X_2 is like very close here to the actual root.

This is how Newton's method can help us find the root of a function. It's going to help us here as well, even when we're working with more than just one dimension. Let's talk about Newton's method in 2D, and how this translates over. In the 1D case, we're using that derivative. Well, in the 2D case, we're still going to be using this derivative, but they're in different forms.

They have these matrix forms of this gradient vector, which is going to be this partial derivative of f corresponding to each of its parameters, I am going to say x_1, x_2, x_n. In our case in 2D, we just have x and y, and then we'll actually also have Theta here. It'll be a three parameters of freedom that we'll be able to move around, and we have this H matrix, which is the Hessians. That's going to be the matrix of all these different combinations of second-order partial derivatives, and that'll be three by three. This x, y Theta, all the different freedoms that we can move around in this space.

Then when you have g and H, as long as H is positive definite, and there's some tricks to make sure that it is, you can use this equation here to find this delta P. So we have g and H. We can calculate this Delta p by just taking the inverse H, multiplying on each side. What that Delta p is telling you is this change in x, y, and Theta that you want to apply to this point, it's telling you this direction. If you apply this transform to that point, you'll have this new point, and that'll be the direction you want to take in order to in this case, get to the peak of this 2D Gaussian.

It depends on how you're defining your score function. If it's minus, then you're doing, you're finding this minimum. You're just taking the reverse of this 2D Gaussian and making it look like a pit. Where if you're looking for that max, then it's just a difference of negatives. But essentially what we want to do is find this interesting point here, and the Gaussian.

In this case, let's think about it as a score that's high up, and we want to try to get to it. Here's the equation for finding that change in x and y. Once we have this calculation here, we can apply this. Here's our x and y point. We can apply this transformation on it using this change, and figure out which direction to go to.

## Additional Content

## NDT Overview
The first part of the Normal Distributions Transforms (NDT) is to create a probability density function (PDF):

* Find the centroid of the cluster region
* Find the covariance of the cluster
* Use the cluster region's centroid and its covariance to define the probability function
#### Create a Probability Density Function (PDF) Equations

$q = \frac{1}{n} \sum_{i}^{n}x^i = mean$

$\sum = \frac{1}{n} \sum_{i}^{n}(x^i-q)(x^i-q)^t$

$\Large p(x) = e^\frac{-(x-q)^t\sum^{-1}(x-q)}{2}$

### Newton's Method
The next part of NDT is to utilize Newton's Method:

* Newton's method gives a direction to take to get to the root of a function or a higher/smaller value
* With a multi-variable function the gradient and hessian matrices are used to do Newton's method
#### Newton's Method (2D) Equations

$g$ is the gradient vector:

$\Large \triangledown f = \begin{pmatrix} \frac{\partial f}{\partial x_1} \\ \frac{\partial f}{\partial x_2} \\ \vdots \\ \frac{\partial f}{\partial x_n} \end{pmatrix}$

while the $H$ matrix is the Hessian matrix:

$\Large \triangledown^2 f = \begin{pmatrix} \frac{\partial^2 f}{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1 \partial x_2} & \cdots  & \frac{\partial^2 f}{\partial x_1 \partial x_n} \\
\frac{\partial^2 f}{\partial x_2 \partial x_1} & \frac{\partial^2 f}{\partial x_2^2} & \cdots & \frac{\partial^2 f}{\partial x_2 \partial x_n} \\
\vdots & \enspace & \ddots & \vdots \\
\frac{\partial^2 f}{\partial x_n \partial x_1} & \frac{\partial^2 f}{\partial x_n \partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_n^2} \end{pmatrix}$

If $H$ is a [positive definite](https://www.math.utah.edu/~zwick/Classes/Fall2012_2270/Lectures/Lecture33_with_Examples.pdf), we can use the gradient and Hessian matrix to calculate the change in position $p$:

$H \Delta p = -g$
