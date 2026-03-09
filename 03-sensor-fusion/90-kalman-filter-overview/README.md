# Kalman Filter Overview

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=LbkL7cCX_9g)

## Summary

**Kalman Filter for 1D Motion Tracking**
=====================================

The Kalman filter is a mathematical algorithm used for estimating the state of a system from noisy measurements. In this lesson, we focus on applying the Kalman filter to track a vehicle's position and velocity using lidar.

### Key Concepts

* **State Transition Function (F)**: models how the state changes over time
	+ For constant velocity model, F predicts new location as old location plus velocity times delta t
	+ Can be represented in matrix form
* **Process Noise (Nu)**: random noise added to account for uncertainties in motion
	+ Covariance Q represents the variability of Nu
	+ Larger entries in Q indicate more acceleration and braking expected
* **Measurement Function (H)**: relates measurement to object state
	+ For lidar, H measures position only
	+ Can be represented in matrix form
* **Covariance Matrices**: P (estimation error covariance) and R (measurement noise covariance)
	+ P contains variances (squared standard deviations)
	+ R represents the variability of measurement noise
* **Kalman Gain (K)**: weighs predicted state against measurement

### Practical Notes

The Kalman filter consists of two main steps:

1. **Prediction**: predict state and estimation error covariance using F and Q
2. **Update**: update state and estimation error covariance using measurement and H

In the prediction step, the uncertainty increases due to process noise. In the update step, the residual is calculated by comparing predicted state with measurement in the same coordinate system.

The formulas for the Kalman filter are:

* Prediction:
	+ x_minus = F \* x_plus
	+ P_minus = FP_plus + F^T \* Q
* Update:
	+ Gamma = z - H \* x_minus
	+ S = HP_H^T + R
	+ K = S^-1 \* HP_
	+ x_plus = x_minus + K \* Gamma
	+ P_plus = (I - K \* H) \* P_minus

Note that the Kalman filter can be applied to different sensors and sensor fusion by modifying the measurement function and covariance matrices.

## Transcript

Now let me give you a quick reminder of the Kalman filter for a simple 1D motion case. Let's say that our mission is to track a vehicle who state, X, is described by position and velocity with a lidar. When designing the Kalman filter, we have to define two functions. The first function, F, is the state transition function that models how the state is changed from time t_k minus 1 to time t_k. For example, if you use a constant velocity model, F says that objects will move forward with constant velocity.

Note that, we use a lowercase letter F for a nonlinear function in an extended Kalman filter, and an uppercase F to indicate a linear matrix function. This is the deterministic part, but of course, our model assumption of constant velocity may be wrong, an object may break or accelerate. This is modeled by adding a random noise, Nu, which we assume zero mean and covariance Q. Nu is the so-called stochastic part. Remember that the covariance tells us how much the noise varies.

The bigger the entries in Q, the more acceleration and breaking we expect. For example, Q should be quiet high for an emergency braking assist, where we know that quick braking will occur. The overall state equation says, x_k equals f_x_k minus 1 plus the process noise, Nu. We have a similar setting for the measurement function. H is a heuristic measurement function which tells us how the measurement is related to the object.

Omega is the stochastic measurement noise with covariance metrics R. Large entries in R tells us that the measurements are quite noisy and may differ a lot from the actual state. The overall measurement equation is z equals h_x plus the measurement noise Omega. Now, let's take another look at our 1D example. By using the linear motion model with a constant velocity, the new location P of our vehicle is the old location plus velocity times Delta t.

Because we assume constant velocity, the new velocity is the same as the old velocity. We can alternatively expressed this in matrix form, and for the measurement function, our lidar only measures the object's position, not the velocity, so the measurement function looks like this. The measurement function can also be represented in matrix form like this. Therefore, we've found our system matrix F and our measurement matrix H, so don't be afraid of all those matrices and variables. Just to remember the system matrix F tells us how to get from one timestamp to the next, and the measurement matrix tells us how the measurements, Z, relates to the state X.

Now let's take another look at the Kalman filter formulas that you already know from Sebastian's lesson. In the prediction step, the state is predicted to the next timestamp by multiplying with F x minus equals F times x plus. Likewise, the estimation error covariant P is predicted to the next timestamp by multiplying with FP minus equals FP plus F transpose plus Q. In general, the uncertainty increases in the prediction step because of the process noise. We assume the object moves at a constant velocity, but in reality, the object might accelerate or decelerate.

Therefore, the process noise covariance Q is added to the transformed estimation error covariance P and increases the overall uncertainty. Note that the covariance P contains variances, which are squared standard deviations. Therefore, we also have to multiply twice with F and F transpose. If you are interested in more details on why we use the transpose here, you will learn more about it in the multi-target trekking lesson. But you can also check out the additional resources linked below this video.

For now, the detailed derivations are not important. In the update step, we first calculate the residual Gamma, which compares the new measurement z with the state estimation transform to the measurement space H times x. The measurement space is the space where the measurement lives in. For example, if C is a detection in an image, H would transform our estimated position x in world coordinates to the measurement space. H times x would be a projection to the image.

