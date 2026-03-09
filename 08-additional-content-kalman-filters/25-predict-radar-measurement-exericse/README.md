# Predict Radar Measurement Exericse

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=GYQeizoj09E)

## Summary

**Predicting Radar Measurement Statistics**
=====================================

This project involves predicting the mean and covariance of a radar measurement. The goal is to develop a system that can accurately estimate these statistics from radar data.

### Key Concepts

* **Radar Measurement**: A three-dimensional vector representing the measurement obtained from a radar system.
* **Measurement Dimension**: The number of dimensions used to represent the radar measurement, set to 3 in this example.
* **Weights**: Values assigned to each dimension of the radar measurement to calculate the covariance matrix.
* **Covariance Matrix (R)**: A square matrix representing the variance and covariance between different dimensions of the radar measurement.
* **Radar Measurement Uncertainty**: The values required to build the covariance matrix, including the predicted sigma points.
* **Predicted Sigma Points**: The matrix used to store the measurement sigma points.
* **Output Objects**:
	+ **Predicted Measurement Mean**: The estimated mean value of the radar measurement.
	+ **Predicted Covariance Matrix (S)**: The estimated covariance between different dimensions of the radar measurement.

### Practical Notes

To complete this project, you will need to:

1. Set up a system to obtain and process radar measurements.
2. Assign weights to each dimension of the radar measurement.
3. Calculate the covariance matrix using the radar measurement uncertainty values.
4. Use the predicted sigma points to estimate the mean and covariance of the radar measurement.

Note: This project involves a coding quiz, so be sure to review the provided code and complete the exercises to practice your skills in predicting radar measurement statistics.

## Transcript

<v English>The goal of this coding quiz</v>
<v English>is to predict the mean and</v> <v English>the covariance of a radar measurement.</v> <v English>We expect a radar measurement, so I set</v>
<v English>the measurement dimension to three here.</v> <v English>This is an example how</v>
<v English>I set the weights.</v> <v English>To be able to build the measurement</v>
<v English>covariance matrix r,</v> <v English>you need the values for</v>
<v English>the radar measurement uncertainty.</v> <v English>And of course,</v>
<v English>you need the predicted sigma points.</v> <v English>This is the matrix, where you can</v>
<v English>store your measurement sigma points.</v> <v English>And these are the two output objects,</v> <v English>the predicted measurement mean, and</v>
<v English>the predicted covariance matrix, s.</v> <v English>Good luck with the quiz.</v>

## Additional Content

### Helpful Equations

#### State Vector

$$x_{k+1|k}=\begin{bmatrix}
p_x\\
p_y\\
v\\
\psi\\
\dot{\psi}
\end{bmatrix}$$

#### Measurement Vector

$$z_{k+1|k}=\begin{bmatrix}
\rho\\
\varphi\\
\dot{\rho}
\end{bmatrix}$$

#### Measurement Model

$$z_{k+1|k}=h(x_{k+1}) + w_{k+1}$$

$$\rho = \sqrt{p_x^2+p_y^2}$$

$$\varphi =arctan(\frac{p_y}{p_x})$$

$$\dot{\rho}=\frac{p_xcos(\psi)v+p_ysin(\psi)v}{\sqrt{p_x^2+p_y^2}}$$

#### Predicted Measurement Mean

$$\large  
z_{k+1|k} = \sum_{i=1}^{n_\sigma} w_i Z_{k+1|k,i}$$

#### Predicted Covariance

$$\large 
S_{k+1|k} = \sum_{i=1}^{n_\sigma} w_i( Z_{k+1|k,i} - z_{k+1|k})(Z_{k+1|k,i} - z_{k+1|k})^T + R$$

$$\large
R = E(w_k\cdot w_k^T) = \begin{bmatrix}
\sigma_{\rho}^2 \qquad 0\qquad0\\
0\qquad\sigma_{\varphi}^2 \qquad 0\\
0\qquad0\qquad\sigma_{\dot{\rho}}^2 
\end{bmatrix}$$

>Note: 
* The assignment files are present in `/home/workspace/assignments/05_predict_radar_measurement` and the solution files are present in `/home/workspace/solutions/05_predict_radar_measurement`

* After completing the assignment, you can run the code from the workspace terminal as follows:
	```bash
    cd /home/workspace/assignments/05_predict_radar_measurement
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
* Test your output against the output of the solution code. You can run the solution code as follows:
	```bash
    cd /home/workspace/solutions/05_predict_radar_measurement
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
