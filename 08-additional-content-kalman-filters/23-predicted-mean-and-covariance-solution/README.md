# Predicted Mean and Covariance Solution

> Part of: **Unscented Kalman Filters**

## Additional Content

### Solution

The first part of my solution is setting a vector of weights as we discussed in the last video. 

The predicted state mean is just the implementation of the corresponding equation. 

When calculating the predicted state covariance matrix, I did something you might not have done. In the equation we always need the difference between the mean predicted state and a sigma points. The problem here is that the state contains an angle. As you have learned before, subtracting angles is a problem for Kalman filters, because the result might be

$2\pi$

plus a small angle, instead of just a small angle. That’s why I normalize the angle here.

Make sure you always normalize when you calculate the difference between angles.
