# Polynomial Trajectory Generation

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=5ZzYOqYZZ3I)

## Summary

**Polynomial Trajectory Generation**
=====================================

This project involves implementing a polynomial solver to generate jerk-minimizing trajectories. The solver takes in current and goal vehicle states, as well as duration, and outputs six coefficients that define the polynomial describing the longitudinal trajectory.

**Key Concepts**
-----------------

* **Polynomial Solver**: A mathematical algorithm that generates a polynomial equation based on input parameters.
* **Jerk Minimizing Trajectory**: A type of motion planning that minimizes the rate of change of acceleration (jerk) to smooth out the vehicle's movement.
* **Longitudinal and Lateral Trajectories**: The solver generates two types of trajectories:
	+ Longitudinal: Describes the vehicle's position along its own axis (e.g., forward or backward).
	+ Lateral: Describes the vehicle's position relative to other vehicles in adjacent lanes.
* **Coefficients**: Six coefficients that uniquely define the polynomial equation describing the longitudinal trajectory.

**Practical Notes**
-------------------

The solver can be used in real-world scenarios, such as:
* Self-driving cars navigating through traffic
* Autonomous vehicles passing other vehicles on a road

To implement this project, you will need to:

1. Define the input parameters (current and goal vehicle states, duration) for the polynomial solver.
2. Implement the solver algorithm to generate the six coefficients that define the longitudinal trajectory.
3. Use the coefficients to compute the lateral trajectory based on input parameters.

Note: This summary provides a high-level overview of the key concepts and practical notes. You will need to consult additional resources or the Udacity lesson video for more detailed information on implementing the polynomial solver.

## Transcript

I am soon going to ask you to implement a polynomial solver to generate Jerk minimizing trajectories. But first, I want to show you how it's being used. Let's consider the S coordinates first. As an input, it takes the current vehicle state, the goal state, and the duration. And as an output, it will generate six coefficients, which uniquely define the polynomial that describes the longitudinal trajectory. Similarly, we feed input parameters to our solver regarding lateral configurations and compute the lateral trajectory. We can use this approach in a situation like this one, you have traffic and a self-driving car. And let's say that the requested behavior is to pass the vehicle in front of us. With polynomial trajectory generation, we take the current configuration of the car along with its velocity and acceleration as our start state. And then we specify a valid goal state that leads our vehicle in the other lane. We ship these states into our polynomial solver along with the desired duration that will allow for the maneuver. And we get a Jerk minimizing trajectory to the goal.
