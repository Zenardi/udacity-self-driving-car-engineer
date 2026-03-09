# Exercise: Jacobian

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Jj9GVLarwvs)

## Summary

**Nonlinear Camera Measurement Function and Jacobian**

This README file summarizes the key concepts and practical steps for implementing a nonlinear camera measurement function `h` and its Jacobian `h_j` in a camera class.

### Key Concepts

* **Nonlinear measurement function h**: A two-dimensional column vector that represents the measurement of a state `x` by a camera.
* **Jacobian h_j**: A 2x6 NumPy matrix that represents the partial derivatives of the nonlinear measurement function with respect to the state `x`.
* **Principal point c** and **focal length f**: Predefined parameters in the camera class that affect the measurement function.
* **Error handling**: Division by zero is not allowed, and an error message should be printed instead.

### Practical Notes

To implement the nonlinear measurement function `h` and its Jacobian `h_j`, follow these steps:

1. Implement the `get_hx` function to calculate the nonlinear measurement function for a given state `x`. The function should return a two-dimensional column vector.
2. Implement the `get_H` function to calculate the Jacobian at the current state `x`. The function should return a 2x6 NumPy matrix.
3. Use the `plot` functionality in the script to visualize the nonlinear measurement function and its linear approximation (tangent) at the green extension point `x`.

Note: Make sure to handle division by zero errors correctly in both functions.

## Transcript

In this exercise, I want you to implement the nonlinear camera measurement function h and the Jacobian h j. I have prepared a camera class for you with a predefined focal length f and principal point c. In the function get_hx, I want you to implement the nonlinear measurement function h and return h of x for the input state x. The function should return a two-dimensional column vector with the result. Make sure to not divide by zero, but print an error instead.

In the get_H function, I want you to calculate the Jacobian at the current state x. The function should return a two by six NumPy matrix. Again, make sure to not divide by zero. The remainder of the script contains plot functionality. If I run the script, the first and second component of the nonlinear measurement function h should be plotted in the two subplots.

As you can see here, they are not implemented yet. Once you have implemented everything correctly, the linear approximation uppercase H should be plotted as tangent to the nonlinear measurement function lowercase h at the green extension point x. Now it's your turn.

## Additional Content

## Exercise: Jacobian
### Derivation of

$\mathbf H_J$

Here is the complete derivation of the Jacobian

$\mathbf H_J$

for camera measurements. Don't worry if you can't follow every step in detail, it is more important to understand the overall idea of linearization and to be able to implement the resulting Jacobian. Remember that projecting our 6D state vector to 2D image space gives the following nonlinear camera measurement function:

$$h(\mathbf{x}) =
h\left(\begin{pmatrix}
p_x\\
p_y\\
p_z\\
v_x\\
v_y\\
v_z
\end{pmatrix}\right) =
\large \begin{pmatrix}
c_i-\frac{f_i\cdot p_y}{p_x}\\
c_j-\frac{f_j\cdot p_z}{p_x}
\end{pmatrix} =
\begin{pmatrix}
h_1(\mathbf x)\\
h_2(\mathbf x)
\end{pmatrix}$$

We are therefore looking for a 2x6 Jacobian

$\mathbf H_J$

:

$$\mathbf H_J =
\Large \begin{pmatrix}
\frac{\partial h_1(\mathbf x)}{\partial p_x}&
\frac{\partial h_1(\mathbf x)}{\partial p_y}&
\frac{\partial h_1(\mathbf x)}{\partial p_z}&
\frac{\partial h_1(\mathbf x)}{\partial v_x}&
\frac{\partial h_1(\mathbf x)}{\partial v_y}&
\frac{\partial h_1(\mathbf x)}{\partial v_z}\\
\frac{\partial h_2(\mathbf x)}{\partial p_x}&
\frac{\partial h_2(\mathbf x)}{\partial p_y}&
\frac{\partial h_2(\mathbf x)}{\partial p_z}&
\frac{\partial h_2(\mathbf x)}{\partial v_x}&
\frac{\partial h_2(\mathbf x)}{\partial v_y}&
\frac{\partial h_2(\mathbf x)}{\partial v_z}
\end{pmatrix}$$

We can calculate all entries of

$\mathbf H_J$

as follows:

$$\frac{\partial h_1(\mathbf x)}{\partial p_x} = \partial p_x \left(c_i-\frac{f_i\cdot p_y}{p_x}\right) = \frac{f_i\cdot p_y}{p_x^2}$$

$$\frac{\partial h_1(\mathbf x)}{\partial p_y} =  \partial p_y \left(c_i-\frac{f_i\cdot p_y}{p_x}\right) = -\frac{f_i}{p_x}$$

$$\frac{\partial h_1(\mathbf x)}{\partial p_z} =  \partial p_z \left(c_i-\frac{f_i\cdot p_y}{p_x}\right) = 0$$

$$\frac{\partial h_2(\mathbf x)}{\partial p_x} = \partial p_x \left(c_j-\frac{f_j\cdot p_z}{p_x}\right) = \frac{f_j\cdot p_z}{p_x^2}$$

$$\frac{\partial h_2(\mathbf x)}{\partial p_y} =   \partial p_y \left(c_j-\frac{f_j\cdot p_z}{p_x}\right) = 0$$

$$\frac{\partial h_2(\mathbf x)}{\partial p_z} =  \partial p_z\left(c_j-\frac{f_j\cdot p_z}{p_x}\right) = -\frac{f_j}{p_x}$$

Further, all derivatives after velocity components are zero, because velocity is not used in the measurement function.
Summing it up, our Jacobian

$\mathbf H_J$

is:

$$\mathbf H_J =
\large \begin{pmatrix}
 \frac{f_i\cdot p_y}{p_x^2}   &
-\frac{f_i}{p_x} &
0&
0&
0&
0\\
\frac{f_j\cdot p_z}{p_x^2}    &
0&
 -\frac{f_j}{p_x} &
0&
0&
0
\end{pmatrix}$$

Now it is your turn! Please implement the camera measurement function

$h(x)$

and the Jacobian

$\mathbf H_J$

in the exercise below.
