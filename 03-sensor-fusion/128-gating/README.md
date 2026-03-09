# Gating

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=E5y2X9Jh54Y)

## Summary

**Association Matrix and Gating Method**
=====================================

This project introduces the concept of an association matrix and the gating method for reducing computational effort in tracking multiple objects. The goal is to efficiently assign measurements to their corresponding targets while minimizing false positives.

**Key Concepts**
---------------

* **Association Matrix**: A matrix used to store all possible associations between a target (truck) and its measurements.
* **Mahalanobis Distance**: A measure of distance based on the covariance, which can be visualized as an ellipse.
* **Gating Method**: A technique that defines a gate around each target in the form of an ellipse, only updating targets with measurements inside the gate.
* **Chi-Square Distribution**: The squared Gaussian distribution used to calculate the gating threshold from the inverse cumulative chi-squared distribution.
* **Gating Threshold**: A parameter (e.g., 0.995) that determines the percentage of true measurements expected to lie within the gate.

**Practical Notes**
------------------

To implement a gating method in Python, follow these steps:

1. Calculate the Mahalanobis distance between each target and its measurements.
2. Define the gating threshold using the inverse cumulative chi-squared distribution with the same dimension as the measurement space.
3. Check if the Mahalanobis distance is smaller than the threshold for each possible association pair.
4. If the distance is bigger, set the corresponding value in the association matrix to infinity and move on to the next pair.

Note: The gating method helps reduce the association complexity without decreasing performance by excluding unlikely combinations.

## Transcript

Well done, you've just implemented your first association matrix. Of course, the computational effort is quite high to calculate all possible distances. It does not really make sense to calculate the distances of very unlikely and faraway combinations. In this example, after the first three trucks have been updated, we have the false positive clutter measurement and two unassigned trucks left. The simple nearest neighbor would now assign the measurement to the green truck and update it.

This does not make sense because both are not close at all. How can we avoid that? Remember that we calculate the Mahalanobis distance based on the covariance, which can be visualized as an ellipse. Similarly, we can define a gate around the truck shaped like an ellipse and only update the truck with measurements inside the gate. How can we define the gate?

Remember that the Mahalanobis distance contains squared values of the residual. Therefore, we need a squared Gaussian distribution, which is the chi-square distribution. We calculate the gating threshold from the inverse cumulative chi-squared distribution, where the distribution has the same dimension as the measurement space. The parameter 0.995 means that 99.5 percent of true measurements will lie inside the gate. We only have a 0.5.

percent risk of throwing away a correct measurement through gating. If we are not limited in computational power, we can further increase this threshold or we can decrease it to accelerate the association. For every possible association between a truck X and a measurement C, we first check whether the Mahalanobis distance is smaller than the threshold. If the distance is bigger, we know this possible association pair and move on to the next. Let's see what happens in our example if we use gating.

The gating method excludes some very unlikely combinations. For example, the dotted connections in the image. We can simply set their distance in the matrix A to infinity. We stop updating trucks with measurements once A is empty or only contains infinity values. Gating helps us reduce the association complexity without decreasing the performance.

In the next exercise, I want you to implement a gating method in Python.

## Additional Content

## Gating
-

$\textbf{Gating}$

reduces the association complexity by removing unlikely association pairs.
- Because the residual is Gaussian, the Mahalanobis distance follows a

$\chi^2$

distribution.
- A measurement lies inside a track's gate if the Mahalanobis distance is smaller than the threshold calculated from the inverse cumulative

$\chi^2$

distribution as follows:

$$d\left(\mathbf x,\mathbf z\right)\leq F_{\chi^2}^{-1}\left(0.995|\dim_{\mathbf z}\right)$$

- If a measurement lies outside a track's gate, we can set the distance to infinity, for example:

$$\mathbf A = \begin{pmatrix}
d(1, 1) & \infty &\infty \\
d(2, 1) & d(2, 2) &d(2, 3) \\
d(3, 1) & d(3, 2) &d(3, 3) \\
\infty& d(4, 2) &d(4, 3)
\end{pmatrix}$$
