# The Motion Planning Problem

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=daGIOru4Bi4)

## Summary

**Motion Planning Problem Definition**
=====================================

This README file provides a summary of the key concepts and ideas introduced in the first lesson on motion planning algorithms. It covers the formal definition of the motion planning problem, including the concept of configuration space.

**Key Concepts**
---------------

* **Configuration Space**: The set of all possible configurations of a robot in a given world.
	+ Can be 2D or 3D depending on the number of dimensions required to describe the robot's position and orientation.
* **Motion Planning Problem**: A problem that involves finding a sequence of feasible movements in the configuration space that moves the robot from an initial configuration to a goal configuration without hitting any obstacles.
* **Initial Configuration**: The current state of the robot, including its location, speed, acceleration, etc.
* **Goal Configuration**: The desired end state of the robot, including its final location and orientation.
* **Constraints**: Rules that describe how the vehicle is allowed to move, including its dynamics and the description of the environment.

**Practical Notes**
-------------------

The motion planning problem can be solved using various algorithms, such as best planning algorithms. These algorithms take into account the configuration space, initial configuration, goal configuration, and constraints to find a feasible sequence of movements that achieves the desired outcome.

Example code for implementing a motion planning algorithm might look like this:
```python
import numpy as np

def motion_planning(config_space, start_config, goal_config, constraints):
    # Define the motion planning problem
    problem = {
        'config_space': config_space,
        'start_config': start_config,
        'goal_config': goal_config,
        'constraints': constraints
    }

    # Solve the motion planning problem using a best planning algorithm
    solution = solve_motion_planning_problem(problem)

    return solution
```
Note that this is just an example and actual implementation details may vary depending on the specific requirements of the project.

## Transcript

In the first lesson, you saw some best planning algorithms, which solve the motion planning problem. But we never formally defined that problem. I'd like to do that now. Now, there is a word that you might encounter quite a bit if you start reading material regarding motion planning algorithm. That word is "configuration space," which defines all the possible configurations of a robot in the given world. Consider the maze word you saw in the first lesson where these words were all 2D grids, the robot configuration was sometimes two dimensional when we presented it as an x_y point, and sometimes three dimensional when also including the robot's heading. In fact, the configuration space for vehicle that can become even larger depending on what motion planning algorithms we decide to use. With this idea of configuration space in mind, we can define a motion planning problem as follows. We're given three things. An initial configuration, a goal configuration and also some constraints describing how the vehicle was allowed to move, its dynamics and the description of the environment. Here, it is important to understand how this connects to the other decision-making modules that you have recently learned about. Usually, the start configuration is the current configuration of the car given to us by the localization value and the sensors that give us information about car location, speed, acceleration they can go, etcetera. The behavior layer gives us a desired end configuration, and maybe some constraints regarding where to go and at which speed. Finally, the prediction completes this problem by giving us information about how the obstacle region will evolve in time. This way, the sequence of actions that we generate takes into account other vehicles and pedestrian actions. And if we're working with a more sophisticated prediction module, how our actions might influence them. The motion planning problem can then be defined as final sequence of feasible movements in the configuration space that's moved the robot from a start configuration to an end configuration without hitting any obstacles. Now, I'm going to ask you to think about configuration spaces in the following questions.