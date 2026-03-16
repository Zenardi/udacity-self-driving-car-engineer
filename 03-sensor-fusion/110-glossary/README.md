# Glossary

> Part of: **Extended Kalman Filters**

## Additional Content

* **$\mathbf{x}$ (State Vector):** Contains information about the position and velocity of the object being tracked:

$$\mathbf{x} = \begin{pmatrix} p_x \\ p_y \\ p_z \\ v_x \\ v_y \\ v_z \end{pmatrix}$$


* **$\mathbf{P}$ (Estimation Error Covariance Matrix):** Contains information about the uncertainty of the object's position and velocity.
* **$k$ (Time Step Index):** Refers to the specific point in time. Thus, $\mathbf{x}_k$ is the state vector at time $t_k$.
* **$\Delta t$ (Time Step):** The time interval between two consecutive measurements.
* **$\mathbf{x}_k^-$ and $\mathbf{P}_k^-$ (Predicted State/Covariance):** Refers to the state and covariance predicted by the model before the measurement update.
* **$\mathbf{x}_k^+$ and $\mathbf{P}_k^+$ (Updated State/Covariance):** Refers to the state and covariance after the measurement innovation has been applied.
* **$f$ (State Transition Function):** In the linear case, this is the matrix $\mathbf{F}$ (System Matrix). it defines how to transition from one timestamp to the next:

$$\mathbf{x}_k = f(\mathbf{x}_{k-1}) + \nu = \mathbf{F}\mathbf{x}_{k-1} + \nu$$


* **$\nu \sim \mathcal{N}(0, \mathbf{Q})$ (Process Noise):** Zero-mean noise with covariance $\mathbf{Q}$, representing model uncertainty.
* **$h$ (Measurement Function):** In the linear case, this is the matrix $\mathbf{H}$. It relates the state $\mathbf{x}$ to the measurement $\mathbf{z}$:

$$\mathbf{z}_k = h(\mathbf{x}_k) + \omega = \mathbf{H}\mathbf{x}_k + \omega$$


* **$\omega \sim \mathcal{N}(0, \mathbf{R})$ (Measurement Noise):** Zero-mean noise with covariance $\mathbf{R}$, representing sensor uncertainty.
* **$\mathbf{z}$ (Measurement Vector):** For a Lidar sensor, it contains the position measurements:

$$\mathbf{z} = \begin{pmatrix} p_x \\ p_y \\ p_z \end{pmatrix}$$


* **$\gamma$ (Residual):** The innovation $\gamma = \mathbf{z} - \mathbf{H}\mathbf{x}$ with covariance $\mathbf{S} = \mathbf{H}\mathbf{P}\mathbf{H}^T + \mathbf{R}$.
* **$\mathbf{K}$ (Kalman Gain):** Weights the prediction against the measurement: $\mathbf{K} = \mathbf{P}\mathbf{H}^T\mathbf{S}^{-1}$.
* **$(c_i, c_j)$ and $(f_i, f_j)$:** Image center (principal point) and focal length in image coordinates, derived from intrinsic camera calibration.

---

### Coordinate Transformations

* **Rotation and Translation:** The $3 \times 3$ rotation matrix $\mathbf{M}_{\text{rot}}$ and 3D translation vector $\mathbf{t}$ convert from sensor to vehicle coordinates:

$$\begin{pmatrix} p_x \\ p_y \\ p_z \end{pmatrix} = \mathbf{M}_{\text{rot}} \cdot \begin{pmatrix} z_1 \\ z_2 \\ z_3 \end{pmatrix} + \mathbf{t}$$


* **Transformation Matrix (Homogeneous):** Converts from sensor to vehicle coordinates using a single matrix operation:

$$\begin{pmatrix} p_x \\ p_y \\ p_z \\ 1 \end{pmatrix} = \mathbf{T}_{\text{sens2veh}} \cdot \begin{pmatrix} z_1 \\ z_2 \\ z_3 \\ 1 \end{pmatrix} = \left( \begin{array}{ccc|c} & \mathbf{M}_{\text{rot}} & & \mathbf{t} \\ \hline 0 & 0 & 0 & 1 \end{array} \right) \cdot \begin{pmatrix} z_1 \\ z_2 \\ z_3 \\ 1 \end{pmatrix}$$


* **Inverse Transformation:** The matrix $\mathbf{T}_{\text{veh2sens}}$ is the inverse of $\mathbf{T}_{\text{sens2veh}}$.
