# Derivation Overview

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=TuVp_HhQq7A)

## Summary

**Jerk Minimizing Trajectory Coefficients**
=============================================

This README file summarizes the key concepts and practical steps for finding the six coefficients that describe a quintic polynomial representing a jerk minimizing trajectory.

### Key Concepts

* **Quintic Polynomial**: A polynomial of degree 5, used to represent the position of a jerk minimizing trajectory.
* **Boundary Conditions**: Six conditions that define the initial and final positions, velocities, and accelerations of the trajectory.
* **Differentiation**: The process of differentiating the equations of motion to obtain the velocity and acceleration equations.
* **Matrix Inversion**: A mathematical technique used to solve systems of linear equations, represented by a matrix.

### Practical Notes

To find the six coefficients that describe the quintic polynomial, follow these steps:

1. Differentiate the position equation twice to obtain the velocity and acceleration equations.
2. Set the initial time as zero to simplify the problem and reduce the number of unknowns from 6 to 3.
3. Identify the known terms in the simplified equations and separate them from the unknown variables.
4. Represent the system of equations using a matrix, where the known quantities are separated from the unknown variables.
5. Invert the matrix using a mathematical library to solve for the three unknown parameters.

Note: The instructor mentions that this problem can be solved using a matrix inversion technique, which will be covered in later lessons.

## Transcript

<v English>In the previous video,</v> <v English>I showed you that the position of a jerk</v> <v English>minimizing trajectory is given by a quintic polynomial.</v> <v English>In this video, I'm going to present a quick and non-rigorous</v> <v English>walk through of how we find the six coefficients that describe these polynomial.</v> <v English>It is not essential that you remember the details of this,</v> <v English>but you might find it interesting.</v> <v English>First, we differentiate the equations of</v> <v English>the position in order to get the equations for the velocity,</v> <v English>and then we differentiate it again in order to get the equation for the acceleration.</v> <v English>Now, we could just plug in our six boundary conditions to get the six equations.</v> <v English>But first we're going to do something that will make our life a little bit easier.</v> <v English>We're going to set the initial time as zero and when we do that, we find this.</v> <v English>Which means that three or four unknowns don't need to be identified anymore,</v> <v English>which reduces the program from six unknowns to three.</v> <v English>It simplifies those three trajectories by removing three of the unknowns here.</v> <v English>We can gather the known terms into functions of</v> <v English>the star boundary conditions to make it look like a bit cleaner.</v> <v English>The C1, C2, and C3 terms are functions of the initial conditions.</v> <v English>What remains is that we only have to identify three parameters,</v> <v English>that depends only on our N boundary condition.</v> <v English>Those equations look like this,</v> <v English>and we know the final position,</v> <v English>velocity and acceleration at time tf since those are all the quantities that we beat.</v> <v English>Since we know them,</v> <v English>a more useful way to think of these equations is like this,</v> <v English>where I have deliberately separated</v> <v English>the known quantities from the unknown variables that we wish to determine.</v> <v English>This is starting to look like a very solvable system of three equations.</v> <v English>The best way to solve this is with a matrix that looks like this,</v> <v English>and this problem can be solved by inverting this matrix</v> <v English>using any matrix mathematical library, which we will do later.</v>

## Additional Content

There is an error on multiple occasions with equation

$\ddot{s}$

- the

$\alpha_6$

should be

$\alpha_3$

.
