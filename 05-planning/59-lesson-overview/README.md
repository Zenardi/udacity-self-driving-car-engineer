# Lesson Overview

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=NTgG9Tqn5Q8)

## Summary

**Motion Planning for Autonomous Vehicles**
=====================================

This lesson introduces the motion planning problem in the context of self-driving cars, presenting various techniques to solve it. The lesson covers four key areas: motion planning overview, path planning, velocity profile generation, and collision detection.

### Key Concepts

* **Motion Planning**: A critical component of autonomous driving software that enables vehicles to navigate through complex environments.
* **Path Planning**: A sub-problem of motion planning that involves determining the optimal path for a vehicle to follow.
	+ **Parametric Curves**: Mathematical representations of paths used in path planning.
	+ **Path Discretization**: Dividing a continuous path into discrete points.
* **Velocity Profile Generation**: Determining velocities at intermediate points and final speed to ensure smooth motion.
	+ **Linear Composition Velocity Profiles**: A technique for determining velocities using linear functions.
* **Collision Detection**: Ensuring the vehicle's path is collision-free in real-time environments.

### Practical Notes

To implement motion planning, you will need to:

* Use numerical approximation or optimization techniques to solve the path planning problem.
* Employ parametric curves and path discretization to represent paths.
* Calculate final speed and use linear composition velocity profiles to determine intermediate velocities.
* Implement collision detection algorithms to guarantee a collision-free path.

Note: This summary provides an overview of the key concepts and practical steps introduced in the lesson. It is intended as a starting point for further learning and exploration.

## Transcript

Hello everyone, and welcome to this lesson of the self-driving car Nanodegree. In this lesson, we're going to focus on the motion planning problem in the context of autonomous vehicles and present some of the techniques we can use to solve it. The lesson will be divided into four parts. The motion planning overview, a path planning section, velocity profile generation, and collision detection. First, we'll do an overview of motion planning by introducing the concept of motion planning, discussing where motion planning sits within the context of the overall autonomous driving software stack, formalizing the motion planning problem, and finally, we'll sub-divide motion planning into two smaller problems, path planning, and velocity generation.

Next, we'll go deeper into the path planning sub-problem. Specifically, we'll discuss parametric curves, which are convenient mathematical representations of the path, the main components of path planning, and in particular, how to exploit road structure to simplify the problem. The methods that we can use to solve the path planning problem including numerical approximation, and numerical optimization, and finally, path discretization, which is how we divide a continuous path into a set of discrete points. Following that, we will discuss the velocity profile generation sub-problem. We'll focus on two elements.

First, calculating the final speed at the end of the path, and using linear and linear composition velocity profiles to determine velocities at intermediate points prior to the final speed. Lastly, we'll jump into the final piece of the puzzle, which is collision detection. You'll learn to handle safety-critical tasks, of which collision detection is an example. Overcome the challenges of operating in real-time environments and implement the most common techniques used today in the autonomous driving industry to guarantee a collision-free path.

## Additional Content

The lesson will be divided in four parts: 
## 1. Motion Planning Overview
 - Introducing the concept of Motion Planning
 - Discussing where motion planning sits within the context of the overall Autonomous Driving software stack.
 - Formalizing the motion planning problem
 -  And finally, we’ll subdivide motion planning into two smaller problems:
 - Path Planning,
 - Velocity Generation

## 2. Path Planning
 - Parametric curves, which are convenient mathematical representation of paths
 - The main components of path planning,
 - How to exploit road structure to simplify the problem
 - The Methods that we can use to solve the Path Planning Problem:
    - Numerical approximation
    - Numerical optimization
 - Path discretization

## 3. Velocity Profile Generation
  - Calculating the final speed at the end of the path
  - Using linear velocity and composition profiles to determine velocity at intermediate points prior to that final speed.

## 4. Collision Detection
  - Safety-critical task
  - Overcome the challenges of operating in a real-time environment
  - Implement the most common techniques used today in the Autonomous Driving industry to guarantee a collision free path
