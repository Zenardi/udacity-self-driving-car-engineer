# Glossary

> Part of: **The Lidar Sensor**

## Additional Content

## Terms and Symbols
In this section, you will find a list of abbreviations and technical expressions used in the lesson. For further details and an in-depth explanation, please refer to the respective sections.

- **LiDAR** : **Li**ght **D**etection **A**nd **R**anging.
- **Range** : Straight-line distance measured between sensor and obstacle.
- **Spatial resolution** : Measure of the smallest object that can be resolved by the sensor.
- **Object classification** : Sorting of objects into groups with each group having its own characteristic properties (e.g. vehicles, pedestrians).
- **Package** : Physical dimensions of a technical device (e.g. the housing of a sensor).
- **ToF** : Time-of-Flight
- **MEMS** : Micro-Electro-Mechanical Systems
- **FMCW** : Frequency-modulated continuous wave
- **FOV** : Field of view
- **Homogeneous coordinates** : Mathematical concept that allows operations such as translation, rotation, scaling and perspective projection to be implemented as matrix operations.
## Equations
**Range equation that delivers the distance to a target**:

$R = \frac{1}{2n}\cdot c \Delta t$

The range

$R$

is based on the *speed of light*

$c$

, the *time between light emission and reception*

$t$

and the *refractive index*

$n$

of the medium through which the light propagates. 

---

**LiDAR equation which describes the relationship between the power at the receiver and various characteristics of the technical setup and its physical surroundings**:

$P(R) = P_0\cdot \rho \cdot \frac{A_0}{\pi \cdot R^2}\cdot \eta_0 \cdot e^{-2\gamma R}$

-

$P(R)$

: **power received** 
-

$P_0$

: **peak power transmitted**
-

$\rho$

: **target reflectivity** 
-

$A_0$

: **receiver aperture area** 
-

$\eta_0$

: **transmission coefficient** 
-

$\gamma$

: **atmospheric extinction coefficient**

---

**Light propagation angle for optical phase arrays**:
-

$\alpha$

: Direction into which the light wave is deflected
-

$\lambda$

: Wavelength of the light
-

$\Phi$

: Phase difference  between the emitters
-

$d$

: Spatial difference  between the emitters

---
Converting

$x$

,

$y$

and

$z$

from yaw, pitch and roll angles:

$x = r_P \cdot \cos{\alpha_P} \cdot \cos{\beta_P}$

$y = r_P \cdot \sin{\alpha_P} \cdot \cos{\beta_P}$

$x = r_P \cdot \sin{\beta_P}$

-

$\alpha$

:  Yaw angle
-

$\beta$

: Pitch angle

---
**Extrinsic calibration matrix**:

$\begin{bmatrix}
R_{3x3} & T_{3x1} \\
0_{1x3} & 1
\end{bmatrix}$

The matrix

$R$

describes the rotation of the sensor around its three coordinate axes in relation to the superior coordinate system (e.g. the vehicle) while the vector

$T$

denotes the relative center of the coordinate system.
