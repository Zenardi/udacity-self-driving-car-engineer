# Predicted Mean and Covariance Exercise

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=0vl_wfDpVec)

## Summary

**Mean Predicted State X and State Prediction Covariance P**

This README file provides a summary of key concepts related to calculating the mean predicted state X and state prediction covariance P in a statistical context.

### Key Concepts

* **Sigma points**: A set of weighted vectors used for predicting the state of a system.
* **Weights for sigma points**: A vector containing the weights assigned to each sigma point, used for calculating the predicted state mean and covariance.
* **Predicted state mean (X)**: The average value of the predicted states calculated using the sigma points and their corresponding weights.
* **State prediction covariance (P)**: A measure of the uncertainty or variability in the predicted state, calculated using the sigma points and their corresponding weights.

### Practical Notes

This lesson provides a basic understanding of how to calculate the mean predicted state X and state prediction covariance P. However, it does not provide any specific code examples or practical steps for implementation. The instructor simply mentions that you have already obtained the predicted sigma points and are now tasked with calculating the weights and applying them to determine the predicted state mean and covariance.

## Transcript

<v English>In this quiz, we have two</v>
<v English>objects we want to calculate.</v> <v English>The mean predicted state X and</v>
<v English>the state prediction covariance P.</v> <v English>This time we started the point but we</v>
<v English>already have the predicted sigma points.</v> <v English>This is a vector where you can put</v>
<v English>them the weights for the sigma points.</v> <v English>This is the vector for</v>
<v English>the predicted state mean and</v> <v English>this is the metrics for</v>
<v English>the state prediction conversions.</v> <v English>Good luck with this quiz.</v>

## Additional Content

### Helpful Equations

#### Weights

$\Large w_i =\frac{\lambda}{\lambda+n_{a}}, i =1$

$\Large w_i =\frac{1}{2(\lambda+n_{a})}, i =2...n_{a}$

#### Predicted Mean

$\Large x_{k+1|k} = \sum_{i=1}^{n_\sigma} w_i X_{k+1|k,i}$

#### Predicted Covariance

$\Large P_{k+1|k} = \sum_{i=1}^{n_\sigma} w_i( X_{k+1|k,i} - x_{k+1|k})(X_{k+1|k,i} - x_{k+1|k})^T$

>Note: 
* The assignment files are present in `/home/workspace/assignments/04_prediction_mean_covariance` and the solution files are present in `/home/workspace/solutions/04_prediction_mean_covariance`

* After completing the assignment, you can run the code from the workspace terminal as follows:
	```bash
    cd /home/workspace/assignments/04_prediction_mean_covariance
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
* Test your output against the output of the solution code. You can run the solution code as follows:
	```bash
    cd /home/workspace/solutions/04_prediction_mean_covariance
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
