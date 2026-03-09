# Lesson Conclusion

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2t5JFyqCObo)

## Summary

**Motion Planning for Autonomous Vehicles**
=====================================

This project focuses on solving the motion planning problem for autonomous vehicles. Motion planning is a critical component of the autonomous driving software stack, responsible for determining a safe and efficient path for the vehicle to follow.

**Key Concepts**
---------------

* **Motion Planning Problem**: A formal problem statement that involves finding a collision-free path for an autonomous vehicle from its current state to a desired goal.
* **Path Planning Problem**: A sub-problem of motion planning that involves finding a feasible path through a given environment, taking into account obstacles and road structure.
* **Velocity Profile Generation**: A process that determines the final speed at the end of a path and generates a velocity profile to achieve it.
* **Collision Detection**: A safety-critical task that guarantees a collision-free path by identifying potential collisions with obstacles in the environment.

**Practical Notes**
------------------

* To solve the motion planning problem, we subdivided it into two sub-problems: path planning and velocity generation.
* Parametric curves, such as Bezier curves and B-splines, are commonly used in autonomous driving for path planning due to their smoothness and flexibility.
* Discretizing the path is necessary to simplify the path planning problem, with a suitable discretization resolution depending on the specific application.

Note: This summary provides a concise overview of the key concepts and practical notes from the lesson transcript. It can be used as a starting point for creating a README file that documents the project's goals, technical requirements, and implementation details.

## Transcript

In this lesson, we focus on the motion planning problem in the context of autonomous vehicles and presented some of the techniques we can use to solve it. The lesson was divided in the context of four categories? Motion planning, overview, path planning, velocity profile generation, and collision detection. First, we went over an overview of motion planning by introducing the concept of motion planning and where it sits on the overall autonomous driving software stack, describing its formal problem statement and finally, we discuss how motion planning is usually solved by subdividing it into two sub-problems, the path planning problem and the velocity generation problem. Next, we went deeper into the path planning problem by discussing what parametric curves are and which ones are commonly used in the autonomous driving industry and why, what the main components of the path planning problems are and how to exploit a road structure to simplify the problem, what some methods are that we can use to solve the path planning problem, and why we need to discretize the path and what the discretization resolution should be.

Then we discussed the velocity profile generation by talking about what we need to know to calculate the final speed at the end of the path and explain how to generate linear and linear composition velocity profile. Lastly, we covered collision detection, where we identified collision detection as a safety critical task within the autonomous driving software stack. We discussed the challenges we encounter in real-time applications, such as self-driving cars and how to overcome them and presented some of the most common techniques used to guarantee a collision-free path.

## Additional Content

In this lesson we covered in four parts: 
## 1. Motion Planning Overview
 - Motion planning introduction
 - Discussing where motion planning sits within the context of the overall Autonomous Driving software stack.
 - Formalizing the motion planning problem
 - And finally, we’ll subdivide motion planning into two smaller problems:
 - Path Planning
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
