# Course Summary

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=tXslPNulz-g)

## Summary

**Sensor Fusion and Multi-Target Tracking**
=====================================

This lesson series covers the basics of sensor fusion and multi-target tracking, including Kalman filters and extended Kalman filters. By the end of this course, you will be able to fuse data from different sensors and track multiple vehicles over time.

### Key Concepts

* **Kalman Filters**: A mathematical algorithm used for estimating the state of a system from noisy measurements.
* **Extended Kalman Filters (EKF)**: An extension of the Kalman filter that can handle nonlinear measurement models, allowing it to be applied to systems with complex dynamics.
* **Nonlinear Measurement Models**: Mathematical representations of how sensor data is related to the system's state, which are used in EKF algorithms.
* **Track Management Module**: A module responsible for initializing and deleting tracks, as well as managing track scores and data association methods.

### Practical Notes

To implement sensor fusion and multi-target tracking, you will need to:

* Implement an EKF with nonlinear measurement models to fuse camera and Lidar data
* Create a track management module that includes track initialization, deletion, and scoring
* Use a data association method, such as gating, to associate measurements with existing tracks

This knowledge is essential for solving real-world tracking problems, such as fusing Lidar and camera data from an actual self-driving car. The final project will put your skills into practice by applying sensor fusion and multi-target tracking techniques to a real-world scenario.

## Transcript

In the second part of the course, we have covered sensor fusion and multi-target tracking. In lesson four, you have learned from Sebastian through the basics of Kalman filters. We have then moved onto extended Kalman filters to track vehicles over time in lesson five. You have implemented your first EKF with nonlinear measurement models to fuse camera and Lidar data. In lesson six, we have created a track management module, including track initialization and deletion.

A track score, and a data association method including gating. To sum it up, you are now able to fuse data from different sensors and track several vehicles over time simultaneously. Now let's put your knowledge into practice by solving a real world tracking problem and fuse Lidar and camera data from an actual self-driving car in the final project. Have fun.

## Additional Content

## Course Summary

Let's check back in with Andreas, and then Antje will see you out and on into the final project!
In the 3D object detection and sensor fusion course, we have covered the following topics:

- Lidar sensor technology
- How to extract range images from Waymo frames, how to visualize range and intensity data and transform it into a 3d point-cloud
- Object detection based on point clouds
- Assessing the performance of object detectors using recall and precision
- Tracking of vehicles over time with Kalman Filters
- Sensor fusion of camera and lidar measurements using Extended Kalman Filters with nonlinear measurement models
- Multi-Target Tracking including track initialization and deletion, confidence measures and data association
