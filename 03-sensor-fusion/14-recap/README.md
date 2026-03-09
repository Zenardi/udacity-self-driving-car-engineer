# Recap

> Part of: **Introduction to Sensor Fusion and Perception**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=1BOz4jKxDYM)

## Summary

**Autonomous Vehicle Sensor Fusion with LiDAR Technology**
===========================================================

This project focuses on combining multiple sensors in autonomous vehicles using a fusion approach, particularly leveraging LiDAR technology. We'll explore why single-sensor systems are insufficient for true autonomous driving and how to implement an Extended Kalman Filter to track objects over time.

**Key Concepts**
---------------

* **Sensor Fusion**: Combining data from multiple sensors (e.g., camera, LiDAR) to improve accuracy and robustness in autonomous vehicles.
* **LiDAR Technology**: A type of sensor that uses laser light to detect and measure distances, essential for 3D mapping and object detection.
* **Extended Kalman Filter (EKF)**: An algorithm used for tracking objects over time by incorporating camera and LiDAR detections into a single sensor fusion module.
* **Multi-Target Tracking**: The ability to track multiple vehicles simultaneously using a track management module and data association module.

**Practical Notes**
------------------

To implement the components discussed in this lesson, you'll need to:

* Implement an Extended Kalman Filter to incorporate camera and LiDAR detections
* Develop a track management module to initialize empty lead tracks
* Create a data association module to decide which measurement belongs to which track

Note: Familiarity with machine learning concepts is assumed. If needed, review the free courses available on Udacity for a refresher.

## Transcript

Let's quickly recap the most important takeaways from this introductory lesson here. First, please make sure that you take as many boxes in the prerequisites section as possible because we will not be starting from zero in this course, but instead we will assume that you have at least some prior knowledge in the areas which we mentioned there. In case you need to refresh your knowledge on machine learning, make sure to check out the free courses available here at Udacity. Secondly, we have looked at why it makes sense to combine several sensors in autonomous vehicles in a fusion approach with a special focus on LiDar technology and you should appreciate the fact that systems with only one and possibly with two types of sensors will not be sufficient for true autonomous driving, at least not in the first years after market introduction. You have also had first glimpse of the contents of my lessons in this course on LiDAR technology and also on detecting objects in point clouds, which will also be the main focus of the mid-term projects.

Now please take a look at what the [inaudible] has to say about Kalman filters and multi-target tracking. In this lesson you've learned why a sense of fusion is a crucial part of every self-driving car. You also know that we do not only want to detect objects at a single time frame, but we want to track position and velocity of objects over time and predict their future movement. Therefore, we will implement an Extended Kalman Filter that incorporates camera and LiDAR detections in a single sensor fusion module. In order to track several vehicles simultaneously, we need a track management module to initialize empty lead tracks and a data association module to decide which measurement belongs to which track.

We will implement these components and the multi-target tracking lesson.

## Additional Content

## Recap
- Make sure to refresh your knowledge in the areas mentioned in the prerequisites section. To do this, there are courses available at Udacity such as Python programming or Machine learning.

- In this lesson, we have looked at why it makes sense to combine several sensors in an autonomous vehicle, with a special focus on lidar sensors.

- You have also looked at the contents of the lessons on lidar technology and on detecting objects in point clouds - which will also be the main focus of the mid-term project.

- You also know that we do not only want to detect objects at a single time frame, but we want to track position and velocity of objects over time and predict their future movement. Therefore, we will implement an extended Kalman filter that incorporates camera and lidar detections in a single sensor fusion module. 

- In order to track several vehicles simultaneously, we need a track management module to initialize and delete tracks, and a data association to decide which measurement belongs to which track. You will implement these components in the multi-target tracking lesson and in the final project.
