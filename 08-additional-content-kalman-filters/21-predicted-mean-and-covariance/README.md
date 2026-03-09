# Predicted Mean and Covariance

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6DELFN7Fz4c)

## Summary

**UKF Prediction Step: Calculating Mean and Covariance**

This README file provides a summary of the key concepts covered in the Udacity lesson on calculating the mean and covariance matrix of predicted state samples using the Unscented Kalman Filter (UKF) algorithm.

### Key Concepts

* **Sigma Points**: These are points that represent the predicted state, calculated by propagating the original state through the system model.
* **Mean Calculation**: The mean of the predicted state is calculated using the following formula: `mean = Σ(w_i \* x_pred_i)`, where `w_i` are the weights and `x_pred_i` are the predicted Sigma points.
* **Covariance Matrix Calculation**: The covariance matrix of the predicted state is calculated using the following formula: `cov = Σ(w_i \* (x_pred_i - mean) \* (x_pred_i - mean)^T)`, where `w_i` are the weights and `x_pred_i` are the predicted Sigma points.
* **Weights Calculation**: The weights for each Sigma point are calculated using the following formula: `w_i = λ / (n + λ) \* N(x_pred_i)`, where `λ` is the spreading parameter, `n` is the number of dimensions, and `N(x_pred_i)` is the normalized Gaussian distribution.
* **Spreading Parameter**: The spreading parameter `λ` determines how far to spread the Sigma points from the mean. It must be chosen carefully to ensure accurate results.

### Practical Notes

To implement the UKF prediction step in C++, you will need to:

* Calculate the predicted Sigma points using the system model and the original state.
* Calculate the weights for each Sigma point using the formula above.
* Use the weights and predicted Sigma points to calculate the mean and covariance matrix of the predicted state.

Note that there are multiple ways to define the weights, and you may need to adjust this implementation based on your specific use case.

## Transcript

<v English>Awesome. You implemented a C++ function to predict the Sigma points.</v> <v English>This means, we can move on to the next step and</v> <v English>calculate the mean and the covariance matrix of the predicted state.</v> <v English>Let's look at the visualization again.</v> <v English>First, we generated the Sigma points.</v> <v English>Then, we predicted them.</v> <v English>Now, we want to use the Sigma points to calculate</v> <v English>the mean and the covariance of the predicted state.</v> <v English>The standard rule for calculating the mean and</v> <v English>covariance of a group of state samples is given by these equations.</v> <v English>The index i means,</v> <v English>we are talking about the column number i of this matrix.</v> <v English>However, we have these additional weights we need to consider.</v> <v English>Obviously, we need a weight for every Sigma point,</v> <v English>and this is how the weights are calculated.</v> <v English>You can see that these weights somehow depend on the spreading parameter lambda.</v> <v English>We use lambda before to set how far we want to spread the Sigma points.</v> <v English>Why do we need to consider lambda again here?</v> <v English>Think about it like this.</v> <v English>Before we had a covariance matrix and generated Sigma points,</v> <v English>now we're doing the inverse step.</v> <v English>We have predicted Sigma points and we want to recover the covariance matrix.</v> <v English>So, we also have to invert the spreading of the Sigma points,</v> <v English>and this is what the weights do.</v> <v English>There's more than one correct way to define</v> <v English>these weights and you will find several suggestions if you look into the literature.</v> <v English>But in this lesson, we will stick with these rules. All right.</v> <v English>That's how you calculate the mean and the covariance of your predicted Sigma points.</v> <v English>With this, you will have completed the UKF prediction step.</v>

## Additional Content

## Note Regarding Sigma Point Generation and Prediction Steps
- **Sigma Point Generation:** Sigma points are generated using ```Calligraphic-X(k)```, followed by a nonlinear transformation ```f(x_k,nu_k)```.
- **Sigma Point Prediction:** The generated Sigma points are propagated to obtain the state of the system at time k+1.  These predicted points are denoted ```Calligraphic-X(k+1)```.
