# Outro

> Part of: **Vehicle Models**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=DqKw_m3Uxr0)

## Summary

**Model Predictive Control (MPC) Fundamentals**
=============================================

This summary covers the key concepts of Model Predictive Control, a fundamental technique in control systems. MPC relies on kinematic and dynamic vehicle models, along with actuator constraints, to optimize controller performance.

### Key Concepts
* **Kinematic and Dynamic Vehicle Models**: These models describe the future trajectory of a vehicle, taking into account its motion and behavior.
* **Actuator Constraints**: Limitations on the vehicle's actuators (e.g., speed, acceleration) that must be considered when developing an optimal controller.
* **Cost Function**: A mathematical representation of the errors to be minimized in MPC. It calculates the difference between the desired trajectory and the predicted trajectory based on the vehicle model.

### Practical Notes
To implement MPC, you will need to:

* Use a cost function that captures the errors you want to minimize
* Predict the future trajectory of the vehicle using the kinematic and dynamic models
* Define actuator constraints to ensure realistic control

Note: This summary focuses on the theoretical foundations of Model Predictive Control. Practical implementation details are not included, but will be covered in subsequent lessons.

## Transcript

<v English>Congratulations, you're now familiar with kinematic and dynamic vehicle models.</v> <v English>These models along with</v> <v English>the actuator constraints are the foundations of model predictive control.</v> <v English>What we've built so far is a model that describes the future trajectory of the vehicle.</v> <v English>In order to develop an optimal controller,</v> <v English>we need to define a cost function that captures the errors we want to minimize.</v> <v English>The cost function will require you to use</v> <v English>the model to predict where the vehicle will go into the future.</v> <v English>The cost is actually the difference between where you want the vehicle</v> <v English>to go and where you predict it will go based on that model.</v> <v English>That's what's it's called Model Predictive Control.</v>
