# CTRV Process Noise Position

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=DJ_K1udemNk)

## Summary

**Influence of Noise Vectors on Position**
=====================================

This README file summarizes the key concepts related to the influence of noise vectors on position, as discussed in the Udacity lesson.

### Key Concepts
* **Noise Vectors**: The lesson discusses two types of noise vectors: yaw acceleration noise and longitudinal acceleration noise. These noise vectors affect the position of an object.
* **Yaw Acceleration Noise**: Yaw acceleration noise changes the radius of a circle being driven, influencing the position of the object. However, its effect is assumed to be relatively small compared to other factors.
* **Longitudinal Acceleration Noise**: The exact calculation for longitudinal acceleration noise involves solving a differential equation with constant acceleration. An approximation method is suggested, which assumes an acceleration offset similar to that of a car driving straight.

### Practical Notes
To apply the concepts learned in this lesson:

* Understand how yaw and longitudinal acceleration noises affect the position of an object.
* Use the approximation method for longitudinal acceleration noise when solving differential equations with constant acceleration.
* Be aware of the limitations of the approximation method, particularly at high speeds.

## Transcript

<v English>Now, let's look at the influence of the noise vector on the position.</v> <v English>For this, I will zoom in to our object.</v> <v English>This is where our object is at time step k,</v> <v English>and this is where our object is at time step k plus one,</v> <v English>without any acceleration noise.</v> <v English>Clearly, the yaw acceleration noise will change the radius of the circle we are driving.</v> <v English>So, the yaw acceleration does have some influence on to the position.</v> <v English>If the yaw acceleration is positive,</v> <v English>we might end up here.</v> <v English>If the yaw acceleration is negative,</v> <v English>we might end up here.</v> <v English>However, we assume the effect of the yaw acceleration on</v> <v English>the position is relatively small in comparison to other factors,</v> <v English>and we will neglect here.</v> <v English>Now, let's look at the effect of the longitudinal acceleration noise on the position.</v> <v English>The exact calculation is pretty straight forward.</v> <v English>You have to go back to the differential equation where we started.</v> <v English>But this time, instead of a constant velocity,</v> <v English>you would need to assume a constant acceleration and then,</v> <v English>solve the integral for that case.</v> <v English>This is absolutely doable and you are welcome to give it a try,</v> <v English>but it takes some time.</v> <v English>I want to speed things up a little bit,</v> <v English>so we can go into the uncentered Kalman filter sooner.</v> <v English>So, I suggest using an approximation here,</v> <v English>which is really easy but it's still pretty close to the exact solution.</v> <v English>What we will use as an approximation,</v> <v English>is the acceleration offset of a car driving exactly straight, like here.</v> <v English>This approximation will be okay,</v> <v English>as long as the [inaudible] is not too high.</v> <v English>Can you tell me in the next quiz,</v> <v English>what the acceleration offset in px and py would be,</v> <v English>if the car drove perfectly straight?</v>

## Additional Content

### 1) What would the x acceleration offset be if the car were driving perfectly straight? In other words, what is

$a$

?

A.

$\frac{1}{2}(\Delta t)^2 cos(\psi_k) \cdot \nu_{a,k}$

B.

$\frac{1}{2}(\Delta t)^2 sin(\psi_k) \cdot \nu_{a,k}$

### 1) What would the y acceleration offset be if the car were driving perfectly straight? In other words, what is

$b$

?

A.

$\frac{1}{2}(\Delta t)^2 cos(\psi_k) \cdot \nu_{a,k}$

B.

$\frac{1}{2}(\Delta t)^2 sin(\psi_k) \cdot \nu_{a,k}$
