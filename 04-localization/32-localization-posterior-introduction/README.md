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

Here is a picture from the introduction when you first encountered localization. We have a map with all these landmarks in a global coordinate system, observations from the on-board censor and the local coordinates system, and we also have the information how the car moves between two timesteps. Formally, the observations are defined as a vector z which includes all observations from timestep one to t. The observations could be range measurements, bearing angles, or images, for example. We also have the controls of the car as a vector u which includes all control elements from timestep one to t. Typically, you have low pitch or roll rates and velocity information. Finally, we have the map. The map could be a grid map of the global environment, or a database which includes global feature points and the lane geometry. Here, we do not add the time index t to the map because we assume the map does not change over time, and we assume these variables are known. Again, what we want to estimate is the transformation between the local coordinate system of the car and the global coordinate system of the map. If we know this transformation, then we also know the posts of the car in the global map. The position of the car at time t is defined with x. If we assume we have a 2D map for example, x includes a position with x and y coordinates and also the orientation phi. And these values are unknown. We will never know the state xt with perfect accuracy. What we want is to form a sufficiently accurate belief of the state xt, and we want to formulate this belief in a probabilistic way. Now here's a good question: Could you write down the posterior for the belief xt?

## Additional Content

## Formal Definition of Variables

$z_{1:t}$ represents the observation vector from time 0 to t (range measurements, bearing, images, etc.).

$u_{1:t}$ represents the control vector from time 0 to t (yaw/pitch/roll rates and velocities).

$m$ represents the map (grid maps, feature maps, landmarks)

$x_t$ represents the pose (position (x,y) + orientation $\theta$)


