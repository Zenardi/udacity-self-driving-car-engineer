# ICP Alignment Overview

> Part of: **Utilizing Scan Matching**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=-Xu6hy3okhE)

## Summary

**Applying Scan Matching with 3D Scans**
=====================================

This section introduces applying scan matching using Iterative Closest Point (ICP) algorithm with 3D scans. The key concepts covered include transformation matrices, rotation and translation, and how they are applied in the ICP algorithm.

### Key Concepts

* **Transformation Matrix**: A matrix that represents a 3D transformation, consisting of six degrees of freedom: three for translation (xyz) and three for rotation (roll, pitch, yaw).
* **Rotation Matrix**: A 3x3 matrix representing rotation around the x, y, and z axes.
* **Translation Vector**: A 1x3 vector representing translation in the xyz space.
* **Homogeneous Row**: An additional row added to the transformation matrix for homogeneous coordinates.
* **ICP Algorithm**: An algorithm that iteratively refines the transformation between two point clouds by minimizing the distance between corresponding points.

### Practical Notes

When working with 3D scans and ICP, you will need to create a transformation matrix using specific yaw, pitch, and roll values. This can be done by plugging in these values into the rotation matrix and multiplying them together to get the final rotation matrix. Additionally, when applying ICP, you will work with 6 degrees of freedom for your transformation matrix.

The equations used in ICP also change slightly when working with 3D scans, but the overall process remains similar to the 2D case. The k-d tree used in PCL is able to handle any dimension, so you don't need to worry about changing its implementation.

## Transcript

Welcome to this section where we're talking about applying scan matching. Here we're talking about using ICP and now with 3D scans. Let's see how this is done. Before in the 2D case, we're dealing with this transform, that was this x, y, Theta. We'll now, we have six degrees of freedom.

We have this translation, that's xyz, and we also have this rotation that's roll, pitch, and yaw. Our transformation matrix still has the same form where there's the rotation, translation, and this homogeneous row and now it looks like this, where we have a three by three rotation matrix that's all filled out and that three by one translation. Here's the different parts for roll, pitch, and yaw also displayed over here. Now if you're just looking at everything from the top-down perspective, you'd just see this rotation around the z and that's your yaw. This order look familiar here that was rotation matrix there working before in 2D.

We'll now we have these extra ones for a pitch and roll. Imagine if this is our car, the pitch is coming across the y. That's like if you're driving up a hill, you'd see some pitch and then that roll let's imagine you're on this bridge and its windy. You might get some roll coming across there. But here's a different matrices for these.

Now let's say you wanted to create a transformation matrix using a specific yaw pitch and roll. You could just plug it in here and so you could put in your roll data part in here. Let's say near the pitch part, you could do the same here in a yaw, and then multiply them all together to get the final rotation matrix. Yes, now in ICP, we're working with of all these six degrees of freedom for our transformation matrix. Not too far of a stretch from last time, just have these additional pieces here.

But let's see how this modifies some of those equations here. Well, not too big of a difference if you remember ICP and creating it came down to these centered vectors that we're lining up together in these corresponding x and y matrices. Well now the center vectors have three parts that xyz offset. That'll make x and y three by n, where n is the number of source points. If we look at that then S will become three-by-three.

U and V will also be three-by-three. Then that rotation, as we expect is three-by-three, and that middle part, we're using that diagonal matrix is three by three, it's 1, 1. Then that last element that's calculated the same as it was in 2D. Also the translation here is now three by one. The centroids are a three by one, three by three by three by one.

That's how those change. But yes, overall, it's still very similar to the 2D case with just this extra part here and the transformation. The k-d tree is quite similar as well. You'll be using the PCL k-d tree. It's able to deal with any dimension in there.

So you don't have to worry too much about that. Just the ordering changes, but yeah, that's it for working with 3D scans in the ICP case.

## Additional Content

## ICP Alignment Overview
* In 3D, there are six degrees of freedom

translation and

rotation. The transformation matrix becomes:

$T = 
\begin{Bmatrix}
   R & R & R & t \\
   R & R & R & t \\
   R & R & R & t \\
   0 & 0 & 0 & 1
\end{Bmatrix}$

* For ICP in 3D, matrices are now 3x3 instead of 2x2 for

$U, V, R$

, and 3x1 instead 2x1 for translation

$t$

.
* ICP in 3D is still very similar to the 2D case
### Roll, Pitch and Yaw Equations

**Roll**

$R_x(\theta) = 
\begin{bmatrix}
   1 & 0 & 0 \\
   0 & \cos\theta & -\sin\theta \\
   0 & \sin\theta & \cos\theta
\end{bmatrix}$

**Pitch**

$R_x(\theta) = 
\begin{bmatrix}
   \cos\theta & 0 & \sin\theta \\
   0 & 1 & 0 \\
   -\sin\theta & 0 & \cos\theta
\end{bmatrix}$

**Yaw**

$R_x(\theta) = 
\begin{bmatrix}
   \cos\theta & -\sin\theta & 0 \\
   \sin\theta & \cos\theta & 0 \\
   0 & 0 & 1
\end{bmatrix}$
