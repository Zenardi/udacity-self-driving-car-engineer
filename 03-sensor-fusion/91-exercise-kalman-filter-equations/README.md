# Exercise: Kalman Filter Equations

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=s1WzB6QG3HA)

## Summary

**Linear Kalman Filter Implementation**
=====================================

This project involves implementing a linear Kalman filter in Python to estimate the state of a system based on noisy measurements. The goal is to use the provided starter code as a foundation and implement the `predict` and `update` functions using the NumPy matrix format.

**Key Concepts**
---------------

* **Kalman Filter**: A mathematical algorithm used for estimating the state of a system from noisy measurements.
* **State Dimension**: In this example, the state dimension is 2, representing a 1D position and velocity.
* **System Matrix (F)**: A matrix that describes the relationship between the current state and the next state.
* **Process Noise Matrix (Q)**: A matrix that represents the uncertainty in the system's dynamics.
* **Measurement Metrics (H)**: A vector that describes how to extract information from the measurements.
* **Covariance**: A measure of the uncertainty associated with the estimated state.

**Practical Notes**
------------------

To implement the `predict` and `update` functions, you will need to use the provided starter code as a foundation. The key steps are:

1. Implement the `predict` function using the system matrix (F) and process noise matrix (Q).
2. Implement the `update` function using the measurement metrics (H) and covariance.
3. Use the NumPy matrix format for all matrix operations.

Some important notes on the code structure:

* The starter code includes a Kalman filter class with an `init` function that initializes the state dimension.
* The system matrix (F), process noise matrix (Q), and measurement metrics (H) are already implemented in the starter code.
* You will need to implement the `predict` and `update` functions using these matrices.

By following these steps and implementing the correct algorithm, you should be able to see the estimated state and covariance converge to the true values.

## Transcript

I have a programming assignment for you. I would like you to implement the predict and update functions of a linear kalman filter in Python. Let me help you get started. Here is the starter code. For matrix manipulation, I would like you to use the numpy matrix format, so we need to import numpy.

The program includes a kalman filter class. It has an init function which initializes the state dimension. In our case, we have a 1D position and a 1D velocity. So the state dimension is two. Next, there's a function F which returns the system matrix.

Note that we use a fixed time step of one in this exercise. This is an example of how you can use the numpy matrix format. You are probably familiar with numpy arrays, and a matrix is simply a 2D array. The advantages that it contains special operators such as matrix multiplication. We also have a function Q to return the two-by-two process noise matrix.

In this very simple exercise, we use a constant velocity without breaking or acceleration. So our process model contains no noise and we can set Q to zero. Additionally, there's a function H that returns the measurement metrics. We use 1D position measurements. So H is a one by two row vector.

Note that we also use numpy matrices for vectors here in order to directly apply matrix multiplication. Next, I've prepared the predict and update functions for you. Please implement the correct algorithm steps here using the prepared F, Q, and H functions. Both predict and update functions return state and covariance. Finally, let's have a look at the main function run filter.

This function loops over all data and iteratively calls the predict and update functions. We initialize the kalman filter. Then we initialize X with position 0 and velocity 0. We initialize P with a rather big initial standard deviation of five. Then we loop over all time steps.

We call the predict function and print the predicted state and covariance X minus and P minus. Then we generate a noisy measurement. The correct position at each time step increases by one. So at time 1, the position is one, at time 2 it is two, and so on. From this correct position, also called ground truth, we generate a noisy measurement, with a standard deviation of one and set R with the same standard deviation.

Finally, we update state and covariance with the generated measurement and print the updated X plus and P plus. Let's see what happens if I run the script. The console output here on the right shows that X remains at the initial value of zero, even though the last measurement Z is around 98. Now it's your turn. Please implement the correct predict and update functions and see how the output changes.

## Additional Content

## Exercise: Kalman Filter Equations
You can find the starter code for this lesson's exercises in the [same repository](https://github.com/udacity/nd013-c2-fusion-exercises) as Andreas's lessons, meaning that if you have been working locally, you can continue with the same files. Otherwise, the code is provided in the workspace below.
