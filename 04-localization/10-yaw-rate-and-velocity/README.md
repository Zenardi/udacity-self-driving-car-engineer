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
x_f = x_0 + v \* cos(θ_0) \* dt
y_f = y_0 + v \* sin(θ_0) \* dt
θ_f = θ_0
```
These equations represent the final x and y positions, and yaw of the car, given its initial position, velocity (v), and time elapsed (dt).
* **Equations for Position Update with Non-Zero Yaw Rate**: When the yaw rate is not zero, the equations become more complex:
```math
x_f = x_0 + v \* cos(θ_0) \* dt - v \* sin(θ_0) \* θ˙ \* dt^2
y_f = y_0 + v \* sin(θ_0) \* dt + v \* cos(θ_0) \* θ˙ \* dt^2
θ_f = θ_0 + θ˙ \* dt
```
These equations take into account the change in the car's heading as it moves.

**Practical Notes**
-------------------

This lesson emphasizes the importance of considering different types of rotations, including yaw, pitch, and roll. Understanding these concepts is crucial for developing accurate sensor fusion algorithms that can accurately determine a vehicle's orientation and position.

## Transcript

<v English>To recap what you</v>
<v English>learned in sensor fusion,</v> <v English>a car's heading, or yaw</v>
<v English>angle, is its orientation.</v> <v English>Yaw is often measured from</v>
<v English>the x-axis in map coordinates</v> <v English>with counterclockwise</v>
<v English>angles being positive.</v> <v English>In this situation, the car's yaw</v>
<v English>is positive pi over 4 radians.</v> <v English>Assuming constant turn</v>
<v English>rate and velocity,</v> <v English>the equations to find the new</v>
<v English>position of the car, which</v> <v English>you derived previously</v>
<v English>in the fusion module,</v> <v English>are shown again here.</v> <v English>These set of equations are valid</v>
<v English>when the yaw rate, theta dot,</v> <v English>is equal to zero.</v> <v English>Here, x sub f, y sub</v>
<v English>f, and theta sub f,</v> <v English>represent the final x position,</v>
<v English>y position, and yaw of the car,</v> <v English>while x sub zero, y sub</v>
<v English>zero, and theta sub zero</v> <v English>represent the initial</v>
<v English>x position, y position,</v> <v English>and yaw of the car.</v> <v English>Finally, v is the</v>
<v English>velocity of the car,</v> <v English>and dt is the time elapsed.</v> <v English>If the yaw rate is not zero, you</v>
<v English>have these equations instead,</v> <v English>which you first saw</v>
<v English>in sensor fusion,</v> <v English>because you'll have to take into</v>
<v English>account the change in the car's</v> <v English>heading as it moves.</v> <v English>Next, I want you</v>
<v English>to think about some</v> <v English>of the other possible rotations</v>
<v English>of the vehicle besides the yaw.</v>
