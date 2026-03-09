# Project: Sensor Fusion and Object Tracking

> Part of: **Introduction to Sensor Fusion and Perception**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Tm0nDsOftAM)

## Summary

**Midterm Project: Detecting Vehicles in Lidar Point Clouds**
===========================================================

This project focuses on detecting vehicles in lidar point clouds using a deep learning approach. The goal is to transform range images into point clouds, create a bird's eye view (BEV) map, and then detect objects within the BEV maps using a pre-trained model.

**Key Concepts**
---------------

* **Lidar Point Clouds**: 3D representations of the environment captured by lidar sensors.
* **Bird's Eye View (BEV) Maps**: 2D representations of point clouds projected onto a horizontal plane.
* **Deep Learning Approach**: Using neural networks to detect vehicles in lidar point clouds.
* **Extended Kalman Filter**: A mathematical algorithm used for tracking multiple objects over time.
* **Sensor Fusion**: Combining data from different sensors (camera and lidar) to improve accuracy.

**Practical Notes**
------------------

To complete the midterm project, you will need to:

1. Transform range images into point clouds using a deep learning approach.
2. Create a bird's eye view (BEV) map of the point cloud.
3. Detect objects within the BEV maps using a pre-trained model.
4. Evaluate the performance of two detectors to determine which one is better.

In the final project, you will build on these skills by implementing an extended Kalman filter to track multiple vehicles over time and fusing camera and lidar detections. The sensor fusion project uses real-world data from an actual self-driving car, making it a challenging but rewarding task.

## Transcript

Now in this section, Anty and I will give you an overview of the projects you will be working on in this course. As I mentioned before, the course is divided into two broader parts, which are lidar and also detecting objects in point clouds, and secondly, Kalman filters and multi-target tracking. After part one, you will start working on the first project, which is called the midterm project. The goal of this midterm is to detect vehicles in lidar point clouds using a deep learning approach. In order to successfully do this, you will need to implement a number of exercises in all these lessons which include transforming the range images into point clouds, creating a bird's eye view of the point cloud, a so-called BEV map, and then thirdly, detecting objects within these BEV maps using a pre-trained model.

Then lastly to evaluate the performance of two detectors to find out which one is better. You will note that some tasks are familiar because you have been working on aspects of them in relevant chapters already. When you diligently work, put in the work, the effort on all the exercises in the lessons, you should really be well prepared when you start the midterm project. Also, Anty and I have decided to create one single [inaudible] for you, which contains both the source code for the midterm, as well as for the final project. Once you are familiar with the code for the midterm, also with the structure, with parameterizing the detector, you will find that the same code base is also used in the final project.

In the final project, you will solve a challenging multi-target tracking task by fusing camera and lidar detections. You will implement an extended Kalman filter to track several vehicles over time, including the different measurement models for camera and lidar. You will also implement a track management module for track initialization and deletion, and a data association module to decide which measurement originated from which track. Sensor fusion and multi-target tracking are complex tasks, but if you complete all lessons and work on all exercises beforehand, you are well prepared to implement your own sensor fusion and tracking module in the final project. The sensor fusion project uses real-world data from an actual self-driving car, which is more challenging and more fun than using simulated data.

I had to deal with a lot of real-world challenges building the course. Therefore, the sensor fusion project is quite close to the everyday work of a sensor fusion engineer.

## Images

![This image shows multiple vehicles tracked simultaneously in the final project.](images/s3.png)
*Multi-target tracking scenario from the final project*

## Additional Content

## Project: Sensor Fusion and Object Tracking
- After completing the first two lessons, you will start working on the mid-term project. The goal of the project will be to detect vehicles in lidar point clouds using a deep-learning approach.

- You will need to implement a number of exercises, which include (1) transforming the Waymo range images into point clouds, (2) creating birds-eye views (i.e BEV maps) from point clouds, (3) detecting objects within BEV maps using pre-trained models and then (4) evaluating the performance of two detectors.

- The [GitHub repo](https://github.com/udacity/nd013-c2-fusion-starter) for the mid-term project is also used for the final project.

- In the final project, you will solve a multi-target tracking task by fusing camera and lidar detections. You will implement an extended Kalman filter to track several vehicles over time, including the different measurement models for camera and lidar. 

- You will also implement a track management module for track initialization and deletion, and a data association module to decide which measurement originated from which track.
