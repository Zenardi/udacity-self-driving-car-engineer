# Exercise: Association Matrix

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=boQlq9miHqA)

## Summary

**Association Metrics for Simple Association Problem**
=====================================================

This project involves implementing association metrics for a simple association problem with three tracks and three measurements. The goal is to calculate the Mahalanobis distances between each track and measurement, which will be used to populate an association matrix.

**Key Concepts**

* **Mahalanobis Distance**: A measure of distance between two points in multivariate space, taking into account the covariance of the data.
* **Association Matrix**: An N by M matrix where N is the number of tracks and M is the number of measurements. The matrix contains the Mahalanobis distances between each track and measurement.
* **Track Class**: A class representing a track with attributes `id`, `x` (position), and `p` (uncertainty).
* **Measurement Class**: A class representing a measurement with attributes `id`, `c` (position), and `r` (uncertainty).

**Practical Notes**

To implement the association metrics, you will need to:

1. Implement the `MHD` function to calculate the Mahalanobis distance between a track and a measurement.
2. Implement the `H` function to represent the measurement model for a 4D state vector and a 2D LiDAR measurement.
3. Initialize an N by M association matrix with infinity entries, where N is the number of tracks and M is the number of measurements.
4. Populate the association matrix with the calculated Mahalanobis distances using the `associate` function.

Note: The track state is already given in sensor coordinates, and the height component is neglected in this exercise.

## Transcript

I've got a programming assignment for you. Please, implement the association metrics for a simple association problem with three tricks and three measurements. The status script contains a class association with an empty association metrics. I want you to implement the function called associate. As input, it gets a track lists containing N track indices and a measurement list containing M measurement indices.

The association metrics is then initialized to an N by M matrix and we initialize the matrix components with infinity. Now please fill the association metrics with the respective Mahalanobis distances. To calculate these distances, please implement the MHD function below, that gets a track and the measurement as input and returns the MHD. You will also have to implement the measurement function H here for a 4D state vector and a 2D LiDAR measurement. We neglect the height in this exercise, as well as the transformation from vehicle to censor coordinates.

The track state is already given in sensor coordinates here. In the remainder of the script, you can see the track class with attributes id, x, and p, as well as the measurement class with attributes id, c and r in the main loop below, which generate three random tracks and three measurements and store them in the track and measurement lists respectively. Finally, we call the association function and plot the results. Let's see what the output of the startup script looks like. The figure contains the three tracks in red and the three measurements in green.

In the console output here on the right, we can see that the association metrics only contains infinity entries. Now, let's see if you can change the association metrics to contain the actual Mahalanobis distances.

## Additional Content

## Exercise: Association Matrix
