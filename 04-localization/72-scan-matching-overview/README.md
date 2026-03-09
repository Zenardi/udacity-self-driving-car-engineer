# Scan Matching Overview

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=-cksfxKoqzg)

## Summary

**Scan Matching for Localization**
=====================================

**Introduction**

Scan matching is a technique used in robotics to recover the offset position (delta d) between two scans taken by a LiDAR sensor. This allows for accurate localization of a vehicle even after it has moved away from its initial position.

**Key Concepts**

* **Scan Matching**: A process that takes two scans and finds the transform that best overlaps them, recovering the delta d vector.
* **Iterative Process**: Scan matching is done in an iterative manner, where each scan is used as either the target or source scan to recover the delta d vector.
* **Transforms**: Transforms are represented as vectors (delta x, delta y, and delta Theta) that can be applied to change a point's position and orientation.
* **Transformation Matrix**: A mathematical representation of a transform, where the top left is the rotation matrix and the right column is the translation.
* **ICP (Iterative Closest Point)**: An algorithm used for scan matching that iteratively finds the best transform to align the source and target scans.

**Practical Notes**

* To implement scan matching using ICP, you need to:
	+ Associate each source point with its closest target point
	+ Calculate the transformation that minimizes the sum of association line segment distances
	+ Repeat the process until the source and target points overlap

Example code for calculating a transformation matrix in 2D space:
```python
import numpy as np

def calculate_transformation_matrix(delta_theta, delta_x, delta_y):
    rotation_matrix = np.array([[np.cos(delta_theta), -np.sin(delta_theta)],
                                [np.sin(delta_theta), np.cos(delta_theta)]])
    translation_vector = np.array([delta_x, delta_y])
    transformation_matrix = np.eye(3)
    transformation_matrix[:2, :2] = rotation_matrix
    transformation_matrix[:2, 2] = translation_vector
    return transformation_matrix

# Example usage:
delta_theta = 0.5
delta_x = 3
delta_y = 5
transformation_matrix = calculate_transformation_matrix(delta_theta, delta_x, delta_y)
print(transformation_matrix)
```
Note: This is a simplified example and actual implementation may vary depending on the specific requirements of your project.

## Transcript

Let's get started by talking about scan matching. In scan matching, we have our car with it's Lidar sensor that's using the scan, the environment. Then the car moves a little bit and scans environment again. If we look at these two scans side-by-side, we can see that they're very similar. The blue scan was the first scan that the car took at time t, and at time t plus 1, the car took the red scan.

Scan matching can allow us recover that offset position that the car moved. We'll call this our delta d. This will be our vector that's connecting the pose that the car is in when it went took its 1st scan, to the pose the car is in when it took the second scan. Scan matching will take these two scans and figure out what transform best overlaps the two and that will recover this delta d. For doing localization with scan matching, we're doing this in an iterative process.

At the very beginning, the car takes it's initial scan, drives a little bit and takes another scan, and then scan matching recovers as delta d. Next time, scan 1 is used as the target and then it drives a little bit. Scan 2 is used as the source, and then scan matching again recovers as delta d. Each time we have a target scan and the source scan and then scan matching gives us as delta d vector, and by stitching all those vectors together, all these transforms, we can see where the car is at even after it's driven really far away from the origin. We're talking about transforms here, and those were those delta ds in the previous slide.

One way to think about that is in this summarized notation here as a vector, which is this delta x, delta y, and delta Theta, so speaking in 2D terms. This is a transform that we could apply on a 2D point to change its position and orientation. The way that we can mathematically use this pose transform here, is represented as a transformation matrix. To do that, we have this form where, in the top left we have our rotation matrix and then over in the right column, we have the translation. We have this homogeneous coordinate here of 0s and 1.

In 2D space, the rotation matrix is going to be two-by-two, represented like this, so that delta Theta is from over here and pose and our translation, this is at delta x, delta y. Even in the transformation format, we can easily read off our delta x and delta y in that transformation matrix. Then down here, is an example of using transformation matrix to move a point. Let's say you have this point x, y, and you want to transform it. Let's say in our pose we had this delta Theta 0, delta x 3, and delta y 5, so we want to shift it 3 and 5, and then x and y, and we don't want to do any rotation on it, here's a transformation matrix that could represent that.

Right here we just have this rotation that's an identity because you're not doing any rotation here. We got this just by plugging in 0, in this part here, and then 3 and 5 are the offset. Then when we do a matrix multiplication with this x, y, we're using this homogeneous coordinate, so the transformation matrix has a homogeneous coordinate so does our input vector that we want to reposition with the transform. When we do this calculation, we see that we've effectively shifted x by 3 and y by 5 using this transformation. Now, let's talk about a way of doing scan matching, and that's with ICP.

ICP stands for Iterative Closest Point. We're talking about how we had this target scan, that's our reference that the car was taking, and then it moves a little bit and then it has this new scan, the source. ICP is going to figure out the transform that best aligns source with target. To begin with, it does this by doing associations. It looks at the closest point, so for each source point, it sees where its closest target point is, and we see this visually by these line segments.

You can see that some source points can actually share the same target point. They're all closest to this point. We have associations, and then what ICP does is this transformation on those associations. It basically finds the transformation that minimizes the sum of these line segment distances. Next, we do associations again, so you can see it's an iterative process.

ICP, Iterative Closest Point, so that's where the iterative part comes in, and so after those source points have moved from finding that best transform that we'll later talk about in this course, it's going to do associations again. You can see it has different associations than it did in the first place because the source points moved. You can see that this target points, for instance, is being shared with fewer source points, and now, even these target points here, have some associations with source points where they didn't before. Associations are being done again, the best transform is being calculated that minimizes the sum of all these association line segments, and then this process is repeated until eventually, the source and target points overlap with each other.

## Additional Content

## Scan Matching Overview
- Scan matching compares two very similar lidar scans to get a transformation in the movement
- You then stitch together the transforms to localize
- The transforms can be represented mathematically by a transformation matrix:

$T = 
\begin{Bmatrix}
   R & t \\
   0 & 1
\end{Bmatrix}$

where Rotation

$R$

, is given by:

$R = 
\begin{Bmatrix}
   \cos(\Delta\theta) & -\sin(\Delta\theta) \\
   sin(\Delta\theta) & \cos(\Delta\theta)
\end{Bmatrix}$

and Translation,

$T$

is:

$T = 
\begin{Bmatrix}
   \Delta x \\
   \Delta y
\end{Bmatrix}$

Accordingly, you may then notice the relation here to trigonometry with:

$X^\prime = x\cos(\Delta\theta) - y\sin(\Delta\theta)$

$Y^\prime = x\sin(\Delta\theta) + y\cos(\Delta\theta)$

ICP has a target scan and a source scan.

- Associations are made between the source points and target points
- A transform that minimizes the sum of association's distances is performed

Steps 1 and 2 repeat until associations don't change, and ICP has converged or a certain number of iterations have been done.
