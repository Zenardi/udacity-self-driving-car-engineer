# Covariance Initialization

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=br--UGxDYxc)

## Summary

**Initializing Estimation Error Covariance Matrix P**

This README file provides an overview of initializing the estimation error covariance matrix **P**, a crucial component in state estimation algorithms.

### Key Concepts

* **Measurement covariance matrix R**: contains variances of measurement coordinates, represented as an ellipse with lengths determined by standard deviations.
* **Rotation matrix**: used to rotate the measurement covariance ellipse and derive the estimation error covariance for position coordinates.
* **Transpose operation**: required when multiplying the rotation matrix with the measurement covariance matrix to ensure correct calculation of the estimation error covariance.
* **Diagonal matrix P_vel**: initializes the velocity components' covariance matrix, reflecting high velocity and certainty at initialization.

### Practical Notes

To initialize the estimation error covariance matrix **P**, follow these steps:

1. Derive the position component's estimation error covariance by rotating the measurement covariance ellipse using the rotation matrix (and its transpose).
2. Initialize the velocity component's covariance matrix **P_vel** as a diagonal matrix with large values to reflect high velocity and certainty at initialization.

Note: The lesson provides additional information on why the transpose operation is necessary when multiplying the rotation matrix with the measurement covariance matrix.

## Transcript

Now, we have initialized the state X_0 based on the lighter measurement z. But we also have to initialize the corresponding estimation error covariance P_0. How can we do that? Remember that with the lighter measurement z, we also get a measurement covariance matrix are from the lidar sensor. Measurement covariance contains the variances of the three measurement coordinates.

R can be visualized as an ellipse where the length of the Xs is determined by the standard deviations in x and y. The estimation error covariance for the three-position coordinates can be found by rotating the ellipse, which means multiplying with the rotation matrix. Remember that R contains variances which are square values of the standard deviations. Therefore, we also have to multiply twice with the rotation matrix and its transpose. If you are interested in the details on why we have to use the transpose here, there are some explanations below this video.

The overall estimation error covariance consists of this derived matrix P_pos plus another three-by-three matrix for the velocity components. We already learned that we cannot measure the velocity with our lidar. Therefore the remaining three-by-three covariance matrix P_vel can simply be initialized by a diagonal matrix where we said large diagonal values to reflect the high velocity and certainty at initialization. This completes the initialization of the estimation error covariance matrix P.

## Additional Content

## Covariance Initialization
- The 3x3 Matrix for the position estimation error covariance $\mathbf P_{\text{pos}}$ can be initialized from the measurement covariance $\textbf R$ by rotating from sensor to vehicle coordinates:

$$\mathbf P_{\text{pos}}=
\mathbf M_{\text{rot}}\cdot \mathbf R \cdot \mathbf M_{\text{rot}}^T$$

- The 3x3 Matrix for the velocity estimation error covariance $\mathbf P_{\text{vel}}$ can be initialized with a diagonal matrix containing large diagonal values, since we cannot measure velocity and therefore have a huge initial velocity uncertainty. 
- The overall estimation error covariance can then be initialized as:

$$\mathbf P_0 = 
\left(\begin{array}{c|c}
\underline{\mathbf P_{\text{pos}}}
  &  
{0}\\

{0}  &
\overline{\mathbf P_{\text{vel}}}
\end{array}\right)$$

### Derivation of Covariance Rotation (Optional)

I promised less math for this lesson, so feel free to directly jump to the next page! In case you are interested though, here is the derivation of the rotation formula for the covariance. The measurement covariance $\textbf R$ is defined via the expectation value $E$ (see also the Wiki page on [Covariance Matrices](https://en.wikipedia.org/wiki/Covariance_matrix)):

$$\mathbf R = cov(\mathbf z) = E\left[(\mathbf z - E(\mathbf z))(\mathbf z - E(\mathbf z))^T\right]$$

Remember the measurement equation:

$$\mathbf z = h(\mathbf x)+\omega$$

where $\omega \sim \mathcal{N}\left(0, \mathbf R\right)$ is the zero-mean measurement noise with covariance $\mathbf R$. Since $\omega$ is zero-mean, the expectation value of $\mathbf z$ is simply $h(\mathbf x)$:

$$E(\mathbf z) = E(h(\mathbf x)+\omega) = h(\mathbf x)$$

This gives us:

$$\mathbf R = E\left[(\mathbf z - E(\mathbf z))(\mathbf z - E(\mathbf z))^T\right]$$

$$= E\left[(\mathbf h(\mathbf x)+\omega - E(h(\mathbf x)+\omega))(...)^T\right]$$

$$= E\left[(\mathbf h(\mathbf x)+\omega - h(\mathbf x))(...)^T\right]$$

$$= E\left[\omega \omega^T\right]$$

Now we want to rotate the measurement from sensor to vehicle coordinates, so we get (note that $(\mathbf A \mathbf B)^T =\mathbf B^T \mathbf A^T$):

$$\mathbf P_{\text{pos}} = E\left[\mathbf M_{\text{rot}}\omega \cdot(\mathbf M_{\text{rot}} \omega)^T\right]$$

$$= E\left[\mathbf M_{\text{rot}}\omega \omega^T\mathbf M_{\text{rot}} ^T\right]$$

$$= \mathbf M_{\text{rot}}E\left[\omega \omega^T\right]\mathbf M_{\text{rot}} ^T$$

$$=\mathbf M_{\text{rot}}\cdot \mathbf R \cdot \mathbf M_{\text{rot}}^T$$

A similar reasoning leads to many of the Kalman filter equations from the previous lessons. For example, if you want to go above and beyond, you could try to derive the reason for the covariance prediction:

$$\mathbf P^- = \mathbf F\mathbf P^+\mathbf F^T+\mathbf Q$$

or for the residual covariance:

$$\mathbf S = \mathbf H\mathbf P^+\mathbf H^T+\mathbf R$$
