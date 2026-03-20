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

The bicycle model is a simple and useful way to represent how a car moves. Like all models, it is based on several simplifying assumptions. First, we all ignore all vertical dynamics of the car, so you can assume the car only moves in 2D. This means no flying cars, unfortunately. Next, we'll assume that, like a bicycle, the front wheels of the car are connected to the back wheels of the car by a rigid beam with fixed length. Here, we assume that the front two wheels act together so they can effectively be represented as one wheel, just like a bicycle. The same holds for the two rear wheels. Finally, we assume the car is also controlled like a bicycle, with a steering angle theta and some longitudinal velocity in the direction that the car is heading. For this car, we change the steering angle by pi over 8 radians, and then the car moves forward at a velocity of 3 meters per second. You have just learned how the motion of a car can be simplified down to something similar to a bicycle, with a bicycle motion model. Next, you'll get reminded how to use the yaw rate and velocity of a car to find its new position.
