# Gradient Descent

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=cDJnbLyOpgo)

## Summary

**README: Gradient Descent and TensorFlow**

This project explores the concept of gradient descent, an iterative algorithm used to minimize loss functions in machine learning models. We will also cover the use of TensorFlow's `tf.Variable` class and the `tf.GradientTape` API to calculate gradients.

### Key Concepts

* **Machine Learning Model**: A set of computations that maps input to output.
* **Loss Function**: Quantifies model performance, with lower values indicating better performance.
* **Derivative**: Used to find the minimum of a function by setting it equal to zero.
* **Gradient Descent**: An iterative algorithm that updates weights using gradients to minimize loss.
* **Global Minimum**: The single value of x that minimizes the function's output.
* **Local Minima**: Values of x where the function takes the lowest value in the surrounding subspace, but not necessarily the global minimum.
* **Learning Rate**: A parameter that scales the step size taken by gradient descent.

### Practical Notes

To implement gradient descent and calculate gradients using TensorFlow:

1. Use `tf.Variable` to create tensors whose values can be changed during computation.
2. Record operations executed within a context using `tf.GradientTape`.
3. Calculate gradients using the `tf.GradientTape` API.
4. Apply gradient descent updates to model weights, scaling by the learning rate.

Example code:
```python
import tensorflow as tf

# Create a variable
x = tf.Variable([1, 2])

# Record operations and calculate gradients
with tf.GradientTape() as tape:
    y = x ** 2
dy_dx = tape.gradient(y, x)
```
This project will cover the implementation of gradient descent and its application to machine learning models using TensorFlow.

## Transcript

At the beginning of this lesson, we learned that a machine learning model consists in the set of computation to map an input to an output. This output is then fed to a loss function that quantifies the model performances. We need to find the optimal combination of weights such that this loss is minimized. Using calculus, we can find this minimum by calculating the value for which the derivative of this loss function is equal to zero. For example, the square function minimum is reached when x equals zero.

The absolute function minimum is also reached when x equals zero. For some machine learning algorithm and losses such as linear regression and L2 loss, an analytical solution exist. However, most of the time, we cannot calculate the analytical solution of our minimization problem. To find the weights combination that minimizes the loss, we need to use an iterative algorithm called gradient descent. Since the analytical solution is not always available, we need a way to calculate a function minimum.

Before we learn about the gradient descent algorithm, we need to differentiate between global and local minima. Let's look at these two functions for example. On the left, we have a square root function and on the right, a much more complex one. Both functions have a global minimum, meaning that there is a single value of x, such that f of x takes the lowest possible value. However, the right function also have what we call local minima.

This local minima are values of x where the function takes the lowest value in the surrounding subspace of x. Why does it matter to us? Well, for two reasons, the loss function we will be dealing with in this course tend to have a lot of local minima. However, we are not interested in a sub-optimal solution. We want to find the lowest possible value of f of x.

We need to design our optimization algorithm such that it ignores these local minima. Let's see our first version of this algorithm in the next slide. To find the global minimum of such function, we'll use an algorithm called gradient descent. Gradient descent is an iterative algorithm that consist in updating weights using the gradients value. In each iteration, we take a step in the opposite direction of the gradient.

These steps are scaled by a parameter called the learning rate. The higher the learning rate, the larger the steps we take. This is how the veneer version of the gradient descent algorithm work. We subtract to the model weights, the gradients scaled by the learning rate. In later videos, we will learn how we can improve this algorithm to overcome the local minima problem we mentioned in the previous slide.

Moreover, we will also learn about the critical role the learning rate is playing. Let's take another TensorFlow break. Previously, we learned about tensors. In this video, we are going to focus on an other TensorFlow class, tf variables, and how we can use them to compute gradients. Variables are created using the tf.Variable class.

They're basically tensors whose value can be changed by running operation on them. Variables conserve a lot of the tensor's attributes, such as shape. Tensorflow variable allows us to calculate gradients, which is exactly what we will need to do to perform gradient descent. Let's consider this example. We are going to create a simple operation to perform element-wise squaring of the X vector.

We have to use the tf.GradientTape API to perform such operation. This tape we record operation executed within the context. Once we have squared the x vector, we can calculate the gradient of y with respect to x. Because the derivative of x squared is 2x, dy/dx is a vector with value 2 and 4. In the next exercises, you'll leverage the tf.GradientTape API to train logistic regression and neural networks algorithm.

## Additional Content

## Gradient Descent
Fitting or training a ML algorithm consists of finding the combination of weights that **minimizes the loss function**. In some cases, it is possible to find an analytical solution (for example, [linear regression with L2 loss](https://towardsdatascience.com/analytical-solution-of-linear-regression-a0e870b038d5)). However, for most of the algorithms tackled in this course, the analytical solution to the loss minimization problem does not exist. 

The **gradient descent** algorithm is an iterative approach to find the minimum of the loss function. This algorithm takes a step towards this minimum using the gradient of the loss function scaled by a float called the **learning rate**. 

One of the challenges when using the gradient descent algorithm is the existence of **local minima**. Local minima are minima in a local subset of the loss function domain. They are the smallest value this function can take, only in this small subset, as opposed to the **global minimum** where the loss function takes the smallest value of its entire domain. The gradient descent algorithm can get stuck in local minima and outputs suboptimal solutions. Later in this lesson, we will see how other approaches solve this problem.
Tensorflow **variable** are tensors with fixed type and shape but their value can be changed through operations. We need to use variables to calculate gradients in Tensorflow with the `tf.GradientTape` api.
You can use the workspace below to try out the code from the video.
