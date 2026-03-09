# More on Process Models

> Part of: **Prediction**

## Additional Content

Later in the lesson I'm going to ask you to read a paper titled ["A comparative study of multiple-model algorithms for maneuvering target tracking"](https://d17h27t6h515a5.cloudfront.net/topher/2017/June/5953fc34_a-comparative-study-of-multiple-model-algorithms-for-maneuvering-target-tracking/a-comparative-study-of-multiple-model-algorithms-for-maneuvering-target-tracking.pdf) but for now I'd like you to take a look at **section 3.1 and 3.2 only**. This section, titled MM Tracking Algorithms' Design, discusses the 9 process models used in the earlier part of the paper. 

Before you read the section, I'll explain some of the uncommon notation you will see.

### Notes on Notation
#### 1. Matrix Notation
When you see something like the following:

$$F_{CV} = \text{diag}[F_2, F_2], 
 F_2 = \begin{bmatrix}
1 & T \\ 
0 & 1 
\end{bmatrix}$$

it means that

$F$

is a 4x4 matrix, with

$F_{2_{}}$

as blocks along the diagonal. Written out fully, this means:

$$F_{CV} =  \begin{bmatrix}
1 & T & 0 & 0\\ 
0 & 1 & 0 & 0 \\
0 & 0 & 1 & T \\
0 & 0 & 0 & 1
\end{bmatrix}$$

#### 2. State Space
The process models all use cartesian coordinates. The state space is

$$\mathbf{x} = \begin{bmatrix}
x\\ 
\dot{x} \\
y \\
\dot{y}
\end{bmatrix}$$

#### 3. Variables
The equation

$x_{k} = Fx_{k-1} + Gu_{k-1} + Gw_k, \ \ w_k \sim \mathcal{N}(0,Q)$

should be read as follows:
> the **predicted state at time k** (

$x_{k_{}}$

) is given by **evolving** (

$F$

) the **previous state** (

$x_{k-1_{}}$

), **incorporating** (

$G$

) the **controls** (

$u_{k-1_{}}$

) given at the previous time step, and **adding normally distributed noise** (

$w_k$

).

## The Paper
You can find the paper here: [A comparative study of multiple-model algorithms for maneuvering target tracking](https://d17h27t6h515a5.cloudfront.net/topher/2017/June/5953fc34_a-comparative-study-of-multiple-model-algorithms-for-maneuvering-target-tracking/a-comparative-study-of-multiple-model-algorithms-for-maneuvering-target-tracking.pdf)
#### Supporting Materials
*

[A comparative study of multiple-model algorithms for maneuvering target tracking](https://video.udacity-data.com/topher/2017/June/5953fc34_a-comparative-study-of-multiple-model-algorithms-for-maneuvering-target-tracking/a-comparative-study-of-multiple-model-algorithms-for-maneuvering-target-tracking.pdf)
