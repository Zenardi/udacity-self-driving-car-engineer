# Waymo: Using Sensors

> Part of: **Introduction to Sensor Fusion and Perception**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=849rTdCmjL4)

## Summary

**Sensor Fusion and Calibration**

This project involves combining data from multiple sensory modalities to create coherent object-based representations and tracks. The goal is to fuse input from various sensors into a unified understanding of the environment.

### Key Concepts

* **Late fusion methods**: Techniques for combining data from multiple sources, including common filters that embody the Markovian assumption.
* **Markovian assumption**: A model where all state about a track is carried in the model and updated through data association with various inputs.
* **Deep-learning methods**: Modern approaches to sensor fusion that are producing stronger results than traditional late fusion methods.
* **Calibration**: The process of accurately determining the positions of sensors on a vehicle, as well as their optical properties.

### Practical Notes

When working with multiple sensors, it's essential to calibrate them accurately to ensure effective data transfer and cross-referencing. This involves computing the precise positions of all sensors, including cameras, lidar, radar, and microphones. The calibration process is crucial for applications like autonomous driving, where accurate sensor placement can significantly impact performance.

For example, Waymo's use of multiple sensors (lidar, radar, cameras, and microphones) demonstrates the importance of thoughtful sensor selection and calibration. By combining these modalities, they achieve a more comprehensive understanding of their environment and improve overall system performance.

## Transcript

In the case where you have detection and tracking systems in multiple sensory modalities, providing your input, there's multiple ways to fuse those, into coherent object-based representations, tracks. Of the late fusion methods, common filters are really popular. They embody the Markovian assumption. All the state about a track is carried in the model and through data association with the various inputs from the perception subsystems, you keep updating the state. Nowadays, deep-learning methods are also possible and they're coming in and starting to provide stronger results as well.

So carbon filter is not the only solution anymore for late fusion. Typically, when you put a bunch of sensors on the car, in order to use them well and be able to transfer information from one sensor to another or cross-reference it with the map, you need to know their position on the vehicle really accurately. Calibration is the process of computing the accurate positions of all sensors, and also often even the optical properties of some of the sensors. Waymo, uses several different sensors in the vehicle. These include lighter, radar, and cameras.

They were chosen very deliberately and thoughtfully because they really complement each other in their capabilities. A fourth sensor Waymo uses is microphones as well. This can be helpful, for example, in detecting ambulances and police cars.

## Additional Content

## Waymo: Using Sensors

Let's check back in with Waymo, and Dragomir, Distinguished Scientist at Waymo, on using sensors on their autonomous vehicles.

### Tracking Objects Across Different Sensors
### Sensor Calibration
### What Sensors does Waymo use?
