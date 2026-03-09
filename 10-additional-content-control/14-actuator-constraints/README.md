# Actuator Constraints

> Part of: **Vehicle Models**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=EwcDwdM1msg)

## Summary

**Vehicle Dynamics Modeling with Actuator Constraints**
======================================================

This project focuses on modeling the dynamics of a vehicle while considering actuator constraints. These constraints are based on the fundamental physics of the vehicle's design and limit its movement in certain directions.

**Key Concepts**
----------------

* **Nonholonomic model**: A type of model that describes systems with limited movement due to constraints, such as steering angle limitations.
* **Actuator constraints**: Limits imposed by the vehicle's design on its actuators (e.g., steering angle, acceleration).
* **Lower and upper bounds**: Setting limits for actuator inputs to mimic real-world vehicle behavior.

**Practical Notes**
-------------------

To implement this model in practice:

* Set lower and upper bounds for each actuator input based on the actual vehicle's capabilities.
* For example:
```python
steering_angle_bounds = (-30, 30)  # degrees
acceleration_bounds = (-1, 1)
```
Note that these values should be determined experimentally or through consultation with a vehicle expert to ensure accuracy. By incorporating actuator constraints into the model, you can create a more realistic simulation of real-world vehicle behavior.

## Transcript

<v English>Great. You now know how to model the dynamics for a vehicle.</v> <v English>One last thing before we move on, actuator constraints.</v> <v English>In a real vehicle, actuators are limited by</v> <v English>the design of the vehicle in fundamental physics.</v> <v English>For example, a vehicle can't have a steering angle of 90 degrees. It's impossible.</v> <v English>Thus, it doesn't make sense for us to even consider these kinds of inputs.</v> <v English>There's actually a vocabulary for describing this constraint.</v> <v English>We call this model nonholonomic,</v> <v English>because the vehicle can't move in arbitrary directions.</v> <v English>It's limited by its steering angle constraints.</v> <v English>We can solve this by setting lower and upper bounds for the actuators.</v> <v English>For example, we may set the steering angle to be between minus 30 and 30 degrees,</v> <v English>and the acceleration to be between minus one and one.</v> <v English>Minus one signifying full brake,</v> <v English>and one signifying full acceleration.</v> <v English>In practice, the upper and lower bounds</v> <v English>should mimic the actual vehicle as closely as possible.</v>
