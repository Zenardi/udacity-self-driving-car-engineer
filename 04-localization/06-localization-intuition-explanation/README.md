# Localization Intuition Explanation

> Part of: **Introduction to Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=alIgWnGBUS8)

## Summary

**Localization: Understanding Your Surroundings**
=====================================================

This README file summarizes the key concepts and ideas behind localization, a fundamental technique used by robots to determine their location within a known environment.

### Key Concepts

* **Localization**: The process of determining a robot's location in the world using information gathered from its surroundings.
* **Uncertainty reduction**: Localization reduces uncertainty about a robot's location from an entire globe to a few kilometer radius, given just a single image or small amount of data.
* **Known maps**: A pre-existing map of the environment that is used for comparison with the robot's current observations.
* **Sensor data**: Information gathered by the robot about its surroundings, which is compared to the known map to determine location.

### Practical Notes

Localization has numerous practical applications in robotics and computer vision. Some examples include:

* Autonomous vehicles navigating through unfamiliar terrain
* Robots mapping out their environment for future navigation
* Image recognition systems identifying objects or locations within images

## Transcript

If you recognized this as the Eiffel Tower, then you will probably say something like Paris or France. This may not seem very impressive, but it's actually remarkable. Before the blindfold was removed, you had zero understanding of where you were in the world. You could have made a guess, but you would have had no idea if you were right. But after being shown a tiny amount of data, a single image, you reduce that uncertainty to a few kilometer radius. This is the main intuition behind localization. A robot gathers information about its current environment and compares that to a known map to understand where it is in the world.