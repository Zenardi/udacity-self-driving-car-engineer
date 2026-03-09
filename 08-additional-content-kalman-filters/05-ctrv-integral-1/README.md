# CTRV Integral 1

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=dcR9RtwJ6yk)

## Summary

**Summary of Complete Differential Equation**

This lesson covers the complete differential equation, a fundamental concept in physics and engineering. The instructor explains how to derive the equation for time step k+1 from time step k.

### Key Concepts

* **Delta t**: The difference between two consecutive continuous time values (tk+1 - tk).
* **Complete Differential Equation**: A mathematical equation that describes the relationship between the state of a system at time k and its evolution over time.
* **Integral Over Time**: A mathematical operation used to calculate the accumulation of a quantity over a specified time interval.

### Practical Notes

The instructor provides a step-by-step approach to deriving the complete differential equation:

1. Identify the discrete time steps (k and k+1) and their corresponding continuous time values (tk and tk+1).
2. Calculate Delta t as the difference between tk+1 and tk.
3. Express the state of the system at time k+1 in terms of its initial state at time k and an integral over time.

Note that this lesson assumes constant weight and velocity, which simplifies the calculation of the integral.

## Transcript

<v English>We have the complete differential</v>
<v English>equation now, awesome.</v> <v English>But how do we get from time</v>
<v English>step k to time step k+1?</v> <v English>Let's say the discrete time step k</v>
<v English>relates to the continuous time value tk,</v> <v English>and the discrete time step k+1 relates</v>
<v English>to the continuous time value tk + 1.</v> <v English>The difference between tk +1 and</v>
<v English>tk is called Delta t.</v> <v English>Then this date at time k + 1</v>
<v English>is given by the state of time</v> <v English>k + the integral over x.,</v>
<v English>from time tk to time tk + 1.</v> <v English>This can potentially be</v>
<v English>a very complex calculation.</v> <v English>But in the special case of the CTRB,</v> <v English>this integral can be</v>
<v English>solved pretty easily.</v> <v English>In the first two rows, I will just</v>
<v English>insert the terms of the differential</v> <v English>equation without solving the integral,</v>
<v English>we will do this later.</v> <v English>Let's start with the last three</v>
<v English>rows which are the easiest.</v> <v English>Even if you don't really remember</v>
<v English>how to solve an integral,</v> <v English>you still might be able to choose</v>
<v English>the correct answer in the quiz below.</v> <v English>Remember we assume the weight and</v>
<v English>velocity are constant.</v>

## Additional Content

### Question 1:

$\int_{t_k}^{t_{k+1}} \dot{v}(t) \space dt$

= ???

A.

$0$

B.

$v_k \cdot \Delta t$

### Question 2:

$\int_{t_k}^{t_{k+1}} \dot{\psi}(t) \space dt$

= ???

A.

$0$

B.

$\dot{\psi}_k \cdot \Delta t$

### Question 3:

$\int_{t_k}^{t_{k+1}} \ddot{\psi}(t) \space dt$

= ???

A.

$0$

B.

$\dot{\psi}_k \cdot \Delta t$
