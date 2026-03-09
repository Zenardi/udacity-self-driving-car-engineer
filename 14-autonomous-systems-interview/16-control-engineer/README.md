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

<v English>Well, it's great to have you out here today, Harry Young.</v> <v English>I'm really excited to interview you for our control engineer position.</v> <v English>What I'd like to start off with is just a question in controls actually. Are you ready?</v> <v English>Yeah, sure.</v> <v English>Okay, great. So, my first question for you is just</v> <v English>to explain the different components of PID control.</v> <v English>Okay, sure. So, PID controller: the P stands for Proportional,</v> <v English>I for integral and D for derivative and</v> <v English>those controllers is one of the most used controller in industry.</v> <v English>Yeah, great. So, if you are going to code a PID controller, how would you do it?</v> <v English>Okay, sure.

Let me just go ahead and write those on the whiteboard.</v> <v English>Great.</v> <v English>So, as we just discussed,</v> <v English>PID we need the three controller variables,</v> <v English>the first one would be the kp for proportional</v> <v English>and ki for integral and the kd for derivative.</v> <v English>Essentially, what you're going to receive is our error,</v> <v English>the value of our current error.</v> <v English>We are trying to gain a control output.</v> <v English>I have it here.</v> <v English>So, all control loop,</v> <v English>essentially we are calculate the control value using the error in our PID variables.</v> <v English>Because we are using integral and derivative of parameters,</v> <v English>so we need also two other variables to calculate those states.</v> <v English>There's first of all I will say is the error of</v> <v English>integral and also to calculate derivative we need the previous error,</v> <v English>our codes error underscore free.</v> <v English>So in a control loop,</v> <v English>basically we are going to first,</v> <v English>let's do an update of our integral error.</v> <v English>So, that will be errors underscore i plus equal to</v> <v English>our error in this loop and then we're going to go ahead and calculate the value here.</v> <v English>So that will be four equals to first, the proportional one,</v> <v English>our kp times our error,</v> <v English>then our integral as it was already updated here.</v> <v English>So, I'll go ahead and use it directly.</v> <v English>Error underscore i and the last one would be the derivative,</v> <v English>so kd times the derivative of which</v> <v English>essentially is our current error minus our previous error.</v> <v English>One of the things to know is that after this loop,</v> <v English>we kind of need to update our previous error here.</v> <v English>So, our current error become our previous error in the next loop.</v> <v English>So, that's our error here and that will be my control loop of a PID controller.</v> <v English>Okay, great.</v> <v English>So, in going through this,</v> <v English>if you're going to do it, say,</v> <v English>in C plus plus,</v> <v English>how do you think you might need to initialize</v> <v English>variables including some of the types that you might use?</v> <v English>Yeah. So, I'll say that would really depends on what our error and control variable is.</v> <v English>But suppose we will be using mostly float for</v> <v English>error and come full output variable and since they're essentially the same,</v> <v English>we'll also have float here as our error.</v> <v English>Since the initial state,</v> <v English>our integral error should be zero since there's no error before and also</v> <v English>our previous error should be ideally zeros to calculate the derivative later.</v> <v English>Okay, great.</v> <v English>So, if you have a PID controller in there,</v> <v English>it does seem like it works in a lot of situations,</v> <v English>are there any situations you can think of where it wouldn't work so well?</v> <v English>Yeah, I guess PID is most widely used controller.</v> <v English>One thing I will say about some case that PID is not appropriate,</v> <v English>maybe for like non-linear systems since</v> <v English>our control output may not be able to influence the system's output in a linear fashion.</v> <v English>So, the PID controller will be struggling with different areas of that control output.</v> <v English>Also, another aspect I will say it will be our simple system.</v> <v English>You probably don't even need to use a full PID controller,</v> <v English>sometimes maybe a proportional controller is fine.</v> <v English>Great, okay. That's everything I had for this area anyway,</v> <v English>we can move on to next topic now.</v> <v English>Cool.</v> <v English>All right.</v>
