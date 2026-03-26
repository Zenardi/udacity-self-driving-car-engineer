# Control Engineer

> Part of: **Autonomous Systems Interview Practice**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6Wi9HBIXcpg)

## Summary

**PID Control: A Key Component in Industry**

This project covers the basics of PID control, a widely used controller in industry. The goal is to understand how to implement a PID controller and its limitations.

### Key Concepts

* **PID Controller**: A type of controller that uses three variables:
	+ **Proportional (P)**: Responds to the current error
	+ **Integral (I)**: Accumulates past errors to adjust the control output
	+ **Derivative (D)**: Anticipates future errors by analyzing the rate of change
* **PID Formula**: The control value is calculated using the error and PID variables:
```math
u(t) = kp \* e(t) + ki \* e_i(t) + kd \* (e(t) - e_prev(t))
```
* **Variables**:
	+ `kp`: Proportional gain
	+ `ki`: Integral gain
	+ `kd`: Derivative gain
	+ `e(t)`: Current error
	+ `e_i(t)`: Accumulated integral error
	+ `e_prev(t)`: Previous error

### Practical Notes

* **Initialization**: In a C++ implementation, variables should be initialized with default values:
```c
float kp = 0.0;
float ki = 0.0;
float kd = 0.0;
float e_i = 0.0; // initial integral error
float e_prev = 0.0; // initial previous error
```
* **Types**: Floats are commonly used for errors and control variables.
* **Limitations**: PID controllers may not perform well in non-linear systems or simple systems where a proportional controller is sufficient.

Note: This summary focuses on the key concepts and practical notes from the lesson transcript. It does not include all details, but provides a concise overview of the main ideas.

## Transcript

Well, it's great to have you out here today, Harry Young. I'm really excited to interview you for our control engineer position. What I'd like to start off with is just a question in controls actually. Are you ready? Yeah, sure. Okay, great. So, my first question for you is just to explain the different components of PID control. Okay, sure. So, PID controller: the P stands for Proportional, I for integral and D for derivative and those controllers is one of the most used controller in industry. Yeah, great. So, if you are going to code a PID controller, how would you do it? Okay, sure.

Let me just go ahead and write those on the whiteboard. Great. So, as we just discussed, PID we need the three controller variables, the first one would be the kp for proportional and ki for integral and the kd for derivative. Essentially, what you're going to receive is our error, the value of our current error. We are trying to gain a control output. I have it here. So, all control loop, essentially we are calculate the control value using the error in our PID variables. Because we are using integral and derivative of parameters, so we need also two other variables to calculate those states. There's first of all I will say is the error of integral and also to calculate derivative we need the previous error, our codes error underscore free. So in a control loop, basically we are going to first, let's do an update of our integral error. So, that will be errors underscore i plus equal to our error in this loop and then we're going to go ahead and calculate the value here. So that will be four equals to first, the proportional one, our kp times our error, then our integral as it was already updated here. So, I'll go ahead and use it directly. Error underscore i and the last one would be the derivative, so kd times the derivative of which essentially is our current error minus our previous error. One of the things to know is that after this loop, we kind of need to update our previous error here. So, our current error become our previous error in the next loop. So, that's our error here and that will be my control loop of a PID controller. Okay, great. So, in going through this, if you're going to do it, say, in C plus plus, how do you think you might need to initialize variables including some of the types that you might use? Yeah. So, I'll say that would really depends on what our error and control variable is. But suppose we will be using mostly float for error and come full output variable and since they're essentially the same, we'll also have float here as our error. Since the initial state, our integral error should be zero since there's no error before and also our previous error should be ideally zeros to calculate the derivative later. Okay, great. So, if you have a PID controller in there, it does seem like it works in a lot of situations, are there any situations you can think of where it wouldn't work so well? Yeah, I guess PID is most widely used controller. One thing I will say about some case that PID is not appropriate, maybe for like non-linear systems since our control output may not be able to influence the system's output in a linear fashion. So, the PID controller will be struggling with different areas of that control output. Also, another aspect I will say it will be our simple system. You probably don't even need to use a full PID controller, sometimes maybe a proportional controller is fine. Great, okay. That's everything I had for this area anyway, we can move on to next topic now. Cool. All right.
