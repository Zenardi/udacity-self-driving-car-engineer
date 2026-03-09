# History of Sensor Fusion & Perception

> Part of: **Introduction to Sensor Fusion and Perception**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=qZNsg5VtuxI)

## Summary

**LiDAR Technology and Sensor Fusion**
=====================================

This project explores LiDAR technology, its history, and its application in autonomous vehicles. We will delve into the principles behind LiDAR sensors, their advantages, and challenges.

### Key Concepts
* **Active Sensor Technology**: LiDAR is an active sensor that emits its own light to measure distances.
* **Time of Flight (ToF)**: The time it takes for a laser beam to travel from the sensor to a target and back. This allows the sensor to calculate distance.
* **Optical Phased Arrays**: A technique used in some LiDAR sensors to improve resolution and accuracy.
* **Frequency-Modulated Continuous-Wave LiDARs**: A type of LiDAR that uses frequency modulation to measure distances.
* **Sensor Fusion**: Combining data from multiple sensors, such as LiDAR, radar, and cameras, to create a more accurate representation of the environment.

### Practical Notes
* LiDAR technology has been around since the 1930s but has seen significant improvements in recent years.
* Autonomous vehicles rely heavily on sensor fusion systems that combine data from multiple sensors.
* The price of LiDAR sensors is still a major challenge, but efforts are underway to develop low-cost and high-performance solutions.

Note: This summary provides an overview of the key concepts and practical notes from the lesson transcript. It can be used as a starting point for further research or development in the field of LiDAR technology and sensor fusion.

## Transcript

Let's take a brief look at LiDAR technology and its history, as this is the main new sensor type which you will learn about in this course here. Other than the camera you have already heard about in the first course and deep-dived into it, LiDAR is a so-called active sensor technology, which means the sensor brings its own light and emits it into the scene. This also means it does not have to rely on how to control ambient signals such as sunlight, for example. Just like the camera, lidar is an optical sensor which emits this beam of laser light that reflects off of surfaces and then returns to the sender. Based on the time of flight of this beam of light, the ToF, the LiDAR sensor can then calculate the distance to the reflective target which might be, for example, a preceding vehicle and traffic.

This technology has actually been around for quite some time now since the 1930s, and among its first applications was the Luna Laser Ranging experiment in 1969 onboard Apollo 11 even. Later it was used as an airborne sensor to create accurate topological maps, and elevation models, for example, in archaeology where it helped to discover hidden sites under the ground. One of the first successful uses in automotive in 2005 was when the Stanford Racing Team won the DARPA Grand Challenge through the Mojave desert using LiDAR sensors and in 2007, the Urban Challenge. Since then with the advent of autonomous driving at our doorstep, significant improvements of LiDAR technology have been developed, making it one of the cornerstones of the autonomous vehicle sensors [inaudible] currently. One of its major problems though, is the price which is still orders of magnitude higher than for other established sensors, such as, for example, the radar of a camera.

However, a large number of teams all around the world in many, many companies are currently working on low cost and high-performance LiDAR sensors. It really can be expected that these teams will be successful at bringing down the price point and miniaturize LiDAR sensors enough: Let's say in about five years, three to five years, maybe, to be really used in mass production. In the first lesson you will learn a lot about this technology and the underlying principles which is not only time of flight, but also includes optical phased arrays and frequency-modulated continuous-wave LiDARs, and much more. I'm really looking forward to sharing all of this with you now. Let's take a quick look at the history of tracking and sensor fusion.

Most tracking algorithms were developed in the context of air surveillance and military applications. For example, the famous Kalman filter for tracking dates back to the 1960s where it helped fly to the moon during Apollo space program. Isn't it impressing that such an old method is still state- of-the-art today and automated vehicles all over the world rely on it? The first tracking applications did not use sensor fusion but mainly relied on radar data alone. Same holds true for the first driver assistant systems.

For example, the first adaptive cruise control systems around the year 2000 were realized with radar only, and the first parking systems were realized with ultrasonic sensors alone. It was only with the rise of advanced driver assistant systems and automated driving that single sensors reached their limits and more effort was put into developing sensor fusion systems. Today, most driver assistant systems rely on several sensors. Automated vehicles mostly use one central fusion system. The sensor fusion module creates one consistent model of the environment and different assistant systems and applications use the same fused world representation.

## Additional Content

## History of Sensor Fusion & Perception
- Lidar is an active sensor, which means that it does not rely on ambient signals such as sunlight. Just like a camera, lidar is an optical sensor, which emits a beam of laser light, that reflects off of surfaces and returns to the sender. Based on the time-of-flight (ToF) of the beam of light, the lidar sensor can calculate the distance to the reflective target.

- Lidar technology has been around since the 1930s and among its first applications was the "Lunar Ranging Experiment" in 1969 on board Apollo 11. Later it was used as an airborne sensor to create accurate topological maps and elevation models, for example in archaeology.

- One of the first successful uses in automotive occurred in 2005, when the Stanford Racing Team won the DARPA Grand Challenge. Since then, significant improvements of LiDAR technology have been developed, making it one of the cornerstones of the autonomous vehicle sensor suite.

- A problem of Lidar sensors is the price, which is still orders of magnitude higher than for other established sensors such as radar. However, it can be expected that within 3-5 years, the technology will be miniaturized and cheap enough to be used in mass production.

- Most tracking algorithms were developed in the context of air surveillance and military applications. For example, the famous Kalman filter for tracking dates back to the 1960s, where it helped fly to the moon during Apollo space program. 

- The first tracking applications did not use sensor fusion, but mainly relied on radar data alone. The same holds true for the first driver assistance systems. For example, the first adaptive cruise control systems around the year 2000 were realized with radar only, and the first parking systems were realized with ultrasonic sensors alone. 

- It was only with the rise of advanced driver assistance systems and automated driving that single sensors reached their limits and more effort was put into developing sensor fusion systems. Today, most driver assistance systems rely on several sensors, and automated vehicles mostly use one central fusion system. The sensor fusion module creates one consistent model of the environment, and different assistance systems and applications use the same fused world representation.
