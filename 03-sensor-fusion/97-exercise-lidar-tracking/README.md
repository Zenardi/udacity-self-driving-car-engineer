# Exercise: Lidar Tracking

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=N9Kq15RjovU)

## Summary

**2D Kalman Filter Implementation**
=====================================

This project involves implementing a 2D Kalman filter in Python to track a moving object with non-linear motion. The goal is to estimate the position and velocity of the object using noisy measurements from a LiDAR sensor.

### Key Concepts

* **Kalman Filter**: A mathematical algorithm for estimating the state of a system from noisy measurements.
* **System Matrix F**: A 4x4 matrix representing the transition model, which describes how the state evolves over time.
* **Process Noise Covariance Q**: A 4x4 matrix representing the uncertainty in the process noise.
* **Measurement Matrix H**: A 2x4 matrix representing the measurement model, which describes how the measurements are related to the state.
* **State Dimension**: The number of variables that describe the system's state (in this case, 4: x position, y position, x velocity, and y velocity).
* **Process Noise Variable q**: A scalar value representing the standard deviation of the process noise.

### Practical Notes

To implement the 2D Kalman filter, you will need to:

1. Define the system matrix F using the given timestep.
2. Calculate the process noise covariance Q using the process noise variable q.
3. Define the measurement matrix H for a 2D LiDAR measurement.
4. Use the prediction and update functions from the previous exercise to run the filter.
5. Visualize the results of the tracking.

Note: The system model used in this project is linear, but the motion is non-linear due to the square term in the y position. This will introduce some estimation error in the results.

## Transcript

Now it's your turn. I have provided a starter code with a 2D Kalman filter for you. I want you to implement the system matrix F, process noise covariance Q, and the measurement matrix H. The Python script should look familiar. It is quite similar to the last exercise only now we move from 1D to 2D.

Therefore, we have a state dimension of four in the int function with a 2D position and a 2D velocity. We now use a timestamp of 0.1 seconds and I have prepared a process noise variable, lowercase q equals 0.1. that you should use when implementing the covariance metrics uppercase Q. In the next function F, please implement and return the four-by-four system metrics taking into account the given timestep. In the function Q, please implement and return the process noise covariance.

Finally, please implement and return the measurement metrics H for a 2D LiDAR measurement. You have already implemented the prediction and update functions in the last exercise and you already know the main loop run filter. Again, we initialize the filter state and covariance. Then we loop over the measurements and predict the next timestamp. The ground truth is now slightly more challenging.

We have a non-linear motion with a square value in the y position. Since we use a linear motion model to trick a nonlinear motion, just like we do in real-world applications, the result will never be as perfect as in the last exercise. There will always be a small estimation error. Then we generate the noisy measurements, called the update function, and visualize the results. Let's see if you can put your tracking knowledge into practice now.

## Additional Content

## Exercise: Lidar
### Measurement Noise Covariance Matrix R Explanation

For lidar sensors, we have a 2D measurement vector. Each location component $\left(p_x, p_y\right)$ is affected by a random noise. So our noise vector $\omega$ has the same dimension as $\mathbf z$. And it is a distribution with zero mean and a 2 x 2 covariance matrix which comes from the product of the vertical vector $\omega$ and its transpose:

$$\mathbf R = E[\omega \omega^T] = \begin{pmatrix} \sigma^2_{x} & 0 \\ 0 & \sigma^2_{y} \end{pmatrix}$$

where $\textbf R$ is the measurement noise covariance matrix. In other words, the matrix $\textbf R$ represents the uncertainty in the position measurements we receive from the lidar sensor.

Generally, the parameters for the measurement noise covariance matrix will be provided by the sensor manufacturer or have to be determined in test drives. In the mid-term project, you evaluated the standard deviation of your lidar detections in x and y, so you can directly use your results for R in the final project.

Remember that the off-diagonal 0 entrys in $\textbf R$ indicate our assumption that the noise processes are uncorrelated, noise in $x$ position does not affect the $y$ position and vice versa.

You now have all you need for lidar-only tracking! In the following, I want you to apply what you've learned in a programming assignment.