We do this because we can only calculate how much the predicted state differs from the measurement if both are given in the same coordinate system. It is in general much simpler to transform from state-space to measurements space, then vice versa. For example, we can project a 3D point to an image, but not vice versa, because a 2D image point lacks the third coordinate. The smaller the residual, the better our state estimation fits the measurement. S is the corresponding covariance of the residual.

For Gamma, we have to transform the estimation error covariance P to the measurement space by multiplying with H and H transpose, and we add the measurement noise covariance R. the formula is S equals HP H transpose plus R. With K, we denote the Kalman gain. The formula for K might seem cryptic, but the idea is straightforward. The Kalman gain weighs the predicted state in comparison to the measurement.

You can see this in the update formula for x, x plus equals x minus plus K times Gamma. The bigger K, the bigger the influence of Gamma, and the more we trust our measurement to be correct. The smaller k, on the other hand, the more we trust our prediction x minus, and the less influence we give to the measurement. Finally, we update the covariance matrix P In addition to the state x. P plus equals I minus K-H times P minus, where I is the identity matrix.

Remember from Sebastian's lesson that you don't have to fully understand or remember all of these formulas. A basic understanding of what happens in which step is sufficient. However, if you want to dive deeper into mathematical derivations of the Kalman Filter, check out the additional optional resources at the bottom of the page. Now, how do these formulas change if we have different sensors and use the Kalman filter for sensor fusion? Let's take another look at our fusion flowchart.

The prediction is always the same, whether we receive a Lidar or a camera measurement. We simply predict the measurement timestamp by applying the state transition function F. The update step differs depending on our sensor. If we have received a Lidar measurement, the measurement function is linear, so we can use the formula z minus H times x with the lighter measurement matrix, uppercase H Lidar to calculate the residual. In the case of a camera measurement, the measurement function is non-linear, so the residual is z minus H of x with the camera measurement function, lowercase h camera.

Finally, we update the state as usual. We will soon learn how to calculate the covariance update with nonlinear measurement functions.

## Additional Content

## Kalman Filter Overview
Now that we've looked back at the State Transition and Measurement functions, let's also review the Kalman Filter equations.
### Variables Summary

-

$f$

is the

$\textbf{state transition function}$

(in the linear case, it is a matrix

$\mathbf F$

, also called

$\textbf{system matrix}$

). It tells us how to get from one timestamp to the next:

$$x_k = f(x_{k-1})+\nu= \mathbf Fx_{k-1}+\nu$$

-

$\nu \sim \mathcal{N}\left(0, \mathbf Q\right)$

is the zero-mean

$\textbf{process noise}$

with covariance

$\mathbf Q$

.
-

$h$

is the

$\textbf{measurement function}$

(in the linear case, it is a matrix

$\mathbf H$

). It tells us how state and measurement are related:

$$z_k = h(x_k)+\omega= \mathbf Hx_k+\omega$$

-

$\omega \sim \mathcal{N}\left(0, \mathbf R\right)$

is the zero-mean

$\textbf{measurement noise}$

with covariance

$\mathbf R$

.
-

$\mathbf z$

is the

$\textbf{measurement vector}$

.
-

$\gamma = \mathbf z- \mathbf H\mathbf x$

is the

$\textbf{residual}$

with covariance

$\mathbf S = \mathbf H\mathbf P \mathbf H^T+\mathbf R$

.
-

$\mathbf K = \mathbf P \mathbf H^T\mathbf S^{-1}$

is the

$\textbf{Kalman gain}$

which weights prediction in comparison to measurement.  
### Kalman Filter Equations Summary

Prediction step:

$$\mathbf x^-=\mathbf F\mathbf x^+$$

$$\mathbf P^-=\mathbf F\mathbf P^+\mathbf F^T+\mathbf Q$$

Update step:

$$\gamma = \mathbf z- \mathbf H\mathbf x$$

$$\mathbf S = \mathbf H\mathbf P^- \mathbf H^T+\mathbf R$$

$$\mathbf K = \mathbf P^- \mathbf H^T\mathbf S^{-1}$$

$$\mathbf x^+ = \mathbf x^- +\mathbf K\gamma$$

$$\mathbf P^+ = \left(\mathbf I - \mathbf K\mathbf H \right)\mathbf P^-$$

### Additional Background on Kalman Filters
If you want to get a deeper understanding of the Kalman filter equations, check out the [derivation of the equations here](http://web.mit.edu/kirtley/kirtley/binlustuff/literature/control/Kalman%20filter.pdf).

You can also take a look at the [original Kalman Filter paper here](http://www.unitedthc.com/DSP/Kalman1960.pdf). Rudolf Kalman derived the Kalman filter as early as 1960, and the filter helped fly to the moon back then. Despite its age, the Kalman filter is still state-of-the-art today and running in most (or all) self-driving cars.

Isn't that amazing?
