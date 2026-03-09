# State

> Part of: **Vehicle Models**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6vFczwAYjsU)

## Summary

**Vehicle State and Dynamics**

This README file provides a summary of key concepts related to modeling the state and dynamics of a vehicle. The goal is to understand how to track and predict the position, orientation, velocity, and other attributes of a moving vehicle over time.

### Key Concepts

* **State**: A set of variables that describe the current status of an object or system, including its position (x, y), orientation (cy), and velocity (v).
* **Position**: The location of an object in two-dimensional space, represented by x and y coordinates.
* **Orientation**: The direction or angle at which an object is facing, denoted as cy.
* **Velocity**: A measure of an object's speed and direction of motion, represented as v.
* **Dynamics**: The study of how the state of a system changes over time.

### Practical Notes

To apply these concepts in practice, you can use the following approach:

* Represent the vehicle's state using variables such as x, y, cy, and v.
* Use mathematical models or algorithms to predict how the state will evolve over time.
* Consider factors such as acceleration, friction, and external forces that may affect the vehicle's motion.

Note: This summary focuses on the theoretical aspects of modeling a vehicle's state and dynamics. For implementation details and code examples, please refer to the accompanying lesson materials.

## Transcript

<v English>Think about how to keep track of the state of a vehicle.</v> <v English>The vehicle is located at a position which we track with x and y.</v> <v English>If we're talking about a car,</v> <v English>then the vehicle also has an orientation which we'll denote with cy.</v> <v English>This is a good model of a stationary vehicle,</v> <v English>but what if our vehicle is in motion?</v> <v English>In that case, it will also have a velocity which we'll call</v> <v English>v. This captures the vehicle's state.</v> <v English>So the next task is to model how that state evolves through time.</v> <v English>If we know the current state of the vehicle,</v> <v English>can we tell where we'll be in the future?</v>
