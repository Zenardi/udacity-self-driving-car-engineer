# Constraints: Curvature

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Rt7F23Ax48A)

## Summary

**Curvature Constrained Path Planning**
=====================================

This summary covers the key concepts and practical notes related to applying curvature constraints to path planning, specifically for vehicle navigation.

### Key Concepts

* **Curvature constraint**: A minimum turning radius that a vehicle must adhere to due to its mechanical design.
* **Discrete sampling**: Representing a continuous curve with a finite number of points (samples) to simplify the problem.
* **Guaranteed satisfaction**: Applying constraints to only a few key points on the curve, ensuring that the curvature constraint is met everywhere.
* **Cubic spiral**: A type of curve that allows for efficient application of curvature constraints.

### Practical Notes

When applying curvature constraints to path planning, it's essential to balance between constraint accuracy and problem complexity. While fewer constraints make the problem easier to solve, they may lead to deviations from the desired continuous curve.

A common approach is to apply two constraints at one-third and two-thirds of the way along the curve, respectively. This allows for a good trade-off between constraint accuracy and computational efficiency.

## Transcript

From previous sections, we learned that the vehicle inherently from its mechanical design, has a minimum turning radius that constitute a curvature constraint. It is obvious that we want to apply this curvature constrained to the path so it's drivable by the vehicle. Ideally, we should apply this constraint to every single point on the curve. But it's not possible to apply infinite constraints. Luckily, due to the characteristics of the cubic spiral, we can apply this constraint to a few points only and still have guarantees that it will be satisfied in all points.

The fewer constraints, the easier the problem is to solve, but the more likely it is that our discrete sample will deviate from the continuous curve we are trying to represent. It's very common across literature to use two constraints at one third and two-thirds of the way respectively.

## Additional Content

### Constraints: Curvature


A **curvature constraint** is the *minimum turning radius* of a vehicle. This constraint comes inherently from the vehicle's mechanical design. In order for the path to be drivable, we need to apply this curvature constraint to the path.

It is not feasible to apply this constraint to every single point on the curve. However, fortunately, due to the characteristics of the cubic spiral, we can apply this constraint to only a few points on the curve and know that the constraint will be satisfied at all points.

There is a trade-off between the number of constraints and the ease of solving the problem: The fewer constraints, the easier it is to solve the problem, but it is also more likely that our discrete sample will deviate from the continuous curve we are trying to represent. Therefore, it’s common across literature to use 2 constraints, at *1/3rd* and *2/3rd* of the way respectively.
