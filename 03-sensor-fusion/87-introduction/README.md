# Introduction

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=sgsZfYKE6g4)

## Summary

**Sensor Fusion with Kalman Filters**
=====================================

This README file provides an overview of the key concepts and practical steps for building a sensor fusion system using Kalman filters, as introduced in this Udacity lesson.

### Key Concepts

* **Sensor Fusion**: The process of combining data from multiple sensors to improve accuracy and robustness.
* **Kalman Filter**: A mathematical algorithm used to estimate the state of a system from noisy measurements. In this context, it's used to combine measurements from different sensors.
* **Multi-Sensor Fusion**: Using Kalman filters to integrate data from multiple sensors, such as LiDAR and cameras.
* **State Estimation**: The process of estimating the current state of a system based on past measurements.

### Practical Notes

This lesson covers the practical application of multi-sensor fusion using Kalman filters. You will learn how to:

* Use a Kalman filter to combine measurements from different sensors
* Implement a sensor fusion system in code (not provided in this transcript)
* Apply this knowledge to fuse LiDAR and camera measurements in the final project

Note: This summary is based on the provided transcript, but it does not include any specific code or formulas. If you need more detailed information, please refer to the original lesson materials or additional resources.

## Transcript

Hi there. My name is [inaudible]. I'm a self-driving car engineer and a technical lead for sensor fusion at Mercedes-Benz. I will guide you through the remaining sensor fusion lessons and the tracking project. You have finally arrived at the point where you will combine your computer vision and LiDAR knowledge in one sensor fusion module.

Sensor fusion is a core component of every self-driving car. It is not possible to rely on a single sensor alone, because every sensor has its strengths and weaknesses and may fail at times. Therefore, it is crucial for a self-driving car engineer to know how to build a sensor fusion system. You've already learned from Sebastian the basics of Kalman filters. So far, you only used a Kalman filter to integrate sequential measurements from a single sensor.

But actually it is also possible to use Kalman filters to combine measurements from different sensors. In this lesson, you will learn to build a fusion system by using Kalman filters. After the lesson, you will have all necessary skills to fuse LiDAR and camera measurements and track vehicles over time in the final project. Does that sound like fun? Let's get started.

## Additional Content

## Introduction
In this lesson, you will learn how to fuse lidar and camera measurements with an Extended Kalman Filter! You will implement a 2D Kalman Filter in Python along with a nonlinear camera measurement model to track objects over time.
