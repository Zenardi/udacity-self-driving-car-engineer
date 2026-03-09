# UKF Basics Unscented Transformation

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=8jbckHQDl4A)

## Summary

**Unscented Transformation for Nonlinear Systems**

The unscented transformation is a method used to solve the problem of transforming a state distribution through a nonlinear function. This technique is particularly useful when dealing with systems that have nonlinear relationships between their states.

### Key Concepts

* **Sigma points**: These are representative points chosen around the mean state and in relation to the standard deviation signal of every state dimension.
* **Unscented transformation**: A method used to transform a state distribution through a nonlinear function by propagating sigma points through the system.
* **Mean and covariance calculation**: The predicted mean and covariance can be calculated from the predicted sigma points, providing an approximation of the true predicted distribution.

### Practical Notes

The unscented transformation is a useful technique for approximating the behavior of nonlinear systems. It involves three main steps:

1. **Choosing sigma points**: Sigma points are chosen around the mean state and in relation to the standard deviation signal of every state dimension.
2. **Predicting sigma points**: The chosen sigma points are inserted into the process function to predict their new values.
3. **Calculating prediction, mean, and covariance**: The predicted mean and covariance can be calculated from the predicted sigma points.

In the context of this lesson, we will implement a C++ function for each step of the unscented Kalman filter, starting with the prediction step. This will provide a practical understanding of how to apply the unscented transformation in a real-world scenario.

## Transcript

<v English>The end center transformation solves</v>
<v English>this problem using sigma points.</v> <v English>What are these sigma points,</v>
<v English>and how do they help us?</v> <v English>It can be difficult to transform</v>
<v English>the whole state distribution through</v> <v English>a nonlinear function.</v> <v English>But it is very easy to transform</v>
<v English>individual points of the state space</v> <v English>through the non-linear function, and</v>
<v English>this is what sigma points are for.</v> <v English>The sigma points are chosen around the</v>
<v English>mean state and in a certain relation to</v> <v English>the standard deviation signal</v>
<v English>of every state dimension.</v> <v English>This is why these points</v>
<v English>are called sigma points.</v> <v English>This serve as representatives</v>
<v English>of the whole distribution.</v> <v English>Once you have chosen the sigma points,</v> <v English>you just insert every single sigma</v>
<v English>point into the non and your function f.</v> <v English>So they will come out somewhere</v>
<v English>here in the predictive state space.</v> <v English>All you have to do now is</v>
<v English>calculate the mean and</v> <v English>the covariance of your</v>
<v English>group of sigma points.</v> <v English>This will now provide the same mean and</v> <v English>covariance as the real</v>
<v English>predicted distribution.</v> <v English>But in many cases,</v>
<v English>it gives a useful approximation.</v> <v English>By the way, you can apply the same</v>
<v English>technique in the linear case.</v> <v English>In this case, you will even find</v>
<v English>the exact solution of the sigma points.</v> <v English>So if the process more or</v>
<v English>less linear, the sigma point approach</v> <v English>provides exactly the same solution</v>
<v English>as the standard common feature.</v> <v English>But you would not use</v>
<v English>sigma points here because</v> <v English>they are more expensive in</v>
<v English>terms of calculation time.</v> <v English>So let's wrap this up.</v> <v English>This is what you really have because</v>
<v English>of your non linear process model.</v> <v English>This is the best possible mean and</v>
<v English>covariance you could use</v> <v English>if you want to keep pretending</v>
<v English>you have a normal distribution.</v> <v English>And this is what the sigma</v>
<v English>points give you.</v> <v English>Now you know the general idea</v>
<v English>of an unscented transformation.</v> <v English>Time to get started with</v>
<v English>the unscented Kalman filter.</v>

<v English>What we will do in the remaining part of</v>
<v English>this lesson is go through the processing</v> <v English>chain of the unscented</v>
<v English>Kalman filter step by step.</v> <v English>We will start with an example state</v>
<v English>vector x and covariance matrix p and</v> <v English>go all the way through prediction and</v> <v English>measurement step until we reach</v>
<v English>the updated state and covariance matrix.</v> <v English>For every step, you will implement</v>
<v English>a C++ function right away.</v> <v English>So you will be well prepared for</v>
<v English>the project in the end.</v> <v English>As always, we will of course</v>
<v English>start with the prediction step.</v> <v English>As you've seen before, we can split the</v>
<v English>unscented prediction into three parts.</v> <v English>First, we need to know a good</v>
<v English>way to choose sigma points.</v> <v English>Second, we need to know how</v>
<v English>to predict the sigma points.</v> <v English>Well, that's easy, just insert</v>
<v English>them into the process function.</v> <v English>And third, you need to know how to</v>
<v English>calculate the prediction, mean, and</v> <v English>covariance from</v>
<v English>the predicted sigma points.</v> <v English>Let's start with the first step.</v> <v English>How do we choose the sigma points?</v>
