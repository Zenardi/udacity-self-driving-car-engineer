# Coordinate Transforms

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ySZgVl-bNBo)

## Summary

**README: Extended Kalman Filter (EKF) and Sensor Coordinate Systems**

The EKF is a mathematical algorithm used for estimating the state of a system from noisy measurements. This README provides an overview of the key concepts covered in the lesson, including sensor coordinate systems and the transformation of measurements between different coordinate frames.

**Key Concepts**

* **Sensor Coordinate Systems**: Each sensor has its own coordinate system centered at the sensor's mounting position, with its own x-axis orientation (e.g., left or right).
* **Vehicle Coordinate System**: The vehicle coordinate system is a right-handed coordinate system centered at the center of the rear axle, with x-axis pointing forward, y-axis to the left, and z-axis upward.
* **Transformation Matrix T**: A four-by-four matrix that combines translation and rotation in one step, avoiding errors due to the order of transformation.
* **Homogeneous Coordinates**: Adding a fourth component (1) to the measurement vector to enable single matrix multiplication for transformation.
* **Rotation Matrix M**: A three-by-three matrix calculated using trigonometric functions (cosine and sine) to rotate vectors between coordinate frames.

**Practical Notes**

* To transform measurements from sensor coordinates to vehicle coordinates, use the transformation matrix T with homogeneous coordinates.
* The order of transformation is crucial; combining translation and rotation in one step (T) avoids errors due to incorrect ordering.
* In an example, a lidar sensor was located 4 meters in front of the rear axle, rotated 45 degrees to the left. The corresponding transformation matrix T was derived using sample values for rotation angle and translation vector.

Note: This README is a summary of the key concepts covered in the lesson, intended as a reference for future use or review.

## Transcript

Well done. You have completed the extended Kalman filter concepts. There is one final topic left that we need to cover in order to implement an EKF with several sensors. In a self-driving car, there are many different sensors at different mounting positions and viewing angles. Each sensor usually has its own coordinate system centered at the sensor's mounting position.

In this image, you can see the sensors used in the Rameau open dataset. The red arrows depict the x-axis of the different sensor coordinate systems. For example, we have a side lidar where the x-axis points to the left and another one where the x-axis points to the right. Both coordinate systems have different origins. All measurements from the different sensors have to be combined in the EKF.

The EKF tracks objects in vehicle coordinates. The vehicle coordinate system is usually centered at the center of the rear axle. The x-axis points forward, the y-axis points to the left, and the z-axis points upward. It is a right-handed coordinate system. So you can remember the directions using your right-hand fingers.

Take a moment now to try it out with your right hand. The thumb points forward, the index finger points left, and the middle finger points upward. Now imagine we have a lidar sensor mounted at the front bumper that looks to the left-hand side of the vehicle. As mentioned, the EKF tracks everything in vehicle coordinates. We have to find a method to transform the measurements z from lidar coordinates to vehicle coordinates and vice versa.

The lidar coordinate system has its origin at the mounting position of the lidar and the x-axis points to the left-hand side of the vehicle. The two origins differ by a translation t, and the lidar coordinate system is rotated by the angle Phi compared to the vehicle coordinate system. Therefore, to convert z from lidar to vehicle coordinates, we can first rotate it by a rotation matrix M, and then add the translation vector t. However, this calculation is error-prone because the order of transformation is relevant. If we first translate and then rotate, the result is a different one.

In order to avoid this error source, we can combine translation and rotation in one four by four transformation matrix T. We use the measurement vector z in homogeneous coordinates by adding the fourth component 1. Multiplication with t leads to the position in homogeneous vehicle coordinates. We simply have to delete the last component 1 in the vector, and we have calculated our desired result with single matrix multiplication. How does T look like?

The transformation matrix T simply consists of the three by three rotation matrix M, followed by the translation vector lowercase t. The last row consists of zeros and a one. Take a moment to verify that the result is really the same as applying the rotation and translation step-by-step. Now let's derive a concrete transformation matrix together in an example. Say the lidar is located four meters in front of the rear axle, which is the origin of the vehicle coordinate system.

The lidar is rotated around Phi equals 45 degrees to the left, which is 0.7 in radians. The rotation matrix M can be calculated using the cosine of Phi and the sine of Phi. There is no rotation in z. Therefore, the third column only contains zeros and a one. The last column of the transformation matrix contains the translation vector.

Substituting the variables with the sample values, we get this transformation matrix. Now it's your turn. In the following quiz, I want you to transform a measurement to vehicle coordinates with this transformation matrix.

## Additional Content

## Coordinate Transforms

Aqui está o conteúdo da imagem convertido para Markdown, utilizando LaTeX para as fórmulas matemáticas conforme solicitado:

---

* A matriz de rotação $3 \times 3$ $\mathbf{M}_{\text{rot}}$ e o vetor de translação 3D $\mathbf{t}$ convertem das coordenadas do sensor para as coordenadas do veículo:

$$\begin{pmatrix} p_x \\ p_y \\ p_z \end{pmatrix} = \mathbf{M}_{\text{rot}} \cdot \begin{pmatrix} z_1 \\ z_2 \\ z_3 \end{pmatrix} + \mathbf{t}$$

* No entanto, a ordem de aplicação da rotação e da translação é importante aqui, portanto, esta conversão é propensa a erros.

Melhor utilizarmos a seguinte transformação:

* A **Matriz de Transformação** converte das coordenadas do sensor para as coordenadas do veículo usando **coordenadas homogêneas**:

$$\begin{pmatrix} p_x \\ p_y \\ p_z \\ 1 \end{pmatrix} = \mathbf{T}_{\text{sens2veh}} \cdot \begin{pmatrix} z_1 \\ z_2 \\ z_3 \\ 1 \end{pmatrix} = \left( \begin{array}{ccc|c} & \mathbf{M}_{\text{rot}} & & \mathbf{t} \\ \hline 0 & 0 & 0 & 1 \end{array} \right) \cdot \begin{pmatrix} z_1 \\ z_2 \\ z_3 \\ 1 \end{pmatrix} = \begin{pmatrix} r_{11} & r_{12} & r_{13} & t_1 \\ r_{21} & r_{22} & r_{23} & t_2 \\ r_{31} & r_{32} & r_{33} & t_3 \\ 0 & 0 & 0 & 1 \end{pmatrix} \cdot \begin{pmatrix} z_1 \\ z_2 \\ z_3 \\ 1 \end{pmatrix}$$

* **Exemplo:** Em um veículo onde um sensor está localizado a **4m** à frente do eixo traseiro (= origem do sistema de coordenadas do veículo) e rotacionado $\phi = 0.7 (\approx 45^\circ)$ para a esquerda, temos a seguinte matriz de transformação:

$$\mathbf{T}_{\text{sens2veh}} = \left( \begin{array}{ccc|c} & \mathbf{M}_{\text{rot}} & & \mathbf{t} \\ \hline 0 & 0 & 0 & 1 \end{array} \right) = \begin{pmatrix} \cos(\phi) & -\sin(\phi) & 0 & t_1 \\ \sin(\phi) & \cos(\phi) & 0 & t_2 \\ 0 & 0 & 1 & t_3 \\ 0 & 0 & 0 & 1 \end{pmatrix} = \begin{pmatrix} 0.7 & -0.7 & 0 & 4 \\ 0.7 & 0.7 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}$$

* A matriz de transformação $\mathbf{T}_{\text{veh2sens}}$ de coordenadas do veículo para o sensor é a matriz inversa de $\mathbf{T}_{\text{sens2veh}}$.

