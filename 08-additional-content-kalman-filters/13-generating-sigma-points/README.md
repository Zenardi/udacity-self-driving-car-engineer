# Generating Sigma Points

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=t7YJJpEzTX4)

## Summary

**UKF Prediction Step: Generating Sigma Points**
====================================================

This README file summarizes the key concepts and practical steps involved in generating Sigma points during the prediction step of the Unscented Kalman Filter (UKF) processing chain.

**Key Concepts**
---------------

* **Sigma points**: A set of points used to approximate a probability distribution, where each point represents a possible value of the state.
* **State dimension**: The number of dimensions in the state vector, which determines the number of Sigma points generated.
* **Lambda (λ)**: A design parameter that controls the spread of Sigma points relative to the mean state estimate.
* **Square root matrix**: A matrix `A` such that `A^T * A = P`, where `P` is the covariance matrix.

**Practical Notes**
------------------

To generate Sigma points, follow these steps:

1. Choose a value for Lambda (e.g., `2/3 - n_x`, where `n_x` is the state dimension).
2. Calculate the square root matrix `A` using an algorithm such as Cholesky decomposition.
3. The first column of the Sigma point matrix `X` is the mean state estimate.
4. For each remaining column, calculate the product of a vector from the square root matrix and the Lambda value, and add it to the mean state estimate.

Example:
```python
import numpy as np

# Define the mean state estimate and covariance matrix
x_mean = np.array([1, 2])
P = np.array([[3, 0], [0, 4]])

# Calculate the square root matrix A
A = np.linalg.cholesky(P)

# Choose a value for Lambda (e.g., 2/3 - n_x)
lambda_val = 2/3 - len(x_mean)

# Generate Sigma points
sigma_points = np.zeros((len(x_mean) + 1, len(x_mean)))
sigma_points[0] = x_mean

for i in range(1, len(sigma_points)):
    vector = A[:, i-1]
    sigma_points[i] = x_mean + lambda_val * vector

print(sigma_points)
```
Note that this is a simplified example and may not cover all edge cases.

## Transcript

<v English>We start at the beginning of the UKF processing chain which means,</v> <v English>we are in the prediction step and we want to generate Sigma points.</v> <v English>At the beginning of the prediction step,</v> <v English>we have the posterior state x k k,</v> <v English>and the posterior covariance matrix P k k from the last iteration.</v> <v English>They represent the distribution of our current state,</v> <v English>and for this distribution,</v> <v English>we now want to generate Sigma points.</v> <v English>The number of Sigma points depends on the state dimension.</v> <v English>Remember, this is the state vector of the CTR V model.</v> <v English>So, the dimension of our state is an x equals five.</v> <v English>We will choose two times an x plus one Sigma points.</v> <v English>The first point is the mean of the state, and then,</v> <v English>we have another two points per</v> <v English>state dimension which will be spread in different directions.</v> <v English>In our case, this would be 11 Sigma points.</v> <v English>To make things easier right now,</v> <v English>we will consider only two dimensions of our state vector,</v> <v English>the position Px and the position Py.</v> <v English>This makes it easier to visualize what's happening.</v> <v English>Now, that our state dimension is two,</v> <v English>we are only looking for five Sigma points.</v> <v English>Together with you, I want to calculate</v> <v English>these five Sigma points and store them in this matrix,</v> <v English>which I write as calligraphic X.</v> <v English>Every column of this matrix represents one Sigma point.</v> <v English>Let's bring this example to life and put</v> <v English>some realistic values into the mean state and the covariance matrix,</v> <v English>just as you will have it later in the real application.</v> <v English>Now, if you Google for</v> <v English>uncentered Kalman filter and look for a rule how to generate Sigma points,</v> <v English>this is what you will find.</v> <v English>This looks awful.</v> <v English>Maybe this is why people don't use the uncentered Kalman filter more often.</v> <v English>The good news is this rule is actually pretty simple to apply.</v> <v English>The first thing you need to know is what this Lambda is.</v> <v English>This is a design parameter.</v> <v English>You can choose where in relation to the error ellipse,</v> <v English>you want to put your Sigma points.</v> <v English>I will show you later how this effect works.</v> <v English>Some people report good results with Lambda equals 2 3 minus nx.</v> <v English>Another thing you might be wondering is what is the square root of a matrix?</v> <v English>More specifically, we are looking for the matrix A which fulfills</v> <v English>A transposed times A equals P.</v> <v English>There are several algorithms available that will calculate such a matrix.</v> <v English>Later, I will show you how to do this in C plus plus.</v> <v English>But here, I'll give you the solution for the square root matrix,</v> <v English>so we can continue,</v> <v English>and this is actually all we need to calculate the Sigma points.</v> <v English>So, how do we read this rule?</v> <v English>The first column of the matrix tells us what the first Sigma point is.</v> <v English>This is always easy because the first Sigma point is simply the mean state estimate.</v> <v English>This term contains two more Sigma points.</v> <v English>In this square root matrix,</v> <v English>we have two vectors.</v> <v English>The first vector points into</v> <v English>this direction and the other vector points into this direction,</v> <v English>and we multiply these vectors by this printing factor.</v> <v English>Now, you can see what the design parameter Lambda does.</v> <v English>If Lambda is larger,</v> <v English>the Sigma points move further away from the mean state.</v> <v English>If Lambda is smaller,</v> <v English>the Sigma points move closer to the mean state.</v> <v English>This all happens in relation to this error ellipse.</v> <v English>In our case, the resulting Sigma points will end up here.</v> <v English>In our example, the overall spreading factor works out to square root of three.</v> <v English>So, we multiply this vector and this vector by the square root of three,</v> <v English>and add it to the mean state.</v> <v English>Finally, here we use the same vectors again.</v> <v English>But we apply them in the opposite direction.</v> <v English>This means that these Sigma points will show up here, and here.</v> <v English>In the next quiz, I would like you to</v> <v English>calculate the two remaining Sigma points from our example.</v>
