# Systematic Bias

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=1wxFEcqq3_c)

## Summary

**Systematic Bias in Robotics**
=====================================

A systematic bias is a problem that can occur in robotics when there is an unintended and consistent deviation from the desired behavior. This can be caused by errors in calibration or alignment of sensors and actuators.

**Key Concepts**
---------------

* **Systematic bias**: A consistent error in the system's behavior, often due to incorrect calibration or alignment.
* **Proportional controller**: A control algorithm that adjusts the output based on the difference between the desired and actual values.
* **Steering drift**: The tendency of the vehicle to deviate from its intended course over time.
* **Crosstrack error**: The difference between the vehicle's actual position and its desired position.

**Practical Notes**
-------------------

To demonstrate the effect of systematic bias, you can modify your proportional controller by introducing a steering drift. This is done by setting the `steering_drift` command to a non-zero value (in this case, 10 degrees). You should then run the controller with a parameter value of 0.2 and observe how it affects the vehicle's behavior.

Note: The exact implementation details may vary depending on your specific robotics system and programming environment.

## Transcript

<v English>Let's talk about a problem that often occurs in robotics called a "systematic bias."</v> <v English>It goes as follows.</v> <v English>When you ordered your car, you believed the front wheels were 100% aligned,</v> <v English>but your mechanic made a mistake, and he aligned the wheels a little bit at an angle.</v> <v English>Now, for people that isn't a big concern. When we notice this we just steer a little bit stronger.</v> <v English>But let's try this out with out our proportional controller.</v> <v English>I'm now adding a line that sets the steering drift to be 10 degrees,</v> <v English>which in radians is this expression over here, using set&lt;u&gt;steering&lt;/u&gt;drift command.</v> <v English>I now want you to run my proportional controller with parameter 0.2,</v> <v English>and for now we're going to set the differential controller to zero.</v> <v English>When you do this, what happens?</v> <v English>It works just as before or it causes a new, big crosstrack error?</v> <v English>Go try it out.</v>
