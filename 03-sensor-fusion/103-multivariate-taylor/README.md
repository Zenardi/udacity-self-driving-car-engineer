# Multivariate Taylor

> Part of: **Extended Kalman Filters**

## Additional Content

## Multivariate Taylor Series
Now that you’ve seen how to do a Taylor series expansion with a one-dimensional equation, we’ll need to look at the Taylor series expansion for multi-dimensional equations. Recall from the

$\textit{Camera Measurement Model}$

lecture that the

$h$

function is composed of two equations that show how the predicted state

$\mathbf x$

is mapped into the image space:

$$h(\mathbf{x}) =
h\left(\begin{pmatrix}
p_x\\
p_y\\
p_z\\
v_x\\
v_y\\
v_z
\end{pmatrix}\right) =
\Large \begin{pmatrix}
c_i-\frac{f_i\cdot p_y}{p_x}\\
c_j-\frac{f_j\cdot p_z}{p_x}
\end{pmatrix}$$

These are multi-dimensional equations, so we will need to use a multi-dimensional Taylor series expansion to make a linear approximation of the

$h$

function. Here is a general formula for the multi-dimensional Taylor series expansion:

$$h(x) \approx h(\mu) + \mathbf H_J(\mu) ( x - \mu)$$

Here we have simply replaced the first derivative

$h'(\mu)$

with the Jacobian matrix

$\mathbf H_J(\mu)$

. The Jacobian matrix contains the partial derivatives of the multi-dimensional function

$h$

.
