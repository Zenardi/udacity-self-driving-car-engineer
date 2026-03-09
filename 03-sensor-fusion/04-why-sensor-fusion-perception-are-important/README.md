# Why Sensor Fusion & Perception Are Important

> Part of: **Introduction to Sensor Fusion and Perception**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=_WiUd2iLiqo)

## Summary

**Sensor Fusion in Autonomous Vehicles**
=====================================

Autonomous vehicles rely on multiple sensors to perceive the environment and make decisions without human intervention. However, each sensor has its limitations and can fail under certain conditions.

### Key Concepts

* **Single Sensor Limitations**: No single sensor can provide a complete picture of the environment due to its inherent advantages and disadvantages.
* **Sensor Fusion**: Combining data from multiple sensors to improve accuracy, reliability, and robustness in environment perception systems.
* **RADAR (Radio Detection And Ranging)**: Uses physical measurement principles to detect objects and measure distances.
* **LiDAR (Light Detection And Ranging)**: Similar to RADAR but uses laser light to create high-resolution 3D maps of the environment.
* **Sensor Failure or Weaknesses**: Even with multiple sensors, there is no guarantee that all will function correctly at all times.

### Practical Notes

When designing an autonomous vehicle's sensor system, consider the following:

* Use a combination of camera, RADAR, and LiDAR sensors to improve accuracy and robustness.
* Implement algorithms for sensor fusion to combine data from multiple sources and compensate for individual sensor failures or weaknesses.
* Continuously monitor and adapt to changing environmental conditions to ensure reliable operation.

Note: This summary is based on the provided transcript and may not cover all aspects of the original lesson.

## Transcript

I think the biggest challenge ahead in the field of autonomous vehicles is moving from advanced driver assistance systems to real self-driving cars where the driver is no fallback option. With current advanced driver assistance systems, you may already drive hundreds of miles automatically without driver into action. But then an unknown situation may occur and the system needs the driver to take over. In real self-driving cars without human drivers, the system will have to handle every single situation on its own. The world is just so complex that nobody has solved this problem so far.

I am convinced that self-driving cars cannot be realized using a single sensor alone. Every sensor has advantages and disadvantages and may fail from time to time. So far, you've learned a lot about camera sensors. But what if the camera is blinded by the sun? What if the view is to stop by raindrops?

Also, the camera image is a 2D projection of the 3D world. So how can we measure the accurate distance of other vehicles? To solve these challenges, additional sensors like RADAR or LiDARS are needed. They have different physical measurement principles and can improve the reliability of the environment perception system. You might ask why it is not possible for an autonomous vehicle to rely on cameras alone, while human drivers mainly use their eyes as sensors.

Yes, for human drivers, the vision based driving task is relatively simple. But remember that we have millions of years of evolution behind us. So it will take some time for machines to close this gap. To sum it up, sensor fusion is an essential part of self-driving cars because it improves single sensor results and compensates for sensor failures or weaknesses. As long as there are no perfect sensors, sensor fusion is a key enabler for self-driving cars.

## Additional Content

## Why Sensor Fusion & Perception Are Important
- Sensor fusion is an essential part of self-driving cars because it improves single-sensor-results and compensates for sensor failures or weaknesses. 

- Every sensor has advantages and disadvantages and may fail from time to time, for example: What if the camera is blinded by the sun? What if the view is disturbed by rain drops? Also, the camera image is a 2D projection of the 3D world, so how can we measure the accurate distance of other vehicles? To solve these challenges, additional sensors like radars or lidars are needed. They have different physical measurement principles and can improve the reliability of the environment perception system.
