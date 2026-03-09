# Sigma Point Prediction Exercise

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=RQvnRpSPUak)

## Summary

**Predicting Sigma Points**
==========================

This lesson focuses on predicting sigma points using an augmented state vector. The goal is to calculate the predicted values of the sigma points.

### Key Concepts

* **Sigma points**: These are a set of points used in the Kalman filter algorithm to represent the mean and covariance of a probability distribution.
* **Augmented state vector**: This includes not only the original state variables (position, velocity, yaw angle, etc.) but also additional noise values that are used to calculate the predicted sigma points.
* **Process model**: A mathematical representation of how the system evolves over time. In this case, it's a matrix that needs to be filled with the predicted sigma points.

### Practical Notes

To implement the CTR (Continuous-Time Representation) remodel in C++ code:

1. Make sure to include all the necessary noise values in the augmented state vector.
2. Implement the process model using the predicted sigma points and delta_t (time step).
3. Consider the effect of division by zero when implementing the process model.
4. Use the predicted sigma points to fill in the matrix that represents the system's behavior over time.

Note: This summary is a brief overview of the key concepts and practical steps covered in the lesson. It's intended to provide a quick reference for readers who want to understand the main ideas without having to watch the entire video.

## Transcript

<v English>This time your goal is to</v>
<v English>predict the sigma points.</v> <v English>So we start from a point where we</v>
<v English>already have the augmented sigma points.</v> <v English>Let's quickly repeat the meaning</v>
<v English>of each of these points.</v> <v English>This column is one sigma point.</v> <v English>We have here a value for the position x.</v> <v English>For the position y, for</v>
<v English>the velocity v, for</v> <v English>the yaw angle psi, and</v>
<v English>for the yaw rate psi dot.</v> <v English>This value is the longitudinal</v>
<v English>acceleration noise mu a.</v> <v English>And this value is the yaw</v>
<v English>acceleration noise mu psi dot dot.</v> <v English>The noise values are mostly 0.</v> <v English>But not for all sigma points,</v>
<v English>as you can see here.</v> <v English>Make sure to also put these two noise</v>
<v English>values correctly into the process model.</v> <v English>This is the matrix you want to fill</v>
<v English>with with the predicted sigma points.</v> <v English>And, of course, you need delta_t</v>
<v English>if you want to calculate numbers.</v> <v English>The main thing you have to do here is</v>
<v English>implement the CTR remodel into C++ code.</v> <v English>Make sure to also consider</v>
<v English>the effect of the process modes, and</v> <v English>to catch division by zero.</v> <v English>All right, good luck.</v>

## Additional Content

### Helpful Equations

$$x = \begin{bmatrix}
p_x \\
p_y \\
v \\
\psi \\
\dot{\psi}
\end{bmatrix}$$

#####  If

$\large \dot{\psi}_k$

is not zero:

$$\text{State}= x_{k+1} = x_k + \begin{bmatrix}
\frac{v_k}{\dot{\psi}_k}(sin(\psi_k+\dot{\psi}_k\Delta t )-sin(\psi_k))\\
\frac{v_k}{\dot{\psi}_k}(-cos(\psi_k+\dot{\psi}_k\Delta t )+cos(\psi_k))\\
0\\
\dot{\psi}_k\Delta t\\
0
\end{bmatrix} 
+\begin{bmatrix}
\frac{1}{2}(\Delta t)^2cos(\psi_k)\nu_{a,k}\\
\frac{1}{2}(\Delta t)^2sin(\psi_k)\nu_{a,k}\\
\Delta t\cdot\nu_{a,k}\\
\frac{1}{2}(\Delta t)^2\nu_{\ddot{\psi},k}\\
\Delta t\cdot\nu_{\ddot{\psi},k}
\end{bmatrix}$$

#####  If

$\large \dot{\psi}_k$

is zero:

$$\text{State} =x_{k+1} = x_k + \begin{bmatrix}
v_kcos(\psi_k)\Delta t\\
v_ksin(\psi_k)\Delta t\\
0\\
\dot{\psi}_k\Delta t\\
0
\end{bmatrix}
+\begin{bmatrix}
\frac{1}{2}(\Delta t)^2cos(\psi_k)\nu_{a,k}\\
\frac{1}{2}(\Delta t)^2sin(\psi_k)\nu_{a,k}\\
\Delta t\cdot\nu_{a,k}\\
\frac{1}{2}(\Delta t)^2\nu_{\ddot{\psi},k}\\
\Delta t\cdot\nu_{\ddot{\psi},k}
\end{bmatrix}$$

Notice that when

$\large \dot{\psi_k} = 0,$

the term

$\large \dot{\psi_k}\Delta{t}$

would also equal zero.

>Note: 
* The assignment files are present in `/home/workspace/assignments/03_sigma_point_prediction` and the solution files are present in `/home/workspace/solutions/03_sigma_point_prediction`

* After completing the assignment, you can run the code from the workspace terminal as follows:
	```bash
    cd /home/workspace/assignments/03_sigma_point_prediction
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
* Test your output against the output of the solution code. You can run the solution code as follows:
	```bash
    cd /home/workspace/solutions/03_sigma_point_prediction
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
