# Lidar Measurement Model

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ToQWO-y2BSE)

## Summary

**Setting Up the Measurement Model for a Lidar Sensor in 2D**
===========================================================

This README file summarizes the key concepts and practical steps introduced in the lesson on setting up the measurement model for a lidar sensor in 2D.

### Key Concepts
* **Measurement Vector z**: A vector that represents the measured values from the lidar sensor, which is a point cloud with x and y coordinates.
* **Measurement Matrix H**: A matrix that projects the state-space (4D vector) to a 2D measurement space. It's used to relate the state variables to the measurements.
* **Measurement Covariance Metrics R**: A matrix that represents the uncertainty or noise associated with the measurements.

### Practical Notes
To set up the measurement model for a lidar sensor in 2D, follow these steps:

1. Define the measurement vector z as `px` and `py`, which represent the x and y coordinates of the object's position.
2. Derive the measurement matrix H by projecting the state-space (4D vector) to a 2D measurement space. You can use one of the provided matrices or try to derive it from scratch.

Note: The output of the lidar sensor is a point cloud, and the object detection gives us the object's position as input for our Kalman filter.

## Transcript

Here we are in the lesson map. So far we have defined the motion model and prediction step. At this point, let's say a lighter measurement has come in, so what should we do now? Exactly, you have to set up our measurement model for a lidar sensor in 2D. This will involve defining the measurement vector z, the measurement matrix H, and the measurement covariance metrics R.

Remember from the previous lighter lessons that the output of the lidar sensor is a point cloud. You also learned how to apply deep neural networks on point clouds to detect objects. The object detection gives us the object's position px py as measurement input for our Kalman filter. The newer network detects other vehicles at each signal timeframe and the Kalman filter can then be applied afterwards to trick the objects over time. Our measurement vector z is just px and py.

We also know that our state is a 4D vector, px py and vx vy. Now, I would like you to derive the right measurement matrix H, which is a projection from afar the state-space to a 2D measurement space. Take a look at the possible matrices below, or if you like the extra challenge try to derive H without looking at the given options.

## Additional Content

## Lidar Measurement Model
### Variables Summary

-

$\mathbf z$

is the measurement vector. For a lidar sensor, the

$\mathbf z$

vector contains the position measurements in

$x$

and

$y$

:

$$\mathbf z = \begin{pmatrix} p_x\\p_y \end{pmatrix}$$

-

$\mathbf H$

is the matrix that projects your belief about the object's current state into the measurement space of the sensor. For lidar, this is a fancy way of saying that we discard velocity information from the state variable since the lidar sensor only measures position: The state vector

$\mathbf x$

contains information about

$\begin{pmatrix}p_x, p_y, v_x, v_y\end{pmatrix}$

, whereas the

$\mathbf z$

vector will only contain

$\begin{pmatrix}p_x, p_y\end{pmatrix}$

. Multiplying

$\mathbf H \mathbf x$

allows us to compare

$\mathbf x$

, our predicted state, with

$\mathbf z$

, the sensor measurement.
###

$\mathbf H$

Matrix Quiz
Find the right

$\mathbf H$

matrix to project from a 4D state space to a 2D measurement space, as follows:

$$\begin{pmatrix} p_x\\p_y \end{pmatrix} = \mathbf H \begin{pmatrix} p_x\\p_y\\v_x\\v_y \end{pmatrix}$$

Here are your options:

a.

$\mathbf H = \begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix}$

b.

$\mathbf H = \begin{pmatrix}
1 & 0 \\
0 & 1 \\
 0 & 0 \\
 0 &0
\end{pmatrix}$

c.

$\mathbf H = \begin{pmatrix}
1 & 1
\end{pmatrix}$

d.

$\mathbf H = \begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 &0
\end{pmatrix}$

(Hint: first consider the matrix dimensions, then try to use a 0 or 1 to correctly project the components into the measurement space.)
