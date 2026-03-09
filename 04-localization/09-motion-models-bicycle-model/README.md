# Motion Models: Bicycle Model

> Part of: **Introduction to Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=B2bXg8LaeF0)

## Summary

**Bicycle Model for Car Motion**
=====================================

The bicycle model is a simplified representation of how a car moves, based on several assumptions. This model is useful for understanding the motion of cars in 2D space.

### Key Concepts

* **Simplifying Assumptions**: The bicycle model ignores vertical dynamics and assumes the car only moves in 2D.
* **Rigid Beam**: The front wheels are connected to the back wheels by a rigid beam with fixed length, allowing them to be represented as one wheel each.
* **Bicycle-like Control**: The car is controlled like a bicycle, with a steering angle theta and longitudinal velocity in the direction of motion.
* **Motion Variables**: The car's motion can be described using variables such as steering angle (theta), longitudinal velocity, and yaw rate.

### Practical Notes

* To implement the bicycle model, you will need to:
	+ Represent the car's motion in 2D space
	+ Use a rigid beam with fixed length to connect the front and back wheels
	+ Control the car like a bicycle using steering angle and longitudinal velocity
* Example code for implementing the bicycle model is not provided in this lesson, but you can use the following Python snippet as a starting point:
```python
import math

# Define motion variables
theta = math.pi / 8  # Steering angle (radians)
v = 3.0  # Longitudinal velocity (m/s)

# Calculate new position using yaw rate and velocity
yaw_rate = v * math.sin(theta) / 2.0
new_position = [x + v * math.cos(theta), y + v * math.sin(theta)]
```
Note: This code snippet is a simplified example and may not be directly applicable to your specific use case. You will need to modify it to fit your needs.

## Transcript

<v English>The bicycle model is</v>
<v English>a simple and useful way</v> <v English>to represent how a car moves.</v> <v English>Like all models, it is</v>
<v English>based on several simplifying</v> <v English>assumptions.</v> <v English>First, we all ignore all</v>
<v English>vertical dynamics of the car,</v> <v English>so you can assume the</v>
<v English>car only moves in 2D.</v> <v English>This means no flying</v>
<v English>cars, unfortunately.</v> <v English>Next, we'll assume</v>
<v English>that, like a bicycle,</v> <v English>the front wheels of</v>
<v English>the car are connected</v> <v English>to the back wheels of the car by</v>
<v English>a rigid beam with fixed length.</v> <v English>Here, we assume that the</v>
<v English>front two wheels act together</v> <v English>so they can effectively be</v>
<v English>represented as one wheel,</v> <v English>just like a bicycle.</v> <v English>The same holds for</v>
<v English>the two rear wheels.</v> <v English>Finally, we assume the car is</v>
<v English>also controlled like a bicycle,</v> <v English>with a steering angle theta</v>
<v English>and some longitudinal velocity</v> <v English>in the direction that</v>
<v English>the car is heading.</v> <v English>For this car, we change</v>
<v English>the steering angle</v> <v English>by pi over 8 radians,</v>
<v English>and then the car</v> <v English>moves forward at a velocity</v>
<v English>of 3 meters per second.</v> <v English>You have just learned</v>
<v English>how the motion of a car</v> <v English>can be simplified down to</v>
<v English>something similar to a bicycle,</v> <v English>with a bicycle motion model.</v> <v English>Next, you'll get</v>
<v English>reminded how to use</v> <v English>the yaw rate and velocity of a</v>
<v English>car to find its new position.</v>
