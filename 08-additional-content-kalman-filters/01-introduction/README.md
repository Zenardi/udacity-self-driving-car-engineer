# Introduction

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=HbPxeJ3onmI)

## Summary

**Extended Kalman Filter and Unscented Kalman Filter**

The Extended Kalman Filter (EKF) is a powerful tool for solving problems related to advanced driver assistance systems and self-driving cars. It's commonly used in cruise control systems with automatic distance keeping. However, there's an alternative technique gaining attention - the Unscented Kalman Filter (UKF). The UKF can achieve even better results than the EKF.

**Key Concepts**

* **Extended Kalman Filter (EKF)**: a technique for dealing with nonlinear process models and measurement models by linearizing a nonlinear function.
* **Unscented Kalman Filter (UKF)**: an alternative to the EKF that uses sigma points to approximate the probability distribution, rather than linearization.
* **Sigma Points**: used in the UKF to approximate the nonlinear transition, which can be more accurate than linearization in many cases.
* **Jacobian Matrix**: not necessary to calculate when using the UKF.

**Practical Notes**

This lesson will cover the implementation of the Unscented Kalman Filter in C++ and its application to a challenging tracking scenario. The lesson has three parts:

1. Introduction to a sophisticated process model that estimates turn rate.
2. Explanation of how the UKF deals with nonlinear process models.
3. Step-by-step implementation of the filter in C++ using the UKF.

Note: This summary is based on the provided transcript and does not include any code or formulas, as they were not present in the original text.

## Transcript

<v English>Congratulations on mastering</v>
<v English>the extended Kalman Filter.</v> <v English>With this, you can solve a lot of</v>
<v English>problems related to advanced driver</v> <v English>assistance systems and</v>
<v English>self-driving cars.</v> <v English>>> Absolutely, if you look into</v>
<v English>the code of a car and cruise control</v> <v English>system with automatic distance keeping,</v>
<v English>you will find an Extended Kalman Filter.</v> <v English>>> There is also another</v>
<v English>technique gaining more and</v> <v English>more attention in this field.</v> <v English>It is called</v>
<v English>the Unscented Kalman Filter or UKF.</v> <v English>And you can achieve even</v>
<v English>better results with it.</v> <v English>The UKF is an alternative technique</v>
<v English>to deal norming your process models,</v> <v English>or nonlinear measurement models.</v> <v English>But instead of linearizing a nonlinear</v>
<v English>function, the UKF uses so-called</v> <v English>sigma points to approximate</v>
<v English>the probability distribution.</v> <v English>>> This has two advantages.</v> <v English>In many cases the sigma points</v>
<v English>approximate the nonlinear transition</v> <v English>better than a linearization does.</v> <v English>Also it is not necessary to</v>
<v English>calculate Jacobian matrix.</v> <v English>>> What are students are going</v>
<v English>to learn in the lesson?</v> <v English>>> This lesson has three parts.</v> <v English>First I will introduce a more</v>
<v English>sophisticated process model</v> <v English>that is able to estimate</v>
<v English>the turn rate of a.</v> <v English>Then I will show you how</v>
<v English>the Unscented Kalman Filter</v> <v English>deals with this nonlinear process model.</v> <v English>Finally, we will implement the filter</v>
<v English>together step by step in C++, and</v> <v English>use it to solve a challenging</v>
<v English>tracking scenario.</v> <v English>>> Let's get started and</v>
<v English>see how the UCAP works.</v>
