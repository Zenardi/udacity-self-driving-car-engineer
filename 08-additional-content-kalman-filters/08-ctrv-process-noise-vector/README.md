# CTRV Process Noise Vector

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Qr99RXys-G0)

## Summary

**README: Understanding Stochastic Process Models**

This project focuses on introducing stochastic elements to process models. A key aspect of this topic is understanding how noise affects the overall model.

### Key Concepts

* **Deterministic vs. Stochastic Process Model**: The deterministic part of a process model describes the expected behavior, while the stochastic part accounts for uncertainty and randomness.
* **Noise Vector (new k)**: A two-dimensional vector consisting of independent scalar noise processes:
	+ **Longitudinal Acceleration Noise (new a)**: Normally distributed white noise with zero mean and variance σ_a^2.
	+ **Yaw Acceleration Noise (new sin_dot_dot)**: Normally distributed white noise with zero mean and variance σ_yaw_dot_dot^2.
* **Influence of Noise on Process Model**: The noise vector affects the process model by introducing uncertainty in its behavior.

### Practical Notes

To apply this knowledge, you can follow these steps:

1. Calculate the influence of the yaw acceleration noise on the yaw rate using the formula: `yaw_acceleration * delta_t`.
2. Consider the longitudinal acceleration (u) as constant between time steps k and k+1.
3. Understand how the noise processes (`new a` and `new sin_dot_dot`) affect the yaw angle and velocity.

Note that this is a theoretical introduction to stochastic process models, and further implementation details may require additional context or code snippets.

## Transcript

<v English>What we have introduced so far was the</v>
<v English>deterministic part of the process model.</v> <v English>But of course, we also need to consider</v>
<v English>the stochastic part of the process model</v> <v English>and that has something to do</v>
<v English>with the process noise new k.</v> <v English>We will describe the uncertainty of</v>
<v English>the process model with a two-dimensional</v> <v English>noise vector new k, consisting of two</v>
<v English>independent scalar noise processes.</v> <v English>The first noise process is the</v>
<v English>longitudinal acceleration noise new a.</v> <v English>It influences the longitudinal</v>
<v English>speed of the vehicle and</v> <v English>it randomly changes its</v>
<v English>value at every time step k.</v> <v English>The longitudinal acceleration</v>
<v English>is a normally distributed white</v> <v English>noise with zero mean and</v>
<v English>the variance sigma a squared.</v> <v English>The other noise process is the yaw</v>
<v English>acceleration new site dot dot.</v> <v English>It is also a normal distributed</v>
<v English>white noise with zero mean and</v> <v English>it has the variance sigma</v>
<v English>yaw dot dot squared.</v> <v English>And what I want to discuss with you</v>
<v English>next is how the noise vector new</v> <v English>k influences our process model.</v>

<v English>How does the noise vector affect</v>
<v English>the overall process model?</v> <v English>Let's do this again row for row starting</v>
<v English>from the bottom with the yaw rate.</v> <v English>Assuming the yaw</v>
<v English>acceleration new sin delta</v> <v English>is constant between k and k plus one.</v> <v English>It will just linearly add up to</v>
<v English>the yaw rate with increasing time.</v> <v English>So,the influence of the yaw</v>
<v English>acceleration on the yaw rate</v> <v English>is the yaw acceleration times delta t.</v> <v English>Can you calculate the influence of</v>
<v English>the noise processes as new a and</v> <v English>new sin delta on the yaw angle and</v>
<v English>the velocity.</v> <v English>Consider that the longitudinal</v>
<v English>acceleration, u,</v> <v English>a is also constant constant</v>
<v English>between k and k plus one.</v>

## Additional Content

### 1) What is the influence of

$\nu_{a,k_{}}$

and

$\nu_{\ddot{\psi},k}$

on the velocity?

In other words, what is

$c$

in the process model?

A.

$\Large \Delta t \cdot \nu_{\ddot{\psi},k}$

B.

$\Large \Delta t \cdot \nu_{a,k}$

### 2) What is the influence of

$\nu_{a,k_{}}$

and

$\nu_{\ddot{\psi},k}$

on the yaw angle?

In other words, what is

$d$

in the process model?

A.

$\Large \frac{1}{2}(\Delta t)^2 \cdot \nu_{\ddot{\psi},k}$

B.

$\Large \Delta t \cdot \nu_{\ddot{\psi},k}$

### 3) What is the influence of

$\nu_{a,k_{}}$

and

$\nu_{\ddot{\psi},k}$

on the yaw rate?

In other words, what is

$\large e$

in the process model?

A.

$\Large \Delta t \cdot \nu_{a,k}$

B.

$\Large \Delta t \cdot \nu_{\ddot{\psi},k}$
