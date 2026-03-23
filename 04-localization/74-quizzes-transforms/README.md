# Quizzes: Transforms

> Part of: **Creating Scan Matching Algorithms**

## Additional Content

## Quizzes: Transforms

A pose can be a position, which in 2D consists of a position $(x,y)$ and orientation $\theta$ (theta), in reference to the global coordinate system. An example of a pose vector is $< 1, 2, π/6 >$ with a position at $(1,2)$ and an orientation of $30 \degree$. 

A pose offset can also be a representation of a delta in $x, y, \theta$ in reference to the local coordinate system, this is then a transformation that provides movement information. For instance take the pose offset $< \Delta 1, \Delta 1, \Delta π/6>$. This delta pose represents your transformation, how the object has moved with its $x, y, \theta$ values in reference to its local coordinate frame.

If you want to calculate where the robot is after starting with pose $< 1, 2, π/6 >$ and then getting a pose transform of $< \Delta 1, \Delta 1, \Delta π/6>$ , you first need to convert these vectors into transformation matrices. In 2D these transformation matrices are 3 x 3, and contain rotation and translation. 

The matrix transformation form is $[ [ R T ], [ 0, 1] ]$ where $R$ is the rotation matrix and $T$ is the translation. In 2D the rotation matrix is 2 x 2 and is calculated from $\theta$ , the orientation. The translation matrix in 2D is 2 x 1 and contains the x and y offsets. To get a good idea of how the rotation matrix works, [check out this great reference link](https://academo.org/demos/rotation-about-point/).

Once pose $< 1, 2, π/6 >$ is converted to transformation matrix $T_1$ and the pose transform $< \Delta 1, \Delta 1, \Delta π/6>$ is converted to transformation matrix $T_2$ , finding the new position and orientation is simply the matrix multiplication of $T_1 * T_2$ . Then that resulting transformation will contain the robot's new $x, y$ position and $\theta$ orientation. That transform matrix could then be converted into a pose vector, which makes it easy to read the new values.

If you had additional transformations after $T_2$ , say $T_3, T_4...T_{100}$ , you could still just multiply them all together to get the final position and orientation. Transformation matrices make it easy to keep track of where the robot is with just matrix multiplication. This first quiz tests how a transformation matrix can decode a translation $(x, y)$ and a rotation $\theta$ . If you get stuck, check out this link that shows [how translation and rotation come together inside a matrix](http://planning.cs.uiuc.edu/node99.html).

In this next quiz you are transforming a single point without orientation. Since the input point doesn't have orientation, you can just multiply the transformation matrix (3 x 3) with the input point including the homogeneous coordinate $< 1, 1, 1>$ (3 x 1). The output from this is (3 x 1) and the first element is the new $x$ , the second the $y$ , and third the homogeneous coordinate $1$.


In this next quiz, you want to track position, which includes orientation. To track orientation, make sure to convert all poses to a 3 x 3 transformation matrix, which includes rotation. Then, multiply matrices to track how the object moves. For a great reference, [check out this link](https://www.desmos.com/calculator/1g03usuyxl); the first step position is already calculated for you.

