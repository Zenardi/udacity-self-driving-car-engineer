# Glossary

> Part of: **Extended Kalman Filters**

## Additional Content

-

$\mathbf{ x}$

is the

$\textbf{state vector}$

. It contains information about position and velocity of the object that you are tracking:

$$\mathbf{ x} = \begin{pmatrix} p_x\\p_y\\p_z\\v_x\\v_y\\v_z\end{pmatrix}$$

-

$\mathbf P$

is the

$\textbf{estimation error covariance matrix}$

, which contains information about the uncertainty of the object's position and velocity. 
-

$k$

refers to the time step index. So

$x_k$

is the object's position and velocity vector at time

$t_k$

. 
-

$\Delta t$

is the

$\textbf{time step}$

between two consecutive measurements.
- The notation

$\mathbf x_k^-$

refers to the predicted state. The corresponding predicted covariance is denoted as

$\mathbf P_k^-$

.
-

$\mathbf x_k^+$

is the updated state after the measurement innovation. Similarly, the updated covariance is

$\mathbf P_k^+$

.
-

$f$

is the

$\textbf{state transition function}$

(in the linear case, it is a matrix

$\mathbf F$

, also called

$\textbf{system matrix}$

). It tells us how to get from one timestamp to the next:

$$x_k = f(x_{k-1})+\nu= \mathbf F x_{k-1}+\nu$$

-

$\nu \sim \mathcal{N}\left(0, \mathbf Q\right)$

is the zero-mean

$\textbf{process noise}$

with covariance

$\mathbf Q$

.
-

$h$

is the

$\textbf{measurement function}$

(in the linear case, it is a matrix

$\mathbf H$

). It tells us how state and measurement are related:

$$z_k = h(x_k)+\omega= \mathbf H x_k+\omega$$

-

$\omega \sim \mathcal{N}\left(0, \mathbf R\right)$

is the zero-mean

$\textbf{measurement noise}$

with covariance

$\mathbf R$

.
-

$\mathbf z$

is the

$\textbf{measurement vector}$

. For a lidar sensor, the

$\mathbf z$

vector contains the position measurements in

$x$

,

$y$

and

$z$

:

$$\mathbf z = \begin{pmatrix} p_x\\p_y\\p_z \end{pmatrix}$$

-

$\gamma = \mathbf z- \mathbf H\mathbf x$

is the

$\textbf{residual}$

with covariance

$\mathbf S = \mathbf H\mathbf P \mathbf H^T+\mathbf R$

.
-

$\mathbf K = \mathbf P \mathbf H^T\mathbf S^{-1}$

is the

$\textbf{Kalman gain}$

which weights prediction in comparison to measurement.  
-

$\left(c_i, c_j\right)$

is the

$\textbf{image center}$

or

$\textbf{principal point}$

in image coordinates, derived from intrinsic camera calibration.
-

$\left(f_i, f_j\right)$

is the

$\textbf{focal length}$

in image coordinates, derived from intrinsic camera calibration.
- The 3x3

$\textbf{rotation matrix}$

$\mathbf M_{\text{rot}}$

and 3D

$\textbf{translation vector}$

$\mathbf t$

convert from sensor to vehicle coordinates:

$$\begin{pmatrix}
p_x\\ p_y\\p_z
\end{pmatrix}
=
\mathbf M_{\text{rot}}
\cdot
\begin{pmatrix}
z_1\\ z_2\\z_3
\end{pmatrix}
+\mathbf t$$

- The

$\textbf{Transformation Matrix}$

converts from sensor coordinates to vehicle coordinates using

$\textbf{homogeneous coordinates}$

:

$$\begin{pmatrix}
p_x\\ p_y\\p_z\\1
\end{pmatrix}
=
\mathbf T_{\text{sens2veh}}
\cdot
\begin{pmatrix}
z_1\\ z_2\\z_3\\1
\end{pmatrix}
=
\left(\begin{array}{c|c}
{\large\mathbf M_{\text{rot}}}
  &  
{\large\text t}\\

 \overline{\begin{matrix}
0 &0&0
  \end{matrix}}  &
  \overline{\begin{matrix}
1
  \end{matrix}}
\end{array}\right)
\cdot
\begin{pmatrix}
z_1\\ z_2\\z_3\\1
\end{pmatrix}$$

- The transformation matrix

$\mathbf T_{\text{veh2sens}}$

from vehicle to sensor coordinates is the inverse matrix of

$\mathbf T_{\text{sens2veh}}$

.
