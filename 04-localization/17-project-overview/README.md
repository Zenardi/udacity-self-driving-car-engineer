# Project Overview

> Part of: **Introduction to Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=aBngBS6zRVM)

## Summary

**Vehicle Localization using Point Cloud Maps**
=====================================================

This project involves localizing a vehicle using a point cloud map from the CARLA simulator. The goal is to develop an algorithm in C++ that can effectively track the vehicle's position and pose, while keeping the pose error low for a given driving distance.

### Key Concepts

* **Point Cloud Map**: A 3D representation of the environment, consisting of a collection of points.
* **CARLA Simulator**: An open-source simulator used to generate point cloud maps and test localization algorithms.
* **Iterative Closest Point (ICP)**: An algorithm for registering two point clouds by finding the closest points between them.
* **Normal Distributions Transform (NDT)**: A registration method that uses a probability distribution to represent the transformation between two point clouds.
* **Pose Error**: The difference between the estimated pose of the vehicle and its ground truth position.

### Practical Notes

To complete this project, you will need to implement either ICP or NDT in C++ and use it to register the current scan with the map cloud. This will involve:

* Loading point cloud data from the CARLA simulator
* Implementing a registration algorithm (ICP or NDT)
* Calculating the pose error between the estimated pose and ground truth position
* Visualizing the results using tools such as RViz or Matplotlib

Note that this project requires a good understanding of C++ programming, point cloud processing, and registration algorithms.

## Transcript

In the final project at the end of this course, you will localize a vehicle using a point cloud map from the CARLA simulator shown below. Using either iterative closest point or normal distributions transform, you will build your localizer in the C++ programming language, similar to the exercises throughout the course. Now, a key requirement of the project is that you'll need to keep the pose era low for a given driving distance that prove that your algorithm can effectively localize the vehicle closely to its ground truth position. Now, let's take a look at what the project actually looks like. What I'm seeing is the current scan in red, that's my scan cloud, and I see the map cloud in blue, and I'm seeing how far I've driven, and the Pose error and the Max error that I've received, and all of these are zeros so far.

I'm just going to hit up on the keyboard three times one, two, three, and I'll start moving and you'll see that the red skin staying put, it's still all in reference to the LIDAR sensor so it's treating that as its reference frame. You can see my distances increasing that Pose error same as the distance, and same with the Max Error. Because it still thinks I'm back at the origin, so once you actually fill in scan matching, then you'll be able to localize and keep up with that red car over there with the green one.

## Additional Content

## Project Overview
### Project Demo

[Watch on YouTube](https://www.youtube.com/watch?v=xqYREk_4_eg)


At the end of the course, you will be working on the final project, wherein you will implement a scan matching algorithm on a point cloud map from the [CARLA simulator](https://carla.org/), using your choice of either of the ICP or NDT algorithms you learn later on. Additionally, you will be building this localizer in C++.

As is the case on a real self-driving car, localization accuracy is of high importance - a self-driving car that can't localize accurately could easily drift into the wrong lane or worse.
