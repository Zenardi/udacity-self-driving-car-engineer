# Exercise: Simpson's Rule

> Part of: **Motion Planning**

## Additional Content

## Simpson's Rule
In this exercise we will calculate the value of the following integral:

$x(s) = x_o + \int_{0}^{s}cos(\Theta(s'))ds'$

NOTE: **x

0

will be 0 in this exercise.**

To do so and since this integral does NOT have a closed-form solution we will use Simpson's Rule.

The only 2 things you need are:
1. The definition of Theta(s) for a Cubic Spiral, which is:

$\Theta(s) = \Theta_0 + \frac{a_3s^4}{4} + \frac{a_2s^3}{3} + \frac{a_1s^2}{2} + a_0s$

NOTE: **θ

0

will be 0 in this exercise.**

2. Simpson's Rule equation:

$\int _{a}^{b} f(x)dx\approx \frac{\Delta x}{3}(f(x_0) + 4f(x_1) + 2f(x_2) + 4f(x_3) + 2f(x_4) + ...+ 4f(x_{n-1}) + f(x_n))$

#### Where:

$\Delta x=\frac{b-a}{n}$

$x_i = a + i\Delta x$

Follow the "TODO"s to complete this exercise.

#### In order to compile the code, you'll need to create a new terminal and use the command `g++ -o output quiz.cpp`
### Check it out!

[https://www.desmos.com/calculator/67uwfvv4xa](https://www.desmos.com/calculator/67uwfvv4xa)
