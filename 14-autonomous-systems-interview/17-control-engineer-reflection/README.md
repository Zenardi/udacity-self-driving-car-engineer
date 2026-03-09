# Control Engineer Reflection

> Part of: **Autonomous Systems Interview Practice**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=D5ugiJVUSsw)

## Summary

**PID Controller Fundamentals**
=====================================

This summary covers the key concepts of PID (Proportional-Integral-Derivative) controllers, including their equation and practical implementation.

### Key Concepts
* **PID Equation**: The overall equation for a PID controller is used to calculate the output value based on the proportional, integral, and derivative components.
* **Proportional Component**: This component calculates the current error and multiplies it by a gain factor to determine its contribution to the output value.
* **Integral Component**: This component accumulates past errors over time and uses this sum to adjust the output value.
* **Derivative Component**: This component calculates the rate of change of the error over time and uses this rate to adjust the output value.

### Practical Notes
* When implementing a PID controller in code, it's essential to use type declarations (e.g., `float`) for variables and initialize them as needed (e.g., setting values to zero).
* Use semicolons to separate statements in your code.
* Consider using a programming language like C++ to implement the PID controller equation.

## Transcript

<v English>Halyon had a fairly good answer for his PID controller.</v> <v English>He went through each step of proportional,</v> <v English>integral, and derivative, and explained each of these well,</v> <v English>and how they relate to the overall PID controller equation,</v> <v English>which is what gets output for steering angle,</v> <v English>for instance, or for a robotic arm.</v> <v English>One of the things I would say that he could do better was the first time he went through.</v> <v English>He mainly did things in pseudocode.</v> <v English>I prompted him a little bit to say what would you do if this within C++,</v> <v English>and he did a good job to add</v> <v English>his type declarations like floats as well as initializing things to zero,</v> <v English>if they needed to be, and adding semicolons.</v> <v English>Other than that though, I thought he gave a great answer.</v>

## Additional Content

## Analyzing Technical Answers - **Control Engineer** Interview

It's time to play the role of the interviewer.

Try to "think like the employer." Make sure to compare your analysis with our analysis at the end!
I noted in the reflection that Haoyang used semi-colons, although in the previous video they actually were not present. Make sure if coding in C++ to include them!
