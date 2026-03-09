# Augmentation Exercise

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=5p-PqtxQeM8)

## Summary

**Augmentation in C++ Code**
==========================

This README file provides a summary of key concepts and practical steps for augmenting state estimation code in C++. The main topic is implementing an augmented state using C++.

### Key Concepts
* **Augmented State**: A 7-dimensional vector that combines the original state with additional variables, such as variance of longitudinal acceleration and yaw acceleration.
* **Process Noise Covariance Matrix (Q)**: A matrix that represents the uncertainty in the system's dynamics, calculated from the variance of acceleration noises.
* **Augmented Mean State (x_aug)**: The mean value of the augmented state, which takes into account the zero-mean value of acceleration noises.
* **Augmented Covariance Matrix (P_aug)**: The covariance matrix of the augmented state, used to propagate uncertainty through time.

### Practical Notes
To implement augmentation in C++ code:

1. Calculate the process noise covariance matrix Q using the variance of longitudinal and yaw accelerations.
2. Build the augmented mean state x_aug by combining the original state with additional variables (e.g., acceleration noises).
3. Construct the augmented covariance matrix P_aug, paying attention to its dimensions.

Note: Consult the provided cheat sheet for reference on building the augmented state and covariance matrices.

## Transcript

<v English>Okay, let's put</v>
<v English>the augmentation into C++ code.</v> <v English>Now the dimension of</v>
<v English>the augmented state is 7.</v> <v English>Other things you will need</v>
<v English>are the variance of the longitudinal</v> <v English>acceleration and the yaw acceleration.</v> <v English>Together, they build the process noise</v>
<v English>covariance matrix which we call Q.</v> <v English>The rest is almost the same</v>
<v English>as in the last person.</v> <v English>But this time, you have to build</v>
<v English>the augmented state mean x_aug, and</v> <v English>the augmented covariance matrix P_aug.</v> <v English>Again, have a look at the cheat sheet,</v>
<v English>it will also help you here.</v> <v English>When you build the augmented mean state,</v> <v English>consider that the mean value of</v>
<v English>the acceleration noises are both zero.</v> <v English>And this is where</v>
<v English>the augmented sigma points go.</v> <v English>Pay attention to</v>
<v English>the dimensions of this matrix.</v> <v English>Good luck with the quiz.</v>

## Additional Content

### Cheat Sheet

Augmented State =

$$\large
x_{a,k} = \begin{bmatrix}
p_x\\
p_y\\
v\\
\psi\\
\dot{\psi}\\
\nu_a\\
\nu_{\ddot{\psi}}
\end{bmatrix}$$

Note: The mean of the process noise is zero.

Augmented Covariance Matrix =

$$\large
P_{a,k|k} = \begin{bmatrix}
 P_{k|k} \quad 0 \\
0 \qquad Q
\end{bmatrix}$$

### Helpful Matrix and Vector Functions:
Quickly set `vector y` as first `n` elements of `vector x`.

`x.head(n) = y`, where `n` is the number of elements from first element, and `y` is an input vector of that size.

Quickly set `matrix y` to top left corner of `matrix x`.

`x.topLeftCorner(y_size, y_size)`

Reminder of what function to use to take the square root of a `matrix x`,

`x.llt().matrixL()`;



>Note: 
* The assignment files are present in `/home/workspace/assignments/02_augmentation` and the solution files are present in `/home/workspace/solutions/02_augmentation`

* After completing the assignment, you can run the code from the workspace terminal as follows:
	```bash
    cd /home/workspace/assignments/02_augmentation
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
* Test your output against the output of the solution code. You can run the solution code as follows:
	```bash
    cd /home/workspace/solutions/02_augmentation
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
