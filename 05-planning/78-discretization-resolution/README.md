# Discretization Resolution

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=hh9BacjC5h4)

## Summary

**Path Planning Discretization**
=====================================

This project deals with the discretization of a continuous curve representing a spiral path in order to make it suitable for real-time collision detection, velocity profile generation, and motion control.

**Key Concepts**
---------------

* **Discretization**: The process of converting a continuous curve into a series of discrete points.
* **Collision Detection**: The ability to detect potential collisions between the vehicle and its environment.
* **Velocity Profile Generation**: The creation of a smooth and efficient velocity profile for the vehicle to follow.
* **Motion Control**: The control of the vehicle's motion, including acceleration, deceleration, and direction changes.
* **Arc Length**: A measure of the distance along a curve from one point to another.
* **Curvature Changes**: The rate at which the curve bends or turns.

**Practical Notes**
-------------------

When discretizing a continuous path, it is essential to find a balance between computational speed and accuracy. A too coarse discretization can lead to inaccurate collision detection and jerky motion control, while a too fine discretization can be computationally intensive and may not be suitable for real-time planning.

In practice, the resolution of discretization should be calculated dynamically based on the curve's arc length and curvature changes. However, in many cases, it is convenient to select a constant number of points to discretize the curve, especially when planning a constant distance ahead.

The following code snippet demonstrates how to calculate the arc length of a curve:

```python
import numpy as np

def calculate_arc_length(x, y):
    dx = np.diff(x)
    dy = np.diff(y)
    return np.sqrt(dx**2 + dy**2).cumsum()
```

This code calculates the arc length of a curve defined by two arrays `x` and `y`. The `np.diff()` function is used to compute the differences between consecutive points, and the `np.sqrt()` function is used to calculate the Euclidean distance. The `cumsum()` function is then used to accumulate these distances along the curve.

## Transcript

When we solve the path planning problem using numerical approximation or optimization, we end up with a spiral that represent a continuous curve for all infinite values of S from zero to S_f. For effectiveness while performing collision detection while generating a velocity profile, or even while sending commands to our motion controller, we must discretize this curve to make this tasks feasible. At this point, we know we must discretize the spiral curve we got, but now the big question is, how fine or coarse this discretization should be? Is it okay to make it too coarse so we leave gaps? What happens if we make it extremely fine?

Let's dig deeper into this and discuss the pros and cons. Let's start looking at the pros and cons for a too coarse discretization. The main advantage in this case is computational speed. We would have to perform collision checking, assign velocities and generate control commands for only a few points. On the other hand, the collision check accuracy deteriorates to the point where we might even miss a collision.

Also, we may not have enough points for the motion controller to be smooth, and the vehicle's motion could become jerky or undesirable. Let's move on to the pros and cons when discretization is too fine. The main two advantages is that our collision detection would be accurate and the motion controller would be smooth. The main disadvantage is that having to inspect so many points might make it computationally too intensive, and potentially not suitable for real-time planning. We must find a compromise between both, and in the next slide we'll address precisely that.

Really, how do we find a good discretization resolution? Ideally, this resolution should be calculated dynamically based on the curve arc length, and the curvature changes, basically adding more points when making tighter curves. In many cases, if we always plan a constant distance ahead, it's wise and convenient to select a constant number of points to discretize the curve. Let's check what we have learned in this section. We learn that we need to discretize a continuous path so it can be efficiently used for collision checking, velocity profile generation, and motion control.

We also discussed the pros and cons of too few, and too many points.

## Additional Content

## Importance of Discretization Resolution

Solving the Path Planning problem using numerical approximation or optimization, we obtain a spiral that represents a continuous curve for infinite values of $s$ , from 0 to $s_f$ :

** $\kappa(s) = a_3s^3 + a_2s^2 + a_1s + a_0$

** where all “a” parameters are now known.

We still need to discretize this continuous curve, so it can be feasibly and efficiently used for the following tasks:
- Collision Checking
- Velocity profile generation
- Motion control

## Pros and Cons: Should we make this discretization too coarse or too fine?
### Too coarse 

| Pros      | Cons |
| ----------- | ----------- |
| **Computationally fast**, because we would only need to perform collision checking, assign velocities and generate control commands for a few points.      | **Inaccurate collision check** - we might even miss a collision!        |
|        | **Jerky and undesirable vehicle motion** - there may not be enough points for the motion controller to be smooth.        |


### Too fine 

| Pros      | Cons    |
| ----------- | ----------- |
| **Accurate collision detection**       | **Computationally too intensive** - potentially not suitable for real-time planning.        |
| ** Smooth motion controller**         |                |


**Conclusion**: We must find a compromise between a "too coarse" and a "too fine" discretization resolution.

## Finding a Good Discretization Resolution

Ideally, this resolution should be calculated dynamically based on:
- Curve arc length $S_f$

- Curvature changes $\kappa'(s)$: Add more points when making tighter curves

**For simplicity and convenience, if we always plan a constant distance ahead, we can use a constant number of points to discretize the curve.
Pick enough points to account for tight curves.**
