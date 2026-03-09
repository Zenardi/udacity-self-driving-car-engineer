# Localization Posterior: Introduction

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=WCva9DtGgGA)

## Summary

**Localization and State Estimation**

This project focuses on localization, which is the process of determining the position and orientation of an object (in this case, a car) in a global coordinate system. The goal is to estimate the transformation between the local coordinate system of the car and the global coordinate system of the map.

### Key Concepts

* **Observations**: A vector `z` that includes all observations from timestep 1 to `t`, which can be range measurements, bearing angles, or images.
* **Controls**: A vector `u` that includes all control elements from timestep 1 to `t`, typically low pitch or roll rates and velocity information.
* **Map**: A global coordinate system that represents the environment, which can be a grid map or a database of feature points and lane geometry.
* **State Estimation**: The process of forming a sufficiently accurate belief of the state `xt` in a probabilistic way.
* **Posterior Distribution**: The probability distribution over the state `xt`, given all available observations and controls.

### Practical Notes

To implement localization, you will need to:

* Define the observation vector `z` and control vector `u`
* Choose a map representation (grid map or database)
* Implement a method for estimating the transformation between the local and global coordinate systems
* Use probabilistic methods to form a belief of the state `xt`

Note: This project assumes that the map does not change over time, and that all variables are known. The goal is to estimate the position and orientation of the car in the global coordinate system with sufficient accuracy.

## Transcript

<v English>Here is a picture from the introduction when you first encountered localization.</v> <v English>We have a map with all these landmarks in a global coordinate system,</v> <v English>observations from the on-board censor and the local coordinates system,</v> <v English>and we also have the information how the car moves between two timesteps.</v> <v English>Formally, the observations are defined as a vector z which includes</v> <v English>all observations from timestep one to t. The observations could be range measurements,</v> <v English>bearing angles, or images, for example.</v> <v English>We also have the controls of the car as a vector u which includes</v> <v English>all control elements from timestep one to t. Typically,</v> <v English>you have low pitch or roll rates and velocity information.</v> <v English>Finally, we have the map.</v> <v English>The map could be a grid map of the global environment,</v> <v English>or a database which includes global feature points and the lane geometry.</v> <v English>Here, we do not add the time index t to the map</v> <v English>because we assume the map does not change over time,</v> <v English>and we assume these variables are known.</v> <v English>Again, what we want to estimate is the transformation between</v> <v English>the local coordinate system of the car and the global coordinate system of the map.</v> <v English>If we know this transformation,</v> <v English>then we also know the posts of the car in the global map.</v> <v English>The position of the car at time t is defined with x.</v> <v English>If we assume we have a 2D map for example,</v> <v English>x includes a position with x and y coordinates and also the orientation phi.</v> <v English>And these values are unknown.</v> <v English>We will never know the state xt with perfect accuracy.</v> <v English>What we want is to form a sufficiently accurate belief of the state xt,</v> <v English>and we want to formulate this belief in a probabilistic way.</v> <v English>Now here's a good question: Could you write down the posterior for the belief xt?</v>

## Additional Content

## Formal Definition of Variables

$z_{1:t}$

represents the observation vector from time 0 to t (range measurements, bearing, images, etc.).

$u_{1:t}$

represents the control vector from time 0 to t (yaw/pitch/roll rates and velocities).

$m$

represents the map (grid maps, feature maps, landmarks)

$x_t$

represents the pose (position (x,y) + orientation

$\theta$

)


### Quiz

Given the map, the control elements of the car, and the observations, what is the definition of the posterior distribution for the state x at time t?

(A)

$$bel(x_t) = p(x_t|z_t, m, u_t)$$

(B)

$$bel(x_t) = p(x_t| z_{1:t}, u_{1:t})$$

(C)

$$bel(x_t) = p(x_t, m_t|z_{1:t}, u_{1:t})$$

(D)

$$bel(x_t) = p(x_t|z_{1:t}, u_{1:t}, m)$$
