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

<v English>As we continue this lesson,</v> <v English>we'll be relying heavily on Frenet coordinates.</v> <v English>And as a reminder of how these work,</v> <v English>we can first look at the road in Cartesian coordinates,</v> <v English>where we imagine the road leaving on some rectangular X, Y grid.</v> <v English>And you can imagine that the more complex the road shape,</v> <v English>the harder our problem.</v> <v English>Think of how complicated both the X and Y behavior</v> <v English>would look like just to describe a car going along the lane.</v> <v English>If we were to compute that trajectory,</v> <v English>we would be pretty much be computing the shape of</v> <v English>the road whereas this information is already available.</v> <v English>So instead we use a Frenet coordinate system where the S coordinate depicts motion along</v> <v English>the road also called longitudinal motion</v> <v English>and the D coordinate gives side to side or lateral motion.</v> <v English>Before we move on, I want you to realize that</v> <v English>although we can simply take the center of a lane as a reference line,</v> <v English>we could also imagine using an actual nice and feasible trajectory</v> <v English>computed with enough land planning algorithm like A* or Hybrid A*.</v> <v English>And that trajectory would have been later smooth.</v> <v English>The benefit of this is that it would allow us to have</v> <v English>a nominal path that we know the vehicle should follow if possible,</v> <v English>like when the corresponding portion of the lane in front of us is empty.</v>
