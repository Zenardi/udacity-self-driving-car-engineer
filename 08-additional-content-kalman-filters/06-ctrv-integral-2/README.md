# CTRV Integral 2

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=9E6K4Aw_MaI)

## Summary

**Solving Integrals with Assumptions**
=====================================

This README file summarizes the key concepts and practical steps introduced in a Udacity lesson on solving integrals.

### Key Concepts
* **Constant Velocity**: Assuming that velocity `v` is constant, allowing us to move it outside of the integral.
* **Expressing Sine as a Function of T**: Using the assumption of a constant yard rate, expressing `sin` as a function of time `T`.
* **Solving Integrals with Constants**: When all variables are constants except for one, integrals can be solved using basic integration rules.

### Practical Notes
* To solve the first two rows of the integral, follow these steps:
	1. Move the constant velocity `v` outside of the integral.
	2. Express `sin` as a function of time `T` using the assumption of a constant yard rate.
	3. Solve the resulting integrals using basic integration rules or consult online tools/textbooks for assistance.

Note: This is considered an advanced topic, and solving these integrals on the fly may require additional practice and review.

## Transcript

<v English>So, you already solved the last</v>
<v English>three rows, that's great.</v> <v English>For the first two rows,</v>
<v English>we actually have to solve the integral.</v> <v English>There is no way around this time.</v> <v English>First, let's insert the assumption</v>
<v English>that the velocity v is a constant.</v> <v English>So we can move the velocity at time</v>
<v English>K as a constant before the integral.</v> <v English>Also, we can explicitly express sin</v>
<v English>as a function of T using again,</v> <v English>the assumption of a constant yar rate.</v> <v English>After the video,</v>
<v English>take a moment to look at this term and</v> <v English>try to figure out what's going on here?</v> <v English>For the first two rows we now</v>
<v English>have an explicit function of t.</v> <v English>All other variables are constants.</v> <v English>So now it is possible to</v>
<v English>solve these integrals.</v> <v English>You can look up the solution of</v>
<v English>these integrals in a text book or</v> <v English>you can solve them with an online tool.</v> <v English>You will find a link below the video.</v> <v English>Consider this a bonus question for</v> <v English>those who are really good</v>
<v English>in solving Integrals.</v> <v English>I don't really expect you to</v>
<v English>solve this Integral on the fly.</v> <v English>Unless of course you think you can.</v>

## Additional Content

The general form of the solved integral can be found

[here](http://www.wolframalpha.com/input/?i=v+int+cos(a+%2B+b+*+(t+-+c+))+dt,++t+%3D+c+to+d)

.
### Question 1:

$v_k \int_{t_k}^{t_{k+1}} cos(\psi_k + \dot{\psi_k} \cdot (t - t_k)) \space dt$

= ???

A.

$\Large \frac{\psi_k}{\dot{v_k}}(cos(\psi_k) - sin(\psi_k))$

B.

$\Large \frac{v_k}{\dot{\psi_k}}(sin(\psi_k + \dot{\psi_k}\Delta t) - sin(\psi_k))$

### Question 2:

$v_k \int_{t_k}^{t_{k+1}} sin(\psi_k + \dot{\psi_k} \cdot (t - t_k)) \space dt$

= ???

A.

$\Large \frac{v_k}{\dot{\psi_k}}(-cos(\psi_k + \dot{\psi_k}\Delta t) + cos(\psi_k))$

B.

$\Large \frac{\psi_k}{\Delta t}(tan(\psi_k) - sin(\psi_k))$
