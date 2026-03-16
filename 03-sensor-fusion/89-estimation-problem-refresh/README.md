# Estimation Problem Refresh

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=W_v4PLj7DUQ)

## Summary

**Kalman Filter Estimation Problem Summary**
=============================================

The Kalman filter is a mathematical algorithm used to estimate the state of a system from noisy measurements. In this lesson, we'll review the main steps of the Kalman filter and explore how it corrects predictions using measurement data.

### Key Concepts

* **Gaussian Distribution**: A probability distribution that describes the uncertainty in the estimated state.
* **Prediction Step**: The process of predicting the estimated state to the next time stamp based on the current velocity assumption.
* **Update Step**: The process of correcting the prediction using measurement data from sensors, such as LiDAR.
* **Covariance Matrices**:
	+ **Q (Process Noise Covariance)**: Represents the uncertainty in the motion model. Small Q values indicate a more accurate motion model and higher weight on predictions.
	+ **R (Measurement Noise Covariance)**: Represents the noise in measurement data. Small R values indicate less noisy measurements and higher weight on measurement updates.

### Practical Notes

When implementing the Kalman filter, you'll need to choose values for Q and R based on your application's specific requirements. These values can be determined through calibration on a test track with objects of known distance. For example:

```python
# Example code for setting Q and R values
Q = 0.1  # Small value indicates accurate motion model
R = 10   # Large value indicates noisy measurement data
```

In this lesson, we've seen how the Kalman filter uses a combination of prediction and measurement updates to estimate the state of a system with noisy measurements. By understanding the key concepts and practical considerations outlined above, you'll be well-equipped to implement the Kalman filter in your own projects.

## Transcript

In this lesson, we will do a quick recap of the estimation problem and the main Kalman filter steps. Imagine that we're sitting in car 1 and measuring the distance to car 2 with a LiDAR. The LiDAR measurements are depicted by these red stars. From the measurements, we roughly know the state of the car in front, for example, position and velocity. But the measurements are noisy, so we don't know the exact position.

The uncertainty is depicted by the green Gaussian curve. The correct position could basically be somewhere inside this green Gaussian. Like before, we predict the estimated state to the next time stamp assuming the velocity does not change. But again, this assumption might be wrong. That's why the Gaussian distribution is wider and flatter now.

But then we get the next measurements from our LiDAR. The measurements are noisy, that's why we have another Gaussian here in red, and based on these red measurements, we know that the car can't be ahead as much as predicted if the measurements originate from the back of the car. This is exactly what the Kalman filter does in the update step. It corrects the prediction using the measurements. Based on our two Gaussians, the green curve for prediction and the red curve for measurements, the update calculates a third Gaussian, the blue curve, which is more certain than the prediction, and therefore the distribution is more peaked.

That is the main idea of the Kalman filter. We start with an initial guess of the state, the initial green Gaussian here, then we predict the state to the next time stamp, the Gaussian gets wider and flatter through the model uncertainty. Then we measure our actual state including some noise, and we correct our prediction using the measurements. Then we predict again to the next timestamp and so on. Are you following me so far?

Now, here's an important question, since we calculate our update based on two inputs the prediction and the measurement, how much do we believe in the two inputs to be correct? Which of the two do we trust more? Actually, this decision depends on our sensors and our application. We have two different sets of parameters that are relevant for this weighting. First, there's the covariance of the process noise Q.

A small Q means the motion will vary only little, so we trust our motion model to be quite accurate and the prediction will get higher weight. Similarly, we have the measurement noise covariance matrics R. Small values for R, means that we trust our measurement to contain only little noise, and the measurement update will be higher weighted than the prediction. In practical applications, values for R have to be measured on a test track with calibration objects. As you can see in this image, the values for Q can be chosen depending on your application, for example, how much braking and acceleration you expect in your scenarios.

## Additional Content

## Estimation Problem Refresh
### Variable Definitions

- $\mathbf{ x}$ is the **state vector**. It contains information about position and velocity of the object that you are
tracking:

$$\mathbf{ x} = \begin{pmatrix} p_x \\ p_y \\ v_x \\ v_y \end{pmatrix}$$

- Position and velocity are represented by a Gaussian distribution with mean $\mathbf{ x}$. $P$ is the **estimation error covariance matrix**, which contains information about the uncertainty of the object's position and velocity. You can think of it as containing standard deviations.

- $k refers to the time step index. S $x_k is the object's position and velocity vector at tim $t_k$.

- $\Delta t$ is the time step between two consecutive measurements.

- The notation $\mathbf x_k^-$ refers to the prediction step. At time $t_k$ , you receive a sensor measurement. Before taking into account the sensor measurement to update your belief about the object's position and velocity, you predict where you think the object will be at time $t_k$ . You can predict the position of the object at $t_k$ based on its position and velocity at time $t_{k - 1}$ . Hence $\mathbf x_k^-$ means that you have predicted where the object will be at $t_k$ , but you have not yet taken the new sensor measurement into account. The corresponding predicted covariance is denoted as $\mathbf P_k^-$.

- $\mathbf x_k^+$ means that you have now predicted where the object will be at time $t_k$ and then used the sensor measurement to update the object's position and velocity. Similarly, the updated covariance is $\mathbf P_k^+$.
