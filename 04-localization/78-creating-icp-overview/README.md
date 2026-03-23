# Creating ICP Overview

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=X1Vod66FVI0)

## Summary

**README: Implementing Iterative Closest Point (ICP) Algorithm**

The Iterative Closest Point (ICP) algorithm is a widely used technique for registering two point clouds by finding the optimal rigid transformation between them. This summary provides an overview of the key concepts and practical steps involved in implementing ICP.

### Key Concepts

* **KDTree**: A data structure that allows for efficient nearest neighbor searches, reducing the time complexity from O(N) to O(log N).
* **Nearest Neighbor Association**: The process of finding the closest point in the target point cloud to each source point.
* **Centroids**: The mean points of the source and target point clouds used as reference points for calculating centered vectors.
* **Centered Vectors**: Vectors from the centroids to each point in the association, used for aligning the two point clouds.
* **Singular Value Decomposition (SVD)**: A linear algebra technique used to decompose the matrix S into U and V matrices, which are then used to calculate the rotation and translation parts of the transformation matrix.

### Practical Notes

To implement ICP, follow these steps:

1. Create a KDTree from the target point cloud using a library such as PCL.
2. Loop through each source point and use the KDTree to find its closest point in the target point cloud (nearest neighbor association).
3. Calculate the centroids of the source and target point clouds.
4. Calculate centered vectors for each point in the associations by subtracting the centroid from each point.
5. Align the two point clouds using the centered vectors, represented as columns in a matrix X and Y.
6. Calculate the matrix S by multiplying X with Y transpose.
7. Perform SVD on S to obtain U and V matrices.
8. Use U and V to calculate the rotation and translation parts of the transformation matrix.

Note that this summary focuses on the 2D implementation of ICP, but the concepts can be extended to 3D point clouds as well.

## Transcript

Now, let's talk about creating ICP. We have a high-level overview of what ICP is doing. Let's go into the nitty-gritty of how to implement ICP itself. Before we're talking about associations, and this is how we're actually going to be calculating these associations, so we're going to do this nearest neighbor association. We want to do this as fast as possible and as efficient.

To do that, we're going to use a KDTree. We can take the point cloud target and use this KDTree. We can actually use the point cloud library KDTree structure to do this. Then that'll allow us, instead of searching for the closest point and big O of N where N is the total number of target points, we can do it in logarithmic time instead. That'll be the first step, is creating KDTree of target.

Then in a loop, go through all the different source points. You can imagine this radius that's spreading out. Then it's hitting a point and that'll be its association. It's calling a query on this KDTree to see what its closest target point is. So asks this point, "Hey, what's my closest point in this KDTree?" and it'll return it in this radius search.

One of the parameters is how far that radius can go until it gives up. Here it's relatively big, so it'll find something. But if it didn't, like say, this circle is only allowed to expand up to here and didn't get anything, then it just won't have association line segment that we'll be working with later. But here we can see that association to that target point. The next thing that is done again on this next point, so we see it's spreading out.

It hits its target point, that'll be its association. Each time looking in the KDTree you see what the closest point is and that process is repeated. From there, you can actually get this vector representation for all these associations if you're just working with the index points, imagine this is index 0, index 1, that could be your vector elements. Then each element will have this value of this index. Yes, it could be 01.

It's like, index 0 has this association 1. That's how these association line segments could be represented then. That's how the associations are done, and then that next part for ICP is finding that best transform that minimizes the sum of those association distances. In order to do that, these centroids are calculated. We have a centroid for target, which is just the mean of the points, and we have a centroid for source, which is again the mean of those points.

We have the two centroids and we can use those then to calculate the centered vectors. The centered vector then is starting at the centroid and going to the point. We can see each of these centered vectors here, so it's the total number of points. Then we're going to align this with the associations. We calculate the associations in the first step, and now we have these centered vectors for each point in the associations, and we can line those up.

We line it up in this format with this matrix. We see each of the centered vectors being represented by source and each one in its fellow column here is its associated centered vector from the target. These centered vectors, you can see 2D space, this is Delta X, Delta Y, which ends up being this column vector here. The total number of centered vectors for sources, the number of source points, so let's call that N. Then this is two by one, so it has two rows and just a single column.

This X is going to be two by N and same with Y, it's going to be two by N. These highlighted center vectors here, remember that some of the source points were actually sharing that same target point. So then these are all sharing the same target-centered vector then. We have them lining up like this. Then now it's just some linear algebra and doing some calculations.

We calculated X and Y. We can get S by doing this calculation here with X multiplied by Y transpose. This was two by N and then we transposing N by two. So S is going to be two by two. Then what you want to do is a singular value decomposition on S to get these matrices U and V.

Since S is two by two, U and V also end up being two by two. Once you have U and V, you have everything you need to calculate the rotation and translation parts of that overall transformation matrix. We can plug in U and V into the rotation. It's V times this diagonal matrix here, and this is two by two diagonal. That last element, the analysis determinant V times U transpose and then multiply by U transpose.

Overall, this is going to end up being two by two, which we would expect for 2D space rotation matrix because it's two by N and by two [inaudible] get two by two overall. Then also the translation here is calculated by using those beginning centroids that we're using. It's a target centroid minus the rotation matrix, multiply it by the source centroid. Then we have R and t and they can just be plugged in to the overall transformation matrix here. R is two by two, t is two by one.

Our overall transformation matrix is going to be four by four. Since we're in 2D space, notice that this is just one. We're not using that dimension. We just have our two-by-two rotation matrix fitted right here and our translation fitted right here. That's what ICP will return.

Then that moves the source points and then we can do the association steps over again and just repeat that process.

## Additional Content

## Creating ICP Overview
* To begin with ICP, we'll first use a nearest neighbor association to match points. For efficiency, we use a KD Tree on the target scan to quickly associate source points to target points. A KD Tree is a data structure that is similar to a binary tree, but helpful for points in a multi-dimensional space, such as a point cloud.
* Next, make associations into a matrix by using centered vectors and closest neighbors (from a radius search).
* Finally, perform a singular value decomposition (which factorizes matrices into singular vectors or values) on the association matrix to get rotation and translation on the source that minimizes association distances with target.
### ICP Equations

Here, the point is to go from the vectors adding up to total $X$ and $Y$ and get the Rotation $R$ and Translation $t$.

$S = XY^T$

$SVD(S) = U, V$

(the singular value decomposition)

$R = V({^1}_{det(VU^T)})U^T$

$t = c_T - Rc_S$

where $c_T$ and $c_S$ are the target and source centroids, respectively.

### Final Transformation Matrix

$T = 
\begin{Bmatrix}
   R &R & 0 & t \\
   R &R & 0 & t \\
   0 & 0 & 1 & 0 \\
   0 & 0 & 0 & 1
\end{Bmatrix}$
