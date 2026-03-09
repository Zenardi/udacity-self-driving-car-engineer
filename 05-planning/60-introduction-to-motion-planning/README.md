# Introduction to Motion Planning

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=-UASDBtJelo)

## Summary

**Autonomous Vehicles Motion Planning**
=====================================

This README file provides a summary of the key concepts and practical notes from the Udacity lesson on autonomous vehicles motion planning.

### Key Concepts

* **Hierarchical Planning**: A planning approach that divides the entire task into sub-problems, each with its own level of abstraction.
* **Motion Planner**: Responsible for generating kinematically feasible, collision-free, and safe trajectories for an autonomous vehicle.
* **Trajectory vs. Path**:
	+ **Path**: The curve a vehicle describes in space, but not in time. It only indicates where the vehicle will go through, without considering speed or acceleration.
	+ **Trajectory**: The curve a vehicle describes in both space and time. It indicates when and where the vehicle will go through, taking into account speed and acceleration.

### Practical Notes

* To implement motion planning, you need to consider generating trajectories that are kinematically feasible (i.e., physically possible), collision-free, and safe.
* The motion planner should decide not only where the vehicle needs to move but also how fast it can move, considering factors like acceleration and deceleration profiles.

## Transcript

Here we can see where the planning module sits within the typical autonomous vehicles software architecture. The entire planning task is divided into sub-problems. This approach is called hierarchical planning. In hierarchical planning, each level can be described as its own optimization problem, having a specific degree of abstraction with respect to the full problem. In previous lessons, we discuss the route planner and the behavioral planner and their specific levels of abstraction and what tasks did they perform.

In this lesson, we will focus on our attention on the motion planner. The motion planner is responsible for generating kinematically feasible, collision-free, and safe trajectories. Before we continue, let's make sure we fully understand the term trajectory and how it differs from path. Path is the curve that the vehicle describes in space and only in space. That means that we can know where the vehicle will go through, but not when.

It can go fast or it can go slow. Or it can actually accelerate and decelerate following a profile. On the other hand, a trajectory is the curve that the vehicle describes in space and time. That means that we will know when and where the vehicle will go through. This is what we are interested in motion planning.

We want to decide where and how fast the car needs to move.

## Additional Content

Motion planning falls into the **Planning** phase of the Autonomous Driving software architecture stack. The stack is: 

1. Sensors
2. Perception
3. Prediction
4. **Planning**
5. Control  

Planning is divided into subsets, called subproblems. This includes subproblems such as route planning, and behavioral planning. For this course, we're going to focus on Motion Planning. The division of subproblems is referred to as **hierarchical planning.** Hierarchical planning is when each level can be described as its own optimization problem having a specific degree of abstraction with respect to the full problem. 

### What exactly is the Motion Planning? 

The Motion Planning is the part of the planning phase responsible for creating trajectories that satisfy the following criteria: 

1. Kinematically feasible
2. Collision-free
3. Safe

In order to create these trajectories, it's important for us to differentiate between a *path* and a *trajectory.*
## Main Difference

The key difference between a path and a trajectory is that a trajectory takes into consideration both space *and* time when it comes to the curve that the vehicle describes. It allows us to know both when and where the vehicle will go so we can decide how fast the car needs to move and where.
