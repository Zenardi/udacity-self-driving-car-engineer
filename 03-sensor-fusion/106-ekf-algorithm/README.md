# EKF Algorithm

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=XQjIcx-EWLI)

## Summary

**Extended Kalman Filter Algorithm**
=====================================

The Extended Kalman Filter (EKF) is a nonlinear version of the Kalman filter algorithm used for state estimation in systems with complex relationships between states and measurements.

### Key Concepts
* **Nonlinear Measurement Function**: A function that maps the system's state to the measurement space, represented by lowercase `f` and `h`.
* **Jacobian Matrices**: Derivatives of the nonlinear functions with respect to the state variables, used in place of linear matrices in the EKF algorithm. The Jacobian of the measurement function is denoted as `H_j`, and the Jacobian of the system's state transition function is denoted as `F_j`.
* **State Estimation Error Covariance**: A measure of the uncertainty associated with the estimated state, represented by matrix `P`.

### Practical Notes
To implement the EKF algorithm, you will need to:

* Define the nonlinear measurement function and its Jacobian.
* Calculate the Jacobians of the measurement function and the system's state transition function at each time step.
* Update the estimation error covariance using the modified equations.

Note that the EKF algorithm is an extension of the linear Kalman filter, with modifications to account for nonlinear relationships between states and measurements.

## Transcript

We now have everything we need in order to understand the full extended Kalman filter algorithm. In the prediction step, we now use the nonlinear measurement function, lowercase f to predict the state to the next time step. Then we calculate the Jacobian F_j at the current state X. Finally, we update the estimation error covariance P as usual, just with the Jacobian instead of the state transition function F. In the update step, we apply similar modifications.

First, we transform the status summation X to the measurement space with the nonlinear measurement function lowercase h and calculate our residual. Then we calculate the Jacobian H_j at the current state X. Finally, we update all covariances where we use the Jacobian instead of the measurement function and that's it. These equations are not that different from the linear Kalman filter, are they?

## Additional Content

## EKF Algorithm
### Extended Kalman Filter Equations

Although the mathematical proof is somewhat complex, it turns out that the Kalman filter equations and extended Kalman filter equations are very similar. 

The main differences are:

- The

$\textbf F$

matrix will be replaced by

$\mathbf F_J$

when calculating

$\mathbf P^-$

.
- The

$\textbf H$

matrix will be replaced by

$\mathbf H_J$

when calculating

$\mathbf S$

,

$\mathbf K$

, and

$\mathbf P^+$

.
- To calculate

$\mathbf x^-$

, the prediction update function,

$f$

, is used instead of the

$\textbf F$

matrix.
- To calculate

$\gamma$

, the measurement function,

$h$

, is used instead of the

$\textbf H$

matrix.

For the final project, however, we do not need to use the

$f$

function or

$\mathbf F_J$

, because we are using a linear model for the prediction step. So, for the prediction step, we can still use the regular Kalman filter equations and the

$\textbf F$

matrix rather than the extended Kalman filter equations.

The measurement update for lidar will also use the regular Kalman filter equations, since lidar uses linear equations. Only the measurement update for the camera sensor will use the extended Kalman filter equations.

One important point to reiterate is that the equation

$\gamma=\mathbf z-\mathbf H\mathbf x$

for the Kalman filter does not become

$\gamma =\mathbf z-\mathbf H_J\mathbf x$

for the extended Kalman filter. Instead, for extended Kalman filters, we'll use the

$h$

function directly to map predicted locations

$\mathbf x^-$

from cartesian to image coordinates.
