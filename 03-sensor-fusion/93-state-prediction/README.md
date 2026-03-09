# State Prediction

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=M-ULhwlSIPQ)

## Summary

**Kalman Filter for 2D Position and Velocity Estimation**
===========================================================

This project extends the Kalman filter implementation from the previous lesson to estimate a 2D position and velocity using measurements in 2D.

### Key Concepts
* **State Vector**: A 4D vector representing the current state of the system, consisting of x-position (`Px`), y-position (`Py`), x-velocity (`Vx`), and y-velocity (`Vy`).
* **Linear Motion Model**: The same model used in the previous lesson, where new positions are calculated as old positions plus velocity times delta t.
* **Process Noise**: A 4D vector representing the uncertainty of the system's dynamics, which is now a 4D vector to account for changes in both x and y axes.
* **State Transition Equation**: Expressed in matrix form, this equation describes how the state vector evolves over time.
* **Elapsed Time**: The time between two consecutive observations, which may vary and must be calculated at each time step.

### Practical Notes
To implement a Kalman filter for 2D position and velocity estimation:

1. Define the 4D state vector `X` with components `Px`, `Py`, `Vx`, and `Vy`.
2. Update the linear motion model to account for changes in both x and y axes.
3. Calculate the elapsed time between two consecutive observations at each time step.
4. Use the process noise as a 4D vector to represent uncertainty in the system's dynamics.

Note: This project includes quizzes to challenge your intuition about the process noise, so be sure to review the material carefully before attempting them.

## Transcript

Congratulations, you have just implemented the Kalman filter for 1D tracking problem. But now, let's say that our sensors are able to deliver measurements in 2D, and that we want to estimate a 2D position and 2D velocity. We have a 4D the state vector X equals Px, Py, Vx, Vy. We'll use the same linear motion model as before with constant velocity. The new x and y positions will be the old positions plus the displacement, which is the same as velocity times delta t.

The velocity along both x and y axes stays the same. Again, we at a process most new, which is now also a 4D vector. This gives us the following state transition equation expressed in a matrix form. Another change is that delta t is not necessarily constant anymore. In reality, the time elapse between two consecutive observations might vary, therefore, we have to calculate the elapsed time between two measurements at each time step.

In the following, let's look a little closer at the process most new, because you didn't use this before with Sebastian. I want to challenge your intuition with two quizzes.

## Additional Content

## State Prediction
For 2D motion and velocity, the constant velocity system matrix is:

$$\mathbf{F}(\Delta t) =
\begin{pmatrix}
1 & 0 & \Delta t & 0 \\
0 & 1 & 0 & \Delta t \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 
\end{pmatrix}$$

The state transition equation in 2D space is:

$$\begin{pmatrix}
 p_x  \\
 p_y   \\
 v_x  \\
 v_y
\end{pmatrix} =
\begin{pmatrix}
1 & 0 & \Delta t & 0  \\
0 & 1 & 0 &  \Delta t  \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
 p_x  \\
 p_y   \\
 v_x  \\
 v_y
\end{pmatrix}
+
\begin{pmatrix}
\nu_{p_x}  \\
\nu_{ p_y }  \\
\nu_{ v_x } \\
\nu_{ v_y} 
\end{pmatrix}$$

Reminder: The process noise

$\nu$

refers to the uncertainty in the object's position and velocity when predicting. The model assumes velocity is constant between time intervals, but in reality we know that an object's velocity can change due to acceleration. The model includes this uncertainty via the process noise.
From the examples I've just showed you we can see that the process noise depends on both 1) the elapsed time and 2) the uncertainty of acceleration. So, how can we model the process noise by considering both of these factors? Keep going to find out!
