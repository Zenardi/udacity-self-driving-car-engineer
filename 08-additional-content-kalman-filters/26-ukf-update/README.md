# UKF Update

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=pJ5XauGNclI)

## Summary

**UKF Update Step: Fusing Data from Different Sensors**

The UKF update step is a crucial part of the Unscented Kalman Filter algorithm. It enables you to fuse data from different sensors, making it a powerful and useful ability in various applications.

### Key Concepts

* **Predicted state mean and covariance**: These are the estimates of the system's state and its uncertainty after prediction.
* **Predicated measurement mean and covariance**: These are the estimates of the measurement and its uncertainty before updating with actual measurements.
* **Actual measurement zk+1**: This is the actual measurement received at time step k+1, which is used to update the predicted state and covariance matrix.
* **Cross-correlation matrix**: This matrix represents the relationship between the predicted sigma points in the state space and the predicted sigma points in the measurement space.

### Practical Notes

The UKF update calculation involves updating the predicted state mean and covariance with the actual measurement. The key difference from the standard Kalman filter is how the Kalman gain K is calculated, which requires the cross-correlation matrix between the predicted sigma points in the state space and the predicted sigma points in the measurement space.

To implement this step, you will need to:

* Calculate the predicted sigma points in both the state and measurement spaces
* Compute the cross-correlation matrix
* Update the Kalman gain K using the cross-correlation matrix
* Use the updated Kalman gain to update the predicted state mean and covariance matrix

With this understanding, you are now ready to implement your own UKF and fuse data from different sensors.

## Transcript

<v English>Congrats, you have made it</v>
<v English>almost through the UKF.</v> <v English>This is the last step you need to learn,</v>
<v English>and then you will be ready to</v> <v English>implement your own UKF and</v>
<v English>fuse data from different sensors.</v> <v English>This is a very powerful and</v>
<v English>useful ability.</v> <v English>So let's see how the final step works</v>
<v English>and how you can update your state and</v> <v English>your covariance matrix</v>
<v English>with the measurement.</v> <v English>What we have is this, the predicted</v>
<v English>state mean and covariance and</v> <v English>the predicated measurement mean and</v>
<v English>covariance.</v> <v English>But there's one more thing that we need,</v>
<v English>and</v> <v English>this is the actual measurement zk+1</v>
<v English>that we receive for the time step k+1.</v> <v English>This is actually the first</v>
<v English>time we really need to</v> <v English>know the measurement values.</v> <v English>What we needed right from the beginning</v>
<v English>was the time of the measurement, so</v> <v English>we could predict to the correct time.</v> <v English>And later, the sensor type so we could</v>
<v English>use the correct measurement model</v> <v English>in the measurement prediction step.</v> <v English>But this is the first time where we</v>
<v English>look into the measurement values.</v> <v English>The update calculation closes</v>
<v English>the processing chain and</v> <v English>produces the updated state mean and</v>
<v English>the updated state covariance matrix.</v> <v English>These equations are exactly the same</v>
<v English>as for the standard Kalman filter.</v> <v English>The only difference here is how</v>
<v English>you calculate the Kalman gain K.</v> <v English>Here you need the cross-correlation</v>
<v English>matrix between the predicted sigma</v> <v English>points in the state space and</v> <v English>the predicted sigma points</v>
<v English>in the measurement space.</v> <v English>And that's it.</v> <v English>With this, you're done processing</v>
<v English>the measurement at time step k+1, and</v> <v English>you're ready to handle the next</v>
<v English>measurement at time step k+2.</v>
