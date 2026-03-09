# Introduction

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=QnrHK_k0MY4)

## Summary

**Multi-Target Tracking with Sensor Fusion**
=============================================

This README file summarizes the key concepts and practical steps covered in the multi-target tracking lesson.

### Key Concepts

* **Track management**: Deciding which track to update with a new measurement, especially when multiple targets are present
* **Track initialization**: Setting up a new track for a vehicle that appears from around the corner or enters the visible range
* **Track deletion**: Determining when to delete a track for a vehicle that disappears from view
* **Confidence measure (track score)**: Calculating a confidence level to determine if an emergency braking is necessary, such as detecting a pedestrian in front of the vehicle

### Practical Notes

This lesson focuses on practical problems that arise in real-world applications of multi-target tracking. To apply these concepts, you will need to:

* Implement track management strategies for multiple targets
* Develop algorithms for initializing and deleting tracks based on sensor measurements
* Calculate confidence measures (track scores) to determine the likelihood of a target's presence

Note: The final project will involve applying these skills to track multiple vehicles with real-world camera and lidar measurements.

## Transcript

Welcome to the final lesson of the sense of using cars. You already know a lot about estimating of vehicles position and velocity with an extended Kalman filter. But there are some important questions left that we need to answer before moving on to the final project. Imagine a real self-driving car that perceives its environment with sensor fusion. Usually, there will not only be a single vehicle or pedestrian to trick but several ones, so how to decide which track to update with which measurement.

What if a new vehicle appears from around the corner, how to set up a new track? What if a vehicle disappears from our visible range, when should we delete the track? Finally, we only want to do an emergency braking if diffusion system is absolutely sure that there is a pedestrian in front of the vehicle. We need some confidence measure or track score. All these questions arise in the context of multi-target tracking and we will solve them in this lesson.

After the theoretical estimation problem in the last lesson, this lesson is more concerned with practical problems that arise in real-world applications. After this lesson, you will have all necessary skills to track multiple vehicles with real-world camera and lighter measurements in the final project. Have fun.

## Additional Content

## Introduction
In the last lesson, we have learned how to track a single object over time. In reality, there are several objects at once and they may appear or disappear. Therefore, we will move from single-target tracking to multi-target tracking in this lesson.
