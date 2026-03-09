# Measurement Prediction

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=qDX8nL_OT60)

## Summary

**Predicting Measurement in Unscented Kalman Filter (UKF)**

The Unscented Kalman Filter (UKF) is a sophisticated algorithm for state estimation and prediction. This summary covers the key concepts and practical steps involved in predicting measurement using UKF.

### Key Concepts

* **Measurement Model**: A function that defines the transformation of the predicted state into the measurement space.
* **Sigma Points Reuse**: A shortcut to reuse signal points from the previous prediction step instead of generating new ones.
* **Augmentation Step Skipping**: In cases where the measurement noise has a purely additive effect, the augmentation step can be skipped.
* **Measurement Noise Accounting**: The measurement covariance noise is added to calculate the resulting mean and covariance of the predicted measurement.

### Practical Notes

To predict the measurement using UKF:

1. Transform the individual sigma points into the measurement space using the measurement model.
2. Store the transformed measurement signal points as columns in a matrix, called `Z`.
3. Calculate the resulting mean and covariance of the predicted measurement by adding the measurement covariance noise.

Note that this step is similar to the prediction step, but with two shortcuts: reusing sigma points and skipping augmentation when applicable.

## Transcript

<v English>You have successfully predicted</v>
<v English>the state mean and covariance matrix.</v> <v English>Terrific, this means we can go</v>
<v English>into the update step now and</v> <v English>predict the measurement.</v> <v English>This is where we are now.</v> <v English>We have successfully predicted</v>
<v English>the state from times step k</v> <v English>to times k step plus one.</v> <v English>Now we have to transform the predicted</v>
<v English>state into the measurement space.</v> <v English>The function that defines this</v>
<v English>transformation is the measurement model.</v> <v English>Of course, now we have to consider what</v>
<v English>kind of sensor produced the current</v> <v English>measurement and</v>
<v English>use the corresponding measurement model.</v> <v English>The problem we have here is very similar</v> <v English>to the problem we had</v>
<v English>in the prediction step.</v> <v English>We need to transform a distribution</v>
<v English>through a non linear function so</v> <v English>we can apply exactly the same on</v>
<v English>center transformation approach</v> <v English>as we did before during</v>
<v English>the state prediction.</v> <v English>However, we can take two shortcuts</v>
<v English>here and make it a little easier.</v> <v English>Let me show you how.</v> <v English>The first thing we did in the prediction</v>
<v English>step was generating [INAUDIBLE] points.</v> <v English>We could do the same here again</v>
<v English>using the predicted mean and</v> <v English>covariance matrix.</v> <v English>However, a popular shortcut is</v> <v English>to just reuse the signal points we</v>
<v English>already have from the prediction step.</v> <v English>So we can skip generating</v>
<v English>sigma points this time.</v> <v English>In this very case,</v>
<v English>we can also skip the augmentation step.</v> <v English>Why is that?</v> <v English>We needed the augmentation</v>
<v English>because the process noise</v> <v English>had a non linear effect on the state.</v> <v English>Let's assume we're talking about</v>
<v English>a greater measurement in this example.</v> <v English>Here the measurement model was</v>
<v English>a non linear fraction, but</v> <v English>the measurement noise had</v>
<v English>a purely additive effect.</v> <v English>In this case we don't need</v>
<v English>to perform an augmentation,</v> <v English>there is an easier way to</v>
<v English>consider the measurement noise.</v> <v English>I will show you later how this works.</v> <v English>So the only thing that's left for</v>
<v English>us to do is actually transforming</v> <v English>the individual sigma points we already</v>
<v English>have into the measurement space and</v> <v English>using them to calculate the mean and</v> <v English>the covariance matrix S of</v>
<v English>the predicted measurement.</v> <v English>Again, we want to store the transformed</v>
<v English>measurement signal points</v> <v English>as columns in a matrix.</v> <v English>I call this matrix colorgraphic Z.</v> <v English>Remember the measurement</v>
<v English>space of the rater.</v> <v English>This was the radial distance rho,</v>
<v English>the angle phi, and</v> <v English>the radial velocity rho dot, so</v>
<v English>it is a three dimensional space.</v> <v English>This means the matrix with the</v>
<v English>measurement sigma points has three rows</v> <v English>and 15 columns in our case.</v> <v English>Regarding for</v>
<v English>the measurement noise omega,</v> <v English>just put in 0 here, since we will</v>
<v English>account for the measurement noise later.</v> <v English>Now that we have the sigma points and</v>
<v English>the measurement space, We want to</v> <v English>calculate the resulting mean and</v>
<v English>covariance of the predicted measurement.</v> <v English>This is also very similar as before and</v>
<v English>given by these equations.</v> <v English>The only thing that comes</v>
<v English>in addition here is that we</v> <v English>add the measurement covariance noise.</v> <v English>This is how we account for</v>
<v English>the measurement noise.</v> <v English>Remember, we can do this instead</v>
<v English>of the augmentation here,</v> <v English>because the measurement noise</v>
<v English>in our case does not have</v> <v English>a non-linear effect on the measurement</v>
<v English>but it's purely additive.</v> <v English>And that's how you predict</v>
<v English>the measurement mean and covariance.</v> <v English>It's exactly the same</v>
<v English>problem set as before, but</v> <v English>by using the two sharp cards I just</v>
<v English>introduced, it is a very easy step.</v> <v English>After this step you have made it almost</v>
<v English>through the UKF processing chain.</v>
