# Intro

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=N-SvuA8Jf5A)

## Summary

**Control Theory and PID Controllers**
=====================================

This project focuses on control theory, which is crucial for autonomous vehicles. Control involves using steering, throttle, and brakes to navigate a vehicle through its environment.

### Key Concepts

* **Control Theory**: The study of how to use feedback to adjust the behavior of a system.
* **PID Controller**: A fundamental controller that uses proportional, integral, and derivative terms to minimize error.
* **Proportional Term**: Adjusts control output based on current error value.
* **Integral Term**: Adjusts control output based on accumulation of past errors.
* **Derivative Term**: Adjusts control output based on rate of change of error.

### Practical Notes

To implement a PID controller, you will:
1. Learn how to implement a PID controller in Python using the following code pattern:

```python
class PIDController:
    def __init__(self, kp, ki, kd):
        self.kp = kp
        self.ki = ki
        self.kd = kd
        self.error_prev = 0
        self.integral = 0

    def update(self, error):
        p_term = self.kp * error
        i_term = self.ki * self.integral
        d_term = self.kd * (error - self.error_prev)
        self.integral += error
        self.error_prev = error
        return p_term + i_term + d_term
```

2. Implement a PID controller in C++ using the Udacity simulator.

Note: This is just an example of how to implement a PID controller, and you may need to adjust it based on your specific requirements.

## Transcript

<v English>Welcome to Control.</v> <v English>Control is how we use the steering,</v> <v English>throttle, and breaks to move a car where we want it to go.</v> <v English>Our friend, Andrew Gray from Uber Advanced Technology Group,</v> <v English>wrote his PhD dissertation on control theory.</v> <v English>Control's a trickier problem than it might seem.</v> <v English>When human turns through an intersection,</v> <v English>we use our intuition and experience to determine how hard to steer,</v> <v English>and when to accelerate,</v> <v English>and whether we ever need to step on the brakes.</v> <v English>Teaching a computer how to do this is hard.</v> <v English>Control algorithms are often called controllers,</v> <v English>and one of the most common and fundamental controllers is the PID controller.</v> <v English>In this lesson, you'll learn from Sebastian how to implement a PID controller in Python.</v> <v English>Then, you'll dive into the Udacity simulator to implement a PID controller in C++.</v>
