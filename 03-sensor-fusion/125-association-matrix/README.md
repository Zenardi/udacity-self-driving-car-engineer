# Association Matrix

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=CMxDNXCMkPQ)

## Summary

**Mahalanobis Distance Matrix Association**
=============================================

This project involves calculating Mahalanobis distances between tracks and measurements, storing them in an association matrix `A`, and iteratively updating the matrix and lists of unassigned tracks and measurements until all associations are made.

**Key Concepts**

* **Mahalanobis distance**: a measure of similarity between two data points, taking into account their covariance.
* **Association matrix `A`**: an `N x M` matrix where `N` is the number of tracks and `M` is the number of measurements. Each entry in the matrix represents the Mahalanobis distance between a track and a measurement.
* **Unassigned tracks and measurements lists**: lists that keep track of tracks and measurements that have not yet been associated with each other.

**Practical Notes**

To implement this algorithm, you will need to:

* Initialize an `N x M` association matrix `A` where `N` is the number of tracks and `M` is the number of measurements.
* Iterate through the matrix, finding the minimum entry (i.e., the smallest Mahalanobis distance) at each step.
* Update the matrix by removing the row and column corresponding to the associated track and measurement.
* Remove the entries from the lists of unassigned tracks and measurements.
* Repeat this process until all associations are made.

Note that this algorithm is designed for a specific use case (track association in computer vision) and may need to be adapted or modified for other applications.

## Transcript

In the last video, we have learned that we need to calculate the Mahalanobis distances between all tracks and all measurements. But how should we store these distances? A matrix is the straightforward choice. We use the association matrix A to store all distances. In the case of N tracks and M measurements, A is an N by M matrix.

The row stands for the track and the column for the measurement number. Let's make a concrete example. Here we have four tracks and three measurements, so A is a 4-by-3 matrix. We also need to start the IDs of all unassigned tracks and unassigned measurements. First, we look for the minimum entry in A, which is the distance between tracks 3 and measurement 2.

We update track 3 with measurement 2. Since we do not want to update track 3 twice, we remove the third row from A. Similarly, we delete the second column in order to not use measurement 2 advice. Finally, we remove track 3 from the unassigned tracks list and measurement 2 from the unassigned measurements list. In the next step, we have only a three by two matrix A left.

Again, we find the smallest entry, which is in the second row and second column of A now. From the unassigned tracks, we see that the second row corresponds to track ID2. Likewise from the unassigned measurements list, we see that the second column corresponds to measurement ID3 because the second entry in the list is three. Therefore, we update track to with measurement 3. Then we remove the row and column from A and the entries from both lists.

In the last step, we have to tracks and one measurement left. We find the closest distance between track 2 and measurement 1, we delete the matrix column, and we delete both entries from the lists. Now, the association is finished because we have no measurements left to assign and A is empty. Track 4 remains as a false-negative track that was not detected by our lighter.

## Additional Content

## Association Matrix
- Say we hav $N tracks an $M measurements.
- Th $\textbf{association matrix} $\mathbf A is a $N\times M matrix that contains the Mahalanobis distances between each track and each measurement:

$$\mathbf A = \begin{pmatrix}
d(\mathbf x_1, \mathbf z_1) & d(\mathbf x_1, \mathbf z_2) &...&d(\mathbf x_1, \mathbf z_M)\\
\vdots &\vdots&&\vdots\\
d(\mathbf x_N, \mathbf z_1) & d(\mathbf x_N, \mathbf z_2) &...&d(\mathbf x_N, \mathbf z_M)
\end{pmatrix}$$

- We also need a list for unassigned tracks and a list for unassigned measurements. 
- We look for the smallest entry in A in order to determine which track to update with which measurement, then we delete this row and column from A and the track ID and measurement ID from the lists. We repeat this until A is empty.
