# PID Implementation

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Ag8H3Iit9j4)

## Summary

**PID Controller Implementation**
=====================================

This project introduces the concept of PID (Proportional-Integral-Derivative) controllers, which are used to control the motion of robots by adjusting their steering based on error measurements.

### Key Concepts

* **Crosstrack Error**: The difference between a robot's actual position and its desired position.
* **Integral or Sum of Crosstrack Errors**: A measure of the total error accumulated over time, calculated as the sum of all crosstrack errors observed so far.
* **PID Controller**: A control algorithm that combines three terms:
	+ **Proportional (P) Term**: Adjusts steering based on current crosstrack error.
	+ **Differential (D) Term**: Adjusts steering based on rate of change of crosstrack error.
	+ **Integral (I) Term**: Adjusts steering based on sum of all crosstrack errors accumulated over time.
* **PID Formula**: The PID controller formula is given by: `steering = Kp * error + Kd * d(error)/dt + Ki * integral`

### Practical Notes

The instructor demonstrates how to implement a PID controller in code, using the following steps:

1. Calculate the crosstrack error and its differential.
2. Compute the integral of all crosstrack errors observed so far.
3. Combine the proportional, differential, and integral terms to calculate the final steering adjustment.
4. Use a parameter (in this case, 0.004) to adjust the weight given to each term.

Note that the instructor provides example code for implementing the PID controller, but does not explain why the specific values used are chosen.

## Transcript

<v English>What's the intuition?</v> <v English>If you drive a car and your normal steering mode leads you to a trajectory far away from the goal,</v> <v English>then what I submit you do is you notice over a long period of time you can't get closer.</v> <v English>So you start steering more and more the more time goes by to the right to compensate this bias.</v> <v English>As a result, when you drive you steer the car this way.</v> <v English>To do so, you need a sustained situation of large error.</v> <v English>That's measured by the integral or the sum of the crosstrack errors over time.</v> <v English>Let's make a new controller where steering is proportional to the crosstrack errors before.</v> <v English>It's equally proportional to the differential of the crosstrack error,</v> <v English>but now it's also proportional to what's called the integral or the sum</v> <v English>of all the crosstrack errors you ever observed.</v> <v English>This term is interesting. If we have a constant crosstrack error of, say, 0.8</v> <v English>and the sum will increase by 0.8 for each time unit, it'll become larger and larger and larger,</v> <v English>and eventually it'll correct the robot's motion.</v> <v English>This is called the PID controller.</v> <v English>This is the P or the proportional term, the D or the differential term, and the i for integral.</v> <v English>P-I-D.</v> <v English>Let's implement this, and the integrated crosstrack error</v> <v English>is the sum of all crosstrack errors you ever observed.</v> <v English>Let's implement this in our code.</v> <v English>I give you an integral factor of 0.004.</v> <v English>Let's not worry why I picked those. They're actually wisely chosen, as you will see in a minute.</v> <v English>But let's run our code and now modify our code to also allow for this parameter over here.</v>
