# Kalman Prediction

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=doyrdLJ6rJ4)

## Summary

**2D Kalman Filter: Estimating Object Location in Higher Dimensional Spaces**
===========================================================

The 2D Kalman filter is an extension of the 1D Kalman filter, which enables estimation of object location in higher dimensional spaces. In this lesson, we explore how the 2D Kalman filter works and its applications in tracking objects.

**Key Concepts**

* **Higher Dimensional State Spaces**: The 2D Kalman filter operates on state spaces with two or more dimensions, such as x and y coordinates.
* **Implicit Velocity Estimation**: The Kalman filter infers velocity from multiple position measurements, even though the sensor only measures position.
* **Predictive Modeling**: The Kalman filter uses velocity estimates to make predictions about future locations of the object.

**Practical Notes**

The 2D Kalman filter is particularly useful in tracking applications where objects move in two or more dimensions. For example, a self-driving car might use a radar sensor to detect the location of another vehicle over time. The Kalman filter enables the car to infer velocity from position measurements and make predictions about future locations.

To implement a 2D Kalman filter, you would need to:

* Define the state space (x, y coordinates)
* Measure object positions at multiple time steps
* Use the Kalman filter algorithm to estimate velocity and predict future locations

The code for implementing a 2D Kalman filter is not provided in this lesson. However, understanding the key concepts and practical notes above will help you develop your own implementation using programming languages such as Python or MATLAB.

## Transcript

<v English>Now we understand a lot about the 1D Kalman filter.</v> <v English>You've programmed one. You understand how to incorporate measurements.</v> <v English>You understand how to incorporate motion,</v> <v English>and you really implement something that's actually really cool,</v> <v English>which is a full Kalman filter for the 1D case.</v> <v English>Now in reality, we often have many Ds,</v> <v English>and then things become more involved, so I'm going to just tell you how things work</v> <v English>with an example, and why it's great to estimate in higher dimensional state spaces.</v> <v English>Suppose you have a 2-dimensional state space of x and y--like a camera image,</v> <v English>or in our case, we might have a car that uses a radar to detect the location</v> <v English>of a vehicle over time.</v> <v English>Then what the 2D Kalman filter affords you is something really amazing,</v> <v English>and here is how it goes.</v> <v English>Suppose at time t = 0, you observe the object of interest to be at this coordinate.</v> <v English>This might be another car in traffic for the Google self-driving car.</v> <v English>One time step later, you see it over here.</v> <v English>Another time step later, you see it right over here.</v> <v English>Where would you now expect at time t = 3 the object to be?</v> <v English>Let me give you 3 different places.</v> <v English>Please click at the most likely location.</v>

The answer is here. What the Kalman filter does for you, if you do estimation and higher dimensional spaces, is to not just go into x and y spaces, but allows you to implicitly figure out what the velocity of the object is, and then use the velocity estimate to make a really good prediction about the future. Now notice the sensor itself only sees position. It never sees the actual velocity.

Velocity is inferred from seeing multiple positions. So one of the most amazing things about Kalman filters in tracking applications is it's able to figure out, even though it never directly measures it, the velocity of the object, and from there is able to make predictions about future locations that incorporate velocity. That is just really, really, really great. That's one of the reasons that Kalman filters are such a popular algorithm in artificial intelligence and in control theory at large.

## Images

![There are four points in a nearly perfect diagonal line, sloping upwards from t=0 to t= 1 to t=2 to t=3. Your job is to find where t =4 would be from three points.  The first point, A, is also where it was at at t=2.  The second point, B, It is not on the diagonal line but has a vertical component that is higher than t=3 and a horizontal component that is further right from the line.  The third point, C, is not on the diagonal line but is further up and further to the right than A or B.](images/kalman-prediction.jpg)
*Quiz Options*

## Additional Content

## Kalman Prediction

### Quiz Image

### Solution
