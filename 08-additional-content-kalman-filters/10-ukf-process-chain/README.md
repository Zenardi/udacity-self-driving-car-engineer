# UKF Process Chain

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=sU7ifLgxxas)

## Summary

**UKF and Incentive Common Filter**

This project focuses on developing a process model that considers the possibility of driving on a straight line or making a turn. The goal is to achieve good results when tracking a bike in a later project.

### Key Concepts

* **CTR Model**: A process model that takes into account the possibility of driving on a straight line or making a turn.
* **UKF (Unscented Kalman Filter)**: A type of filter that processes measurements over time, similar to the extended common filter.
* **Prediction Step**: An independent step in the UKF process that uses the CTR model for prediction.
* **Update Step**: The second step in the UKF process where the radar or laser measurement model is used to update the state estimate.
* **Incentive Transformation**: A technique used by the incentive common filter to handle non-linear process models or measurement models.

### Practical Notes

To implement the UKF and incentive common filter, you will need to:

* Use the CTR model for prediction in the prediction step
* Update the state estimate using the radar or laser measurement model in the update step
* Apply the incentive transformation technique when dealing with non-linear process models or measurement models.

Note: This summary is based on a limited transcript and may not cover all aspects of the lesson.

## Transcript

<v English>What you have derived for</v>
<v English>the CTR remodel, is a process model that</v> <v English>considers the possibility to drive</v>
<v English>on a straight line, or doing a turn.</v> <v English>That's really great because it will</v>
<v English>help us to achieve good results</v> <v English>when tracking a bike</v>
<v English>in the project later.</v> <v English>Now let's go to the next part of this</v>
<v English>lesson, and see how the UKF works.</v> <v English>The way the incentive common filter</v>
<v English>processes measurements over time is</v> <v English>exactly the same as the extended</v>
<v English>common filter does.</v> <v English>We have a prediction step, which is</v>
<v English>independent of the measurement model.</v> <v English>In this step, you will use</v>
<v English>the CTR model we just arrived.</v> <v English>Then we have an update step where we</v>
<v English>use the radar measurement model, or</v> <v English>the laser measurement model,</v> <v English>depending on the type of</v>
<v English>measurement we just received.</v> <v English>This means you'll be able to apply</v>
<v English>the same top level processing chain for</v> <v English>the incentive common filter as you</v>
<v English>use for the extended common filter.</v> <v English>The difference between the incentive and</v>
<v English>the extended common filters is how</v> <v English>the incentive common filter deals</v>
<v English>with the non linear process models or</v> <v English>measurement models.</v> <v English>For that, the incentive common filter</v>
<v English>uses an approach called incentive</v> <v English>transformation.</v> <v English>Let me show what this is.</v>

## Additional Content

### Unscented Kalman Filter Introduction

Now that you have learned the CTRV motion model equations, we will discuss how the unscented Kalman filter works. As you go through the lectures, recall that the extended Kalman filter uses the Jacobian matrix to linearize non-linear functions. 

The unscented Kalman filter, on the other hand, does not need to linearize non-linear functions; instead, the unscented Kalman filter takes representative points from a Gaussian distribution. These points will be plugged into the non-linear equations as you'll see in the lectures.
