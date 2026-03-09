# Glossary

> Part of: **Multi-Target Tracking**

## Additional Content

- We can define a simple

$\textbf{track score}$

by setting:

$$\text{score} = \frac{\#\text{detections in last $n$ frames}}{n}$$

- The

$\textbf{data association}$

assigns measurements to tracks and decides which track to update with which measurement.
- The

$\textbf{Mahalanobis distance}$

measures the squared distance between a track and a measurement, weighted with the covariance of the residual:

$$d(\mathbf x, \mathbf z)= \gamma^T\mathbf S^{-1}\gamma = (\mathbf z - h(\mathbf x))^T\mathbf S^{-1}(\mathbf z - h(\mathbf x))$$

- The

$\textbf{Simple Nearest Neighbor (SNN)}$

data association calculates all Mahalanobis distances between tracks and measurements, then iteratively updates the closest association pair.
- In the case of

$N$

tracks and

$M$

measurements, the

$\textbf{association matrix}$

$\mathbf A$

is an

$N\times M$

matrix that contains the Mahalanobis distances between each track and each measurement:

$$\mathbf A = \begin{pmatrix}
d(\mathbf x_1, \mathbf z_1) & d(\mathbf x_1, \mathbf z_2) &...&d(\mathbf x_1, \mathbf z_M)\\
\vdots &\vdots&&\vdots\\
d(\mathbf x_N, \mathbf z_1) & d(\mathbf x_N, \mathbf z_2) &...&d(\mathbf x_N, \mathbf z_M)
\end{pmatrix}$$

-

$\textbf{Gating}$

reduces the association complexity by removing unlikely association pairs. A measurement lies inside a track's gate if the Mahalanobis distance is smaller than the threshold calculated from the inverse cumulative

$\chi^2$

distribution as follows:

$$d\left(\mathbf x,\mathbf z\right)\leq F_{\chi^2}^{-1}\left(0.995|\dim_{\mathbf z}\right)$$

- The

$\textbf{Root Mean Square Error (RMSE)}$

calculates the residual between estimated state and ground truth state:

$$RMSE = \sqrt{\frac 1n\sum_{k=1}^n \left(x_k^{\text{est}}-x_k^{\text{true}}\right)^2}$$
