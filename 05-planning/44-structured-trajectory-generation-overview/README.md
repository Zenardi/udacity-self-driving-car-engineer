# Structured Trajectory Generation Overview

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=N2cwqKR63x8)

## Summary

**Trajectory Planning with Jerk Minimization**
=====================================================

This project focuses on developing a method for trajectory planning in structured environments, such as highway driving. The approach uses **Jerk minimization**, which generates smooth trajectories between a start and goal configuration.

### Key Concepts
* **Jerk**: the rate of change of acceleration (m/s^3)
* **Polynomial trajectories**: used to generate smooth motion plans
* **Coefficients computation**: derivation of polynomial coefficients for Jerk minimizing trajectories

### Practical Notes
To apply this method, you can follow these steps:

1. Define a start and goal configuration.
2. Use polynomials to generate a trajectory that minimizes jerk.
3. Compute the coefficients of the polynomial using the provided derivation.
4. Evaluate the drive-ability of the generated trajectory.
5. Compare multiple trajectories to select the best one for your specific situation.

Example code or formulas are not included in this transcript, but you can expect to work with mathematical models and algorithms to implement Jerk minimization and polynomial trajectories.

## Transcript

In the next few segments, I'm going to present a method for trajectory planning that is useful in structured environments like highway driving. To do that, I'll introduce the idea of Jerk minimization to generate a nice trajectory from a start configuration to a goal configuration. I will show you how to generate Jerk minimizing trajectories using polynomials and then present a brief derivation on how to compute the coefficients of the polynomial that solves our problem. Then I will show you an example of what one such trajectory looks like on the highway and how we can evaluate its drive-ability and compare it to other trajectories. Finally, I will show you how by generating many similar jerk minimizing trajectories we can compare them and select the best one for the situation we want to drive through.
