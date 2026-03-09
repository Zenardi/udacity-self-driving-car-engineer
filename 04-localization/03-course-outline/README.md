# Course Outline

> Part of: **Introduction to Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=5M27PwE6vlQ)

## Summary

**Markov Localization and Scan Matching**
=====================================

This module introduces two key concepts in robotic localization: Markov localization and scan matching. These techniques are used to enable robots to determine their location within a given environment.

### Key Concepts

* **Bayes' Rule**: A statistical concept that is leveraged by Markov localization to update the robot's belief about its location based on new sensor data.
* **Markov Localization**: A journalized filter that uses Bayes' rule to estimate the robot's location and uncertainty in real-time.
* **Scan Matching**: An algorithm for localizing a robot using a single Lidar sensor, which can be used even without a map to achieve SLAM (Simultaneous Localization and Mapping).
* **ICP (Iterative Closest Point) Algorithm**: A scan matching method that iteratively finds the closest point between two sets of 3D points.
* **NDT (Normal Distributions Transform) Algorithm**: Another scan matching method that represents the environment as a set of normal distributions.

### Practical Notes

To implement Markov localization and scan matching, you will use C++ to build out a Markov localizer from scratch. You will also learn how to utilize these algorithms in a simulated environment using Lidar scans and a point cloud map. The final project will be similar to how the Udacity self-driving car localizes itself.

Note: This module includes three lessons:

1. Introduction to Markov localization
2. Scan matching (ICP algorithm)
3. Scan matching (NDT algorithm)

## Transcript

The first lesson of the localization module will introduce you to Markov localization, a journalized filter used for robotic localization. It helps leverage the statistics concept of Bayes' rule, which you may have heard of before. But don't worry if not as lesson will provide a refresher. It will be taught by Tiffany and Maximilian from Mercedes Benz, who you will hear from shortly. You'll get lots of practice building out a Markov localizer in that lesson using C++, which you'll also see a checkpoint on an upcoming mini-lesson.

In the final two lessons of this localization module, I'm excited to teach you about scan matching. Scan matching is one of my favorite algorithms for doing the localization and is actually what the Udacity self-driving car use to drive autonomously all the way from Mountain View to San Francisco. The cool thing about scan matching is it just requires a single Lidar sensor to localize. Also, something I always found really interesting about scan matching is it can be used even without a map achieving SLAM, simultaneous localization and mapping. In the first lesson, we'll go over two different algorithms for doing scan matching, the first ICP and then NDT.

In this lesson, you'll learn how to implement these methods from scratch using C++. In the final lesson, you'll learn how to utilize these algorithms to localize a car in a simulated environment using Lidar scans and a point cloud map. The final project will be very similar actually to how the Udacity self-driving car localizes itself.

## Additional Content

## Course Outline
The course outline is as follows:

* Markov Localization (Tiffany and Maximilian)
   * Learn about Markov localization, a generalized filter for robotic localization
   * Leverage Bayes' Rule
   * Lots of C++ practice
* Creating Scan Matching Algorithms (Aaron)
   * Basics of and how to implement Iterative Closest Point (ICP)
   * Basics of and how to implement Normal Distributions Transform (NDT)
* Utilizing Scan Matching (Aaron)
   * Apply ICP and NDT to a simulated environment with the CARLA simulator, using virtual lidar scans and point cloud maps
