# UKF Update Exercise

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=f36o4sCEQvY)

## Summary

**Summary of Key Concepts**

This lesson covers the calculation of the **Updated State X** and the **Updated Covariance Matrix P**, which are essential components in a state estimation problem. The instructor provides guidance on pre-calculating data, using variables to store intermediate results, and overriding previously calculated values with updated ones.

### Key Concepts

* **State Estimation**: Calculating the current state of a system based on measurements.
* **Updated State X**: The estimated state of the system after incorporating new measurements.
* **Updated Covariance Matrix P**: A measure of the uncertainty associated with the estimated state.
* **Predicted Sigma Points**: Pre-calculated data points used to estimate the state and covariance matrix.
* **Cross Correlation Matrix t**: A matrix used to calculate the correlation between the predicted sigma points and the actual measurement.

### Practical Notes

To implement this lesson, you will need to:

* Use variables `x` and `P` to store your updated state and covariance matrix.
* Pre-calculate data for the predicted sigma points in both the state space and measurement space.
* Store intermediate results for the cross correlation matrix `t`.
* Override previously calculated values with updated ones using the same variable names (`x` and `P`).

## Transcript

<v English>Welcome to the last coding</v>
<v English>quiz before the project.</v> <v English>We want to calculate this time</v>
<v English>is the UpdatedState X and</v> <v English>the UpdatedCovariance matrix P.</v> <v English>We need a lot of</v>
<v English>pre-calculated data this time.</v> <v English>These are the predicted sigma</v>
<v English>points in the state space.</v> <v English>This is the predicted state mean and</v>
<v English>the state prediction covariance.</v> <v English>You can use this variable x again, and</v> <v English>override it later with</v>
<v English>the updated state.</v> <v English>The same is true for</v> <v English>the variable p, override this one</v>
<v English>with the updated covariance matrix.</v> <v English>Here we have the predicted sigma</v>
<v English>points in the measurement space.</v> <v English>This is the predicted</v>
<v English>measurement mean and</v> <v English>this is the covariance of</v>
<v English>the measurement prediction.</v> <v English>And of course, you need some values for</v>
<v English>the actual measurement z.</v> <v English>Here you can store your</v>
<v English>intermediate results for</v> <v English>the cross correlation matrix t.</v> <v English>Again, make sure to use the variable</v>
<v English>x and the variable P to store your</v> <v English>updated state and</v>
<v English>your updated covariance matrix.</v> <v English>All right,</v>
<v English>good luck with this final coding quiz.</v>

## Additional Content

### Helpful Equations

#### Cross-correlation Matrix

$$T_{k+1|k} = \sum_{i=1}^{n_\sigma} w_i (X_{k+1|k,i} - x_{k+1|k})\ (Z_{k+1|k,i} - z_{k+1|k})^T$$

#### Kalman gain K

$$K_{k+1|k} = T_{k+1|k}S^{-1}_{k+1|k}$$

#### Update State

$$x_{k+1|k+1} = x_{k+1|k}+K_{k+1|k}(z_{k+1}-z_{k+1|k})$$

#### Covariance Matrix Update

$$P_{k+1|k+1} = P_{k+1|k}-K_{k+1|k}S_{k+1|k}K^T_{k+1|k}$$

>Note: 
* The assignment files are present in `/home/workspace/assignments/06_ukf_update` and the solution files are present in `/home/workspace/solutions/06_ukf_update`

* After completing the assignment, you can run the code from the workspace terminal as follows:
	```bash
    cd /home/workspace/assignments/06_ukf_update
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
* Test your output against the output of the solution code. You can run the solution code as follows:
	```bash
    cd /home/workspace/solutions/06_ukf_update
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
