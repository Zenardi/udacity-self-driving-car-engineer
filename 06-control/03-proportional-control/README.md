# Proportional Control

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=gGo-gSFqYqg)

## Summary

**P-Controller Overview**
=========================

A P-controller is a type of control algorithm that uses proportionality to adjust its output based on an input value. In this context, it's used for steering a car in relation to its crosstrack error.

**Key Concepts**
----------------

* **Proportional Control**: A control strategy where the output is directly proportional to the input.
* **P-Controller**: A specific type of proportional controller that uses a gain factor (tau) to adjust its output based on the crosstrack error.
* **Crosstrack Error**: The difference between the car's current position and its desired reference trajectory.

**Practical Notes**
------------------

While implementing a P-controller, it's essential to consider the trade-offs between overshooting and not quite reaching the reference trajectory. A well-tuned gain factor (tau) is crucial in achieving stable control. This lesson highlights the importance of intuitive understanding of control algorithms and their practical applications in real-world scenarios.

## Transcript

What you just learned is called a "P-controller" where P stands for proportional. Here is a really trick question by which I want to test your intuition-- one that doesn't have a unique answer, but it has a best answer. Suppose you do what I just said. You steer in proportion to the crosstrack error. That is, your steering angle is proportional by some factor of tau to the crosstrack error.

What will happen with the car? It never quite reaches the reference trajectory? It overshoots? Or either can happen?
