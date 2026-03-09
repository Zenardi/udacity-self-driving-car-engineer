# Why CV Is Important for SDC

> Part of: **Introduction to Deep Learning for Computer Vision**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=btqHi9Cs3Lw)

## Summary

**Computer Vision for Self-Driving Cars**
=====================================

This project focuses on building intelligent cars that can navigate complex environments like cities by providing a usable signal. The self-driving car system uses computer vision to understand its environment from digital images, similar to how humans use their eyes when driving.

### Key Concepts
* **Computer Vision**: A field of techniques that allow computers to gain high-level understanding of their environment from digital images.
* **Object Detection**: Identifying and locating objects within an image, such as cars, traffic signs, and pedestrians.
* **Image Analysis**: Understanding the content and context of an image to make informed decisions.

### Practical Notes
To apply computer vision techniques in a self-driving car system, you can follow these steps:

1. Use cameras to capture digital images of the environment.
2. Apply object detection algorithms to identify relevant objects like cars, traffic signs, and pedestrians.
3. Analyze the detected objects to make optimal decisions for the self-driving car system.

Note: This project focuses on computer vision techniques using cameras. Lidar sensors are covered in another course.

## Transcript

To build intelligent cars that are able to navigate through environments as complex as cities, we need to provide some usable signal. How is our car going to decide when to turn or stop? Well, obviously, it needs some understanding of its environment. The same way that humans are using their eyes to analyze the road when driving, cars are going to use cameras. The field of computer vision consists in a range of techniques that allow a computer to get a high-level understanding of its environment from digital images.

For example, let's look at this image of a busy road together. What information do you think is relevant for the self-driving car system? Well, we could start by detecting all the car on image. We can also detect and read traffic signs, such as stop signs, which will be important for a self-driving car system to take into account when making decisions. Finally, we also need to detect pedestrians.

All these objects will be taken into account by the self-driving car system to make optimal decisions. You can now easily understand why computer vision is at the core of the self-driving car system. Some self-driving car system also use another type of sensor called Lidar, but this will be covered in another course of this of this nanodegree.

## Additional Content

## Why CV Is Important for SDC
Self-driving cars have multiple sensors, such as cameras, radar or lidar. In this course, we will focus on the **camera sensor**. Using this sensor, the system will be able to perform multiple tasks critical to its autonomy, such as detecting pedestrian, lanes or traffic signs. Later in the Nanodegree, you will perform **sensor fusion** using camera and lidar data!
