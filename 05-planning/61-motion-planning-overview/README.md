# Motion Planning Overview

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=PuGF6EzuZJE)

## Summary

**Motion Planning Problem Statement**
=====================================

The motion planning problem is a crucial component of autonomous vehicle software architecture. It involves finding a trajectory from a starting position, heading, and curvature to an ending position, heading, and curvature that satisfies the vehicle's kinematic and curvature constraints.

**Key Concepts**
-----------------

* **Kinematic Constraints**: The vehicle's speed limits, comfortable lateral and longitudinal accelerations, and safety speed limitations due to road and weather conditions.
* **Curvature Constraints**: The minimum turning radius of the vehicle due to its steering mechanism.
* **Collision-Free Trajectory**: A trajectory that avoids collisions with other participants in the environment.
* **Path Planning**: Generating a feasible and efficient path from the starting state to the ending state while satisfying curvature constraints.
* **Velocity Profile Generation**: Creating a velocity profile for the generated path that satisfies kinematic constraints.

**Practical Notes**
-------------------

The lesson discusses two approaches to solving the motion planning problem:

1. **Direct Trajectory Generation**: This approach involves generating a sequence of positions and times where the vehicle needs to be, such as with the minimum jerk trajectory.
	* Pros: Closed-form solution, computationally fast, easy to implement.
	* Cons: Requires estimating time for execution in advance, does not guarantee curvature constraints, and is limited to single scenarios.
2. **Path Planning and Velocity Profile Generation**: This approach involves dividing the problem into two sub-problems: path planning and velocity profile generation.

The lesson concludes that the path planning and velocity profile generation approach is more suitable for autonomous vehicles due to its flexibility, adaptability, and ability to include multiple constraints in the problem formulation.

**Code Pattern**
-----------------

No specific code patterns or examples are provided in this lesson. However, it is mentioned that the motion planner must integrate predictions of other participants into its collision detection scheme.

## Transcript

Let's start with the motion planning problem statement. Given a starting position, heading and curvature, we wanted to find a trajectory to an ending position, heading and curvature that satisfies the vehicles kinematic and curvature constraints. For example, the vehicle itself has a minimum turning radius due to its steering mechanism. It's collision-free and satisfies comfort and safety kinematic constraints. There are a few ways you can solve this problem.

Let's take a look at it. We can solve the motion planning problem mainly in two ways, direct trajectory generation and path planning and velocity profile generation. With direct trajectory generation, we can generate a sequence of positions and times where the vehicle needs to be. A perfect example of this approach is the minimum jerk trajectory. The second way to solve the motion planning problem is to divide it into two sub-problems.

The path planning problem, which focuses on generating feasible and efficient path. The velocity profile generation problem, which focuses on grading a velocity profile for that path that guarantees comfort and other safety factors. A multitude of approaches exist for solving each one of these problems. In both cases, the trajectory generated must be collision-free, which means that we need to integrate our predictions of other participants into our collision detection scheme. Let's talk about now the pros and cons for each one of these two approaches.

For the first approach, we will address specifically the pros and cons of a minimum jerk trajectory generation technique. The pros are, this formulation has a closed form solution, it's computationally fast, it's very easy to implement, and involves one single-step to directly generate the trajectory. On the other side, the cons are, you need to estimate the time that it will take to execute the maneuver in advance, which is far from trivial. The curvature constraints are not included in the formulation and therefore are not guaranteed. This is a huge problem since you are not able to guarantee that the car can actually take that planned curve.

Finally, that you are stuck using single approach for all possible driving scenarios and conditions, which is totally undesirable. Let's now jump to discuss the pros and cons of splitting the problem into path planning and velocity profile generation. On one side, we see the process that this approach is flexible and adaptable, meaning that it allows for different path planning and velocity profile techniques to be used depending on the driving scene. This is definitely closer to real life. Also, that we can include multiple constraints into the problem formulation.

On the other side, we have the cons. Path planning approaches are computationally intensive because they require either numerical approximation, numerical optimization, or other iterative approaches. Finally, this is a two-step process which means that there's more work to do and more code to develop. For self-driving cars to be able to handle multiple driving scenarios and to guarantee that the plan paths are feasible, we must choose the path planning and velocity profile generation approach to solve the motion planning problem as a whole. In this subdivision, the planner will find the path from the starting state to the ending state, while it satisfies the vehicles curvature constrained.

Meaning that the path will be feasible. The velocity profile part of the problem will satisfy the kinematic constraints. The speed limits, comfortable lateral and longitudinal accelerations and safety speed limitations due to road and weather conditions. Let's summarize what we have discussed so far. The motion planner is the last layer of the hierarchical planner and a key major component on the overall autonomous vehicles software architecture.

It's in charge of generating the maneuver requested by the behavioral planner. The trajectory generated by the motion planner must be collision-free, safe, efficient, and comfortable. We presented two approaches to generate trajectories and discussed their pros and cons. Finally, we chose the path planning and velocity generation approach.

## Additional Content

### Motion Planning Problem Statement

It's important for us to understand what exactly we want the motion planner to do. This is what we call the motion planning problem statement. We define our problem statement as: Given a starting position, heading, and curvature, find a trajectory to an ending position, heading and curvature that satisfies the vehicle’s kinematic and curvature constraints, avoids collision, and satisfies both comfort and safety kinematic constraints. There's more than one way we can go about solving this problem which we'll get into below. 

### Motion Planning Problem Solution Approaches
One of the ways we can go about solving the motion planning problem is called Direct Trajectory Generation. Direct Trajectory Generation is when you're able to generate a sequence of both positions and times for where a vehicle needs to be. This would require only a single step. An example of Direct Trajectory Generation is called Minimum Jerk Trajectory.

The second approach is to use both path planning and velocity profile generation by dividing the problem into two subproblems. We can use path planning in order to find a path from the starting state to the ending state. We'd also use it to make sure it satisfies the vehicles’ curvature constraints. The velocity profile generation would be used to satisfy the all kinematic constraints such as vehicles’, comfort and safety. 


### Pros and Cons of First Approach: Direct Trajectory Generation
| Pros      | Cons |
| ----------- | ----------- |
| Closed-form solution| You need to estimate the time of the maneuver in advance|
| Computationally fast | Curvature constraints are not included in the formulation. (i.e NOT guaranteed.) |
| Easy to implement | Stuck with 1 single approach |
| One step - directly generates trajectory. |     _ |

### Pros and Cons of Second Approach: Splitting the problem into Path Planning + Velocity Profile generation

| Pros      | Cons |
| ----------- | ----------- |
| Flexibility and adaptability: Allows for multiple approaches depending on the driving scene (Real life!) | Computationally intensive: Requires Num Optimization, Num Approximation or Iterative approaches.|
| We can include multiple constraints into the formulation. | More work to do and more code to develop.|


### Recap 

The Motion Planner is the last layer of the Hierarchical Planner and is in charge of generating the maneuver requested by the behavior planner. The trajectory generated must be collision-free, safe, efficient, and comfortable. In order to resolve the motion planning problem statement, we presented two approaches: Direct Trajectory Generation and Path Planning + Velocity Generation. For this course, we're going to choose the second approach to address the motion planning problem statement.
