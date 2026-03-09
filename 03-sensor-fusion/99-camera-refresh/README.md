# Camera Refresh

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=976UgJCidYU)

## Summary

**Kalman Filter Sensor Fusion with Camera Detections**
======================================================

This project aims to improve vehicle tracking in 2D by integrating camera detections into a Kalman filter system that uses LiDAR measurements.

### Key Concepts

* **Sensor Fusion**: Combining data from multiple sensors (LiDAR and camera) to improve tracking accuracy and robustness.
* **Kalman Filter**: A mathematical algorithm for estimating the state of a system from noisy measurements.
* **Pinhole Camera Model**: A simplified model of a camera that assumes a small hole in place of the lens, projecting images onto an image plane.
* **Image Point Coordinates**: Calculated using the focal length and object point coordinates, with depth information lost due to monocular vision.

### Practical Notes

To integrate camera detections into the Kalman filter system:

1. Understand the advantages of camera detections (object classification, improved accuracy for certain objects).
2. Recognize the limitations of LiDAR measurements (difficulty detecting black or reflective objects).
3. Use sensor fusion to combine data from both sensors and improve tracking robustness.
4. Apply the pinhole camera model to calculate image point coordinates.

Note: This project builds upon a previous implementation of a Kalman filter for tracking vehicles in 2D using LiDAR measurements.

## Transcript

Congratulations, you've just implemented a full Kalman filter program for tracking a vehicle in 2D. You have used LiDAR measurements to update the 4D State containing position and velocity. But of course, this module is called sensor fusion so we need to be able to fuse data from another sensor to improve our tracking. In the next steps, we will integrate camera detections into our Kalman filter. How will camera detections improve our tracking?

Although the LiDAR provides the vehicles position with high accuracy, the camera has its own advantages. For example, camera detections are predestined for object classification. In addition, LiDAR may have problems to detect black or highly absorbing objects, or it might deliver false positive vehicle detections for small but reflective objects like guardrail reflectors. In general, all sensors may fail sometimes due to blockage or calibration errors. Additional sensors always improve robustness and reliability of our fusion system.

Now, let's do a quick recap of some camera basics you learned back in the first lesson. Remember the pinhole camera model that assumes a camera to be like the very first camera in history, the camera obscura. A camera obscura is a black box with a small hole in it. Every object in the world, for example, the candle in the image, is projected through the hole onto the image plane on the back wall of the box. This projected images is upside down.

The pinhole camera model has similar assumptions. We neglect the lens for a moment and replace it by a hole, the optical center O. Every object point x, y, z is projected onto an image point in the image plane, and just like for the camera obscura, the image is upside down. Because dealing with this sign inversion is tedious, we assume that the image plane lies in front of the optical center instead of behind it. This is of course not the reality, but it simplifies our calculations.

Besides that, it has no other significance. The distance of the image plane to the optical center is the focal length f, and with these definitions, we can now tell what the image point of an object point x1,y1, z1 is. The distance x1 is replaced by the focal length f and y1 and z1 are scaled with the same factor by dividing through x1 and multiplying with F. This gives the image point coordinates that you can see here in the violet box. Until we see a shortcoming of monocular cameras, every other point on this line is projected onto the same image point.

We lose the depth information and can't directly resolve this ambiguity. We can however, resolve it through sensor fusion with a LiDAR.

## Additional Content

## Camera Refresh
- Refresh of the pinhole camera model with optical center

$o$

and focal length

$f$

.
- Projection formula of a 3D point to 2D image plane:

$$\begin{pmatrix}
x,&y, &z
\end{pmatrix}

\mapsto
\Large
\begin{pmatrix}
\frac{f\cdot y}{x}, &
\frac{f\cdot z}{x}
\end{pmatrix}$$

- This shows that the distance information is lost, we need to compensate the loss through sensor fusion.
