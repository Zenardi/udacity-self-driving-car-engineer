# Implementation Details for Motion Model

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=O47bOcJm1eE)

## Summary

**Motion Model Implementation**
=====================================

This README file provides an overview of the key concepts and practical steps required to implement the prediction step in a navigation system. The motion model is used to predict the position of a car based on its previous location and movement.

**Key Concepts**
---------------

* **Transition Model**: The transition model is controlled by `x_t - 1` (previous position) and `u_t` (direct move in driving direction).
* **Independence from Map**: The transition model assumes independence from the map, meaning it only considers the car's movement and not its location on the map.
* **1D Normal Distribution**: The transition model is defined by a 1D normal distribution with mean `u_t` and standard deviation `sigma_u_t`.
* **Sigma of u_t**: The sigma (standard deviation) of `u_t` is set to 1 meter, representing the uncertainty in the car's movement.
* **State Space Range**: The state space range is from 0 to 99 meters with a 1-meter step resolution.

**Practical Notes**
-------------------

To implement the motion model, you will need to:

* Define the transition model using the 1D normal distribution formula: `p(x_t | x_{t-1}, u_t) = N(u_t, sigma_u_t)`
* Evaluate the probability at position `x_t - x_{t-1}` using the defined mean and standard deviation
* Use a 1-meter step resolution for the state space range (0 to 99 meters)

Note: This is just an overview of the key concepts and practical steps. For more detailed implementation instructions, please refer to the accompanying code or additional resources.

## Transcript

<v English>Before you start coding,</v> <v English>you'll need some details to help with implementing the prediction step.</v> <v English>At the very beginning,</v> <v English>the assumption is that the car is parked at a tree or a street lamp plus/minus one meter.</v> <v English>This means, the car could be here,</v> <v English>here, here, and so on.</v> <v English>The transition model is controlled only by x_t minus one and u_t.</v> <v English>Here we assume, the transition model is independent from the map.</v> <v English>Remember that u_t is a direct move pointed in driving direction.</v> <v English>The transition model is defined by</v> <v English>the 1D normal distribution defined by the mean u_t and sigma u_t,</v> <v English>and we have to evaluate at position x_t minus x_t minus 1_i.</v> <v English>Here, the sigma of u_t is one meter.</v> <v English>The state space range is from zero to 99 meters with a one-meter step resolution.</v> <v English>Now you have all information to implement the motion model.</v> <v English>So, before we go back to the code,</v> <v English>I have a small quiz for you.</v>
