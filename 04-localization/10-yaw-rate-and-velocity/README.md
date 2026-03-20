# Yaw Rate and Velocity

> Part of: **Introduction to Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=tS7BYlCo3nU)

## Summary

**Sensor Fusion and Vehicle Orientation**
=====================================

This project focuses on understanding sensor fusion and its application in determining a car's orientation, particularly its heading or yaw angle. The key concepts covered include:

* **Yaw Angle**: A car's orientation is represented by its yaw angle, which is measured from the x-axis in map coordinates with counterclockwise angles being positive.
* **Equations for Position Update**: When the yaw rate (θ˙) is zero, the equations to find the new position of the car are:
```math
x_f = x_0 + v \cos(\theta_0)\, dt
y_f = y_0 + v \sin(\theta_0)\, dt
	heta_f = \theta_0
```
These equations represent the final x and y positions, and yaw of the car, given its initial position, velocity (v), and time elapsed (dt).
* **Equations for Position Update with Non-Zero Yaw Rate**: When the yaw rate is not zero, the equations become more complex:
```math
x_f = x_0 + v \cos(\theta_0)\, dt - v \sin(\theta_0)\, \dot{\theta}\, dt^2
y_f = y_0 + v \sin(\theta_0)\, dt + v \cos(\theta_0)\, \dot{\theta}\, dt^2
	heta_f = \theta_0 + \dot{\theta}\, dt
```
These equations take into account the change in the car's heading as it moves.

**Practical Notes**
-------------------

This lesson emphasizes the importance of considering different types of rotations, including yaw, pitch, and roll. Understanding these concepts is crucial for developing accurate sensor fusion algorithms that can accurately determine a vehicle's orientation and position.

## Transcript

To recap what you learned in sensor fusion, a car's heading, or yaw angle, is its orientation. Yaw is often measured from the x-axis in map coordinates with counterclockwise angles being positive. In this situation, the car's yaw is positive pi over 4 radians. Assuming constant turn rate and velocity, the equations to find the new position of the car, which you derived previously in the fusion module, are shown again here. These set of equations are valid when the yaw rate, theta dot, is equal to zero. Here, x sub f, y sub f, and theta sub f, represent the final x position, y position, and yaw of the car, while x sub zero, y sub zero, and theta sub zero represent the initial x position, y position, and yaw of the car. Finally, v is the velocity of the car, and dt is the time elapsed. If the yaw rate is not zero, you have these equations instead, which you first saw in sensor fusion, because you'll have to take into account the change in the car's heading as it moves. Next, I want you to think about some of the other possible rotations of the vehicle besides the yaw.
