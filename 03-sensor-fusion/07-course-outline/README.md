# Course Outline

> Part of: **Introduction to Sensor Fusion and Perception**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=19nIDyR0MrA)

## Summary

**README: Autonomous Driving with LiDAR Technology**

This course covers the fundamentals of LiDAR technology and its application in autonomous driving. The curriculum is divided into two parts: LiDAR Technology and detecting objects from point clouds, as well as Kalman filters and multi-target tracking.

### Key Concepts

* **LiDAR (Light Detection and Ranging)**: a remote sensing technology that uses laser light to measure distances between an object and the sensor.
* **Range Images**: a storage format used in LiDAR data sets, which stores distance information from the sensor to objects in the scene.
* **3D Point Clouds**: a representation of 3D scenes as a collection of points in space, created by transforming range images into point clouds.
* **Convolutional Neural Networks (CNNs)**: a type of deep learning algorithm used for image and signal processing tasks.
* **Kalman Filters**: a mathematical algorithm used to estimate the state of a system from noisy measurements, and predict its future movement.
* **Extended Kalman Filter (EKF)**: an extension of the Kalman filter that can handle non-linear systems.

### Practical Notes

This course provides hands-on experience with LiDAR technology and deep learning algorithms. You will learn to:

* Select and evaluate LiDAR sensors for autonomous driving applications
* Transform range images into 3D point clouds using Python code
* Implement a Kalman filter in Python to track objects over time
* Fuse camera and LiDAR data using an Extended Kalman Filter (EKF)
* Apply multi-target tracking techniques to handle multiple objects in the scene

By completing this course, you will gain the skills necessary to fuse LiDAR and camera measurements and solve real-world tracking problems.

## Transcript

Now, we have divided this course into two major parts, which are LiDAR Technology and also detecting objects from point clouds. Secondly, Kalman filters and multi-target tracking. Angie will be your instructor for the second part, while I will be your guide through the first part which expands lessons one and two and also the mid term project. Lesson one will all be about LiDAR Technology. You will really get a deep dive into this technology.

But we'll start with the general role of LiDAR in autonomous driving. We will discuss criteria you need to consider when selecting a sensor, for example, for a certain project. Then we will go really deep into the LiDAR working principle, the LiDAR equation, and also some of the various underlying technologies currently under development. Once you know what LiDAR is all about, what the abbreviation means, we will take a look at the concept of range images, which is the storage format actually used in the way more open data-set, which we will be using in this course here. I will show you how range images are structured and how you can transform them into the well-known 3D point clouds, you will surely have seen in articles you might have had prior to subscribing for this degree.

This is also the last chapter and concludes the LiDAR lesson. Then Lesson two, we will take a look at methods to detect objects of a certain type within point clouds using a deep learning approach. You will get first an overview of the currently available methods and also of the processing pipelines they use so you can understand the basic ideas and principles behind it. This will not, however, be an in-depth lesson on deep learning as this would be too much content for the scope of this course. Instead, I assume that you are already somewhat familiar, at least with convolutional neural networks, the C and ends, and also with the basic concepts which make up a deep learning system.

In this lesson, we will pick one selected method from the literature, which is called Complex YOLO, and then use it to detect vehicles and point clouds from the way more open data sets. The last chapter in Lesson two will then be about assessing the performance of such an optic equation system using a set of well-established metrics that you really need to know about. In the second half of this course, you will learn how to fuse camera and LiDAR measurements and track vehicles or pedestrians over time. In Lesson four, Sebastian Thrun will teach you the basics of Kalman filters. Kalman filters are a very powerful tool to track objects over time and estimate their position and velocity, as well as predict their future movement.

You will learn from Sebastian how to apply a Kalman filter and you will implement your first Kalman filter in Python. In Lesson five, we will extend this knowledge to more complex motion and measurement models. We will use the so-called Extended Kalman Filter or EKF. We will also learn how to fuse camera and LiDAR data with an EKF. As a sensor fusion engineer, a major task is tuning the Kalman filter and selecting the correct parameters.

Finally, you will implement your first EKF to track objects over time with noisy measurements. In lesson six, we will move onto multi-target tracking. Usually, they will not only be a single vehicle or pedestrian to track, but several ones. How to decide which measurement belongs to which track? What if a new vehicle appears from around the corner?

How to set up a new track? What if a vehicle disappears from our visible range, when should we delete the track? We also need a confidence measure or track score to estimate the reliability of our fusion results. All of these questions arise in the context of multi-target tracking and we will solve them in lesson six. After completing these lessons, you will have all the necessary skills to fuse LiDAR and camera measurements and solve a real-world tracking problem in the final project.

## Additional Content

## Course Outline
The course has been divided the course into two major parts, which are 
1. Lidar technology and object detection from point-clouds (Andreas) and 
2. Kalman filters and multi-target tracking (Antje).

Lesson 1 starts with the general role of LiDAR in autonomous driving and introduces criteria for sensor selection. Then, you will look at the lidar working principle and the lidar equation. Also, you will look at the concept of range images used in the Waymo Open Dataset. You will learn how you can transform them into 3d point-clouds.

In lesson 2, you will learn about methods for object detection within point clouds using deep-learning. This includes an overview of the currently available methods and of the processing pipelines as well as the use of one selected method from the literature called "Complex YOLO". Finally, you will learn how to assess the performance of object detection systems using a set of well-established metrics. 

Lesson 3 is the mid-term project, where you will detect objects in lidar point clouds.

In lesson 4, Sebastian Thrun will teach you the basics of Kalman filters. Kalman filters are a very powerful tool to track objects over time and estimate their position and velocity as well as predict their future movement. You will learn from Sebastian how to apply a Kalman filter, and you will implement your first Kalman filter in Python.

In lesson 5, we will extend this knowledge to more complex motion and measurement models. We will use the so-called "Extended Kalman filter", or EKF. We will also learn how to fuse camera and lidar data with an EKF, and you will implement your first EKF to track objects over time with noisy measurements.

In lesson 6, we will move on to multi-target tracking, where we will track several objects simultaneously. We will learn the basics of track management: how to initialize new tracks and delete old tracks, how to set a track score and a track state, and how to apply a data association technique to determine which measurement originated from which track.

Finally, you will apply your new skills to a real-world multi-target tracking scenario in the final project.
