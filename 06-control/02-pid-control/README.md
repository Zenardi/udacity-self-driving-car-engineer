# PID Control

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=-8w0prceask)

## Summary

**PID Control Basics**
=======================

This lesson introduces the fundamental concepts of PID (Proportional-Integral-Derivative) control, a crucial aspect of control systems. You'll learn how to apply basic PID principles to control a vehicle's steering angle.

**Key Concepts**
---------------

* **Control Systems**: A system that regulates and adjusts its behavior based on feedback from its environment.
* **PID Control**: A type of control algorithm that combines three components:
	+ **Proportional (P)**: Adjusts the output in proportion to the error between the desired and actual states.
	+ **Integral (I)**: Compensates for steady-state errors by adjusting the output based on the accumulation of past errors.
	+ **Derivative (D)**: Predicts future errors by analyzing the rate of change of the error.
* **Crosstrack Error (CTE)**: The lateral distance between a vehicle and its reference trajectory.

**Practical Notes**
------------------

To apply PID control in practice, you'll need to implement an algorithm that adjusts the steering angle based on the CTE. This can be achieved by using a simple proportional controller, which sets the steering angle in proportion to the CTE. The formula for this is:

`steering_angle = Kp * cte`

where `Kp` is a gain factor that determines the sensitivity of the controller.

Note: This lesson only covers the basics of PID control and does not delve into more advanced topics such as tuning and optimization.

## Transcript

Let's now talk about the second part of this lesson called PID control. PID control is a vast field in control, and many, many classes can be taught about this one subject matter. What I'll do is I'll give you the very basics, and I'll let you implement the very basics. I promise it'll be fun. You'll be able to drive a car around, and the Google car to the present day uses a version of this exact same controller that is, of course, much more tuned the specifics of our car.

But you get to see some of the essence of what it means to control a car. Here is the problem. Consider the following car with a steerable front axle and 2 non-steerable wheels in the back. Say we wished this car to drive along this line, which is the output of our smoother we just discussed. Let's assume the car has a fixed forward velocity, but you have the ability to set the steering angle of the car.

How would you do this? You would keep the steering constant? You would use random steering commands? Or you could set the steering angle in proportion to what's known as the "crosstrack error," which is the lateral distance between the vehicle and the so-called reference trajectory. The third possibility is steer in proportion to the this crosstrack error or CTE.

Choose one of those that you think is best suited to control the car.
