# Kalman Filter Prediction

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=HTL5-0DDqE4)

## Summary

**Kalman Filter: 2D Estimation**

This README file summarizes the key concepts and practical notes from the Udacity lesson on building a 2-dimensional estimate using a Kalman filter.

### Key Concepts

* **Gaussian Distribution**: A probability distribution that is elevated around the correct location, but broad in the space of velocities.
* **Prediction Step**: The process of predicting the next state (location and velocity) based on the current state and an assumed velocity.
* **Posterior Distribution**: The updated distribution of the system's state after incorporating new information from measurements or predictions.
* **Kalman Gain**: Not explicitly mentioned in this lesson, but implied as a crucial component in updating the posterior distribution.

### Practical Notes

The lesson demonstrates how to use a Kalman filter for 2D estimation by:

* Assuming an initial velocity and predicting the next state (location and velocity) based on that assumption.
* Updating the posterior distribution after incorporating new information from measurements or predictions.
* Visualizing the prediction step using a Gaussian distribution and selecting the most likely outcome.

Note: The lesson does not provide code examples, but rather focuses on conceptual understanding of the Kalman filter algorithm.

## Transcript

In Kalman filter land, we're going to build a 2-dimensional estimate. 1 for the location, and 1 for the velocity denoted x dot. The velocity can be zero. It can be negative, or it can be positive. If initially I know my location, but not my velocity, then I represent it with a Gaussian that's elevated around the correct location, but really, really broad in the space of velocities.

Let's look at the prediction step. In the prediction step, I don't know my velocity, so I can't possibly predict for location. I'm going to assume. But miraculously, there'll be some interesting correlation. So let's for a second, just pick a point on this distribution over here.

Let me assume my velocity is 0. Of course, in practice, I don't know the velocity, but let me assume for a moment the velocity is 0. Where would my posterior be after the prediction? Well, we know we started in location 1. The velocity is 0, so my location would likely be here.

Now let's change my belief in velocity and pick a different one. Let's say the velocity is 1. Where would my prediction be 1 time step later starting at location 1 and velocity 1? I'll give you 3 choices. Here?

Here? Or here? Please pick the one that makes the most sense. The answer is right over here. Why?

If a car's starting point is the point over here, for which we know the location is 1, and the velocity is 1, and if we predict 1 time step in the future, then for that prediction, we know the location will be 2, and the velocity might be a little uncertain, but it stays about the same. So we end up with a point over here. Let's do this again.

## Images

![There is a line graph showing points 1, 2, 3 and 4. t =1 is over 1. t =2 is over 2. t =3 is over 3. t=4 is circled.  “Prediction” is a graph with 1 through 4 on the x axis and -1 to 2 on the y axis.  There is a line through x = 1.   You have to select from one of three points - (1, 1), (2, 0) and (2, 1).](images/kalman-filter-prediction.jpg)
*Quiz Options*

### Solution

[Watch on YouTube](https://www.youtube.com/watch?v=SK3cnmu8BYU)