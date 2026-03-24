# Frenet Reminder

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=u3TYp-hDojk)

## Summary

**Frenet Coordinates and Lane Following**

This README file provides an overview of key concepts related to Frenet coordinates and their application in lane following. Frenet coordinates are a mathematical framework used to describe motion along a curved path, such as a road.

### Key Concepts

* **Cartesian Coordinates**: A rectangular X-Y grid system used to describe the position of objects in space.
* **Frenet Coordinate System**: A coordinate system that describes motion along a curved path using three coordinates: S (longitudinal), D (lateral), and N (normal).
* **Longitudinal Motion**: Motion along the road, represented by the S coordinate.
* **Lateral Motion**: Side-to-side motion, represented by the D coordinate.
* **A\***: A path planning algorithm used to compute a feasible trajectory for an object moving through a space.

### Practical Notes

When working with Frenet coordinates, consider using a nominal path that is computed using algorithms like A\* or Hybrid A\*. This can provide a smooth and feasible trajectory for the vehicle to follow. However, it's also possible to use the center of the lane as a reference line. Note that the choice of method will depend on the specific requirements of the application.

**Example Code**
```python
import numpy as np

# Define Frenet coordinates
S = 0  # Longitudinal motion
D = 1  # Lateral motion
N = 2  # Normal motion

# Compute trajectory using A\*
trajectory = compute_trajectory(S, D, N)
```
Note: The example code is a placeholder and not actual implementation.

## Transcript

As we continue this lesson, we'll be relying heavily on Frenet coordinates. And as a reminder of how these work, we can first look at the road in Cartesian coordinates, where we imagine the road leaving on some rectangular X, Y grid. And you can imagine that the more complex the road shape, the harder our problem. Think of how complicated both the X and Y behavior would look like just to describe a car going along the lane. If we were to compute that trajectory, we would be pretty much be computing the shape of the road whereas this information is already available. So instead we use a Frenet coordinate system where the S coordinate depicts motion along the road also called longitudinal motion and the D coordinate gives side to side or lateral motion. Before we move on, I want you to realize that although we can simply take the center of a lane as a reference line, we could also imagine using an actual nice and feasible trajectory computed with enough land planning algorithm like A* or Hybrid A*. And that trajectory would have been later smooth. The benefit of this is that it would allow us to have a nominal path that we know the vehicle should follow if possible, like when the corresponding portion of the lane in front of us is empty.