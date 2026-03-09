# Exercise: Initialization

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=GyJYQu1h_Dk)

## Summary

**Track Initialization Based on Unassigned Measurement**
======================================================

This README file summarizes the key concepts and practical steps for implementing track initialization based on an unassigned measurement in a tracking system.

### Key Concepts
* **Track Class**: A class representing a track with methods for initialization and updating.
* **Measurement Class**: A class containing information about a 3D LiDAR measurement, including:
	+ **Transformation Matrix**: A matrix that transforms sensor coordinates to vehicle coordinates.
	+ **Rotation and Translation**: Components of the transformation matrix.
	+ **Noisy Measurement**: A noisy 3D LiDAR measurement with associated covariance metrics R.
* **Initialization Function**: A function that initializes a track based on an unassigned measurement.

### Practical Notes
To implement track initialization, follow these steps:

1. Initialize the vector `x` and metrics `p` in the track class using the measurement input.
2. Use the transformation matrix from the measurement class to convert the measurement from sensor coordinates to vehicle coordinates.
3. Visualize the results using the provided function.

Note: The measurement class is already implemented, so do not modify it. Focus on implementing the initialization function for the track class.

## Transcript

I have a first exercise for you. I want you to implement a track initialization based on an unassigned measurement. This is a track class with a prepared initialization function. Please initialize the vector x and metrics p based on the measurement input. The measurement input is an instance of the measurement class below.

The measurement class already contains the correct transformation matrix, including rotation and translation from sensor to vehicle coordinates. Then a noisy 3D LiDAR measurement is initialized based on the clown tooth input, as well as a corresponding measurement covariance metrics R. You don't have to change anything in the measurement class. Further, the script contains a function to visualize the results. Let's see what happens if I run the starter script.

The left plot contains our test measurement in sensor coordinates. We want to use this measurement to initialize a new track. The second plot shows the initialized track, as you see the track is still zero, but you should see some changes here once you implemented the initialization. Finally, the last plot shows the measurement converted to vehicle coordinates and the initialized track. If you have implemented everything correctly, the track should be initialized where the measurement lies.

The blue and red marker should align. Let's see if you can achieve that.

## Additional Content

## Exercise: Initialization
You can find the starter code for this lesson's exercises in the [same repository](https://github.com/udacity/nd013-c2-fusion-exercises) as the previous lesson, meaning that if you have been working locally, you can continue with the same files. Otherwise, the code is provided in the workspace below.
