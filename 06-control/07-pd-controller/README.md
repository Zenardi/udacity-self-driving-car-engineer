# PD Controller

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=kVYy2kjZjhA)

## Summary

**PD-Control for Oscillating Car**

This README file provides a summary of the PD-control technique used to mitigate overshoot in an oscillating car.

### Key Concepts

* **PD-Control**: A control strategy that combines proportional (P) and derivative (D) terms to improve stability and reduce overshoot.
* **Proportional Gain (τp)**: A parameter that determines how much the steering angle is adjusted based on the crosstrack error.
* **Derivative Gain (τd)**: A parameter that determines how much the steering angle is adjusted based on the rate of change of the crosstrack error.
* **Crosstrack Error**: The difference between the car's current position and its target trajectory.
* **Temporal Derivative**: The rate of change of the crosstrack error over time.

### Practical Notes

To implement PD-control, you need to compute the derivative of the crosstrack error using the following formula:

```python
derivative = (crosstrack_error[t] - crosstrack_error[t-1]) / dt
```

where `dt` is the time step between measurements. In this example, we assume `dt = 1`, so the derivative can be computed as:

```python
derivative = crosstrack_error[t] - crosstrack_error[t-1]
```

The PD-control algorithm adjusts the steering angle based on both the proportional and derivative terms:

```python
steering_angle = tau_p * crosstrack_error + tau_d * derivative
```

To test the PD-control algorithm, you can use the following parameters:

* `param1` (proportional gain): 0.2
* `param2` (derivative gain): 3.0

Run the controller for 100 time steps and observe how it converges to zero.

## Transcript

The basic next question is is there a way to void the overshoot? It would be nice if we could do this, because driving in an oscillating car is no fun. In fact, it makes you really seasick, believe me. I've been in this car for months on end when we prepared for the Darpa Grand Challenge. The trick is called "PD-control." In PD-control my steering alpha is no just related to the crosstrack error by virtue by virtue of the gain parameter tau p, but also to the temporal derivative of the crosstrack error.

What this means is that when the car has turned enough to reduce the crosstrack error, it won't just go shooting for the x axis, but it will notice that it's already reducing the error. The error is becoming smaller over time. It counter steers. It steers up again. This will allow it to gracefully approach our target trajectory, assuming appropriate settings of our differential gain--tau d versus the proportional gain tau p.

How do you compute this derivative over here? Well, at time t this is the same as the crosstrack error at time t minus the crosstrack error at time t minus 1 divided by the time span between t and t minus 1. In our code, we assume delta t equals 1, so so we can omit this. The difference of the current crosscheck error and the previous one is this term over here. We now control not just in proportion to the error itself but also to this difference of the error using a second constant tau d.

Let's implement this. Now I give the run command two parameters--param1 and param2. I want you to implement a controller that varies the steering direction proportionally according to parameter 1, and differentially proportionally to parameter 2. Again, run for 100 time steps and see what happens. When I run my new controller with proportionality parameter of 0.2 and the differentiation one is 3.0.

Then, I get a sequence of y values that converge much more gently to 0. Miraculously, as time goes on, they really go down to 0 and stay at 0, which we didn't achieve for the proportional controller. Please write that routine so we can test it.
