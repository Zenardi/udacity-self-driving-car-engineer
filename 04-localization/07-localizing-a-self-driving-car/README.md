# Localizing a Self Driving Car

> Part of: **Introduction to Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=U-uDtVgezcE)

## Summary

**Localization for Self-Driving Cars**
=====================================

This project focuses on solving the localization problem in self-driving cars, which involves determining the car's location within a global map with high accuracy.

**Key Concepts**
---------------

* **Localization**: The process of determining a vehicle's location within a given map with high accuracy (between 3 and 10 centimeters).
* **Global Navigation Satellite Systems (GNSS)**: Traditional method for finding a vehicle's location, but GPS has an accuracy of about 1-3 meters or sometimes up to 50 meters.
* **Onboard Sensors**: Used to measure distances to static obstacles like trees, poles, or walls, and their bearing in the local coordinate system of the car.
* **Map-Matching**: The process of matching onboard sensor observations with map information to estimate the transformation between the local car coordinate system and the global coordinate system of the map.

**Practical Notes**
-----------------

To solve the localization issue, you can use the following steps:

1. Use onboard sensors to measure distances to static obstacles and their bearing in the local coordinate system.
2. Match these observations with map information to estimate the transformation between the local car coordinate system and the global coordinate system of the map.
3. The goal is to achieve a transformation accuracy within 10 centimeters or less.

Note that this project assumes you have a global map of the environment, which can be used in conjunction with onboard sensor data to solve the localization issue.

## Transcript

Now assume there is a car that is totally lost, which means you, as a driver or as a car, have no clue where you are. Now you assume that you have a global map of the environment. In this example, you can see a map of the environment around the [INAUDIBLE] office in [INAUDIBLE]. Now, generally speaking, localization answers a question, where is our car in a given map with a high accuracy? And high accuracy means between three and 10 centimeters. In a traditional way, we use global navigation satellite systems to find the car, with respect to the map. But GPS is not precise enough. Most of the time, GPS has an accuracy of the worth of a lane-- about one to three meters. But sometimes it can be as broad as 10 to 50 meters. Clearly this is not reliable enough for a self-driving car. So you can't trust GPS. And you have to find another technique to localize yourself inside a given map. It is common practice to use the onboard sensor data, along with our global map, to solve the localization issue. So with the onboard sensors it is possible to measure distances to static obstacles, like trees, poles, or walls. We measure these distances, and the bearing of these static objects in the local coordinate system of our car. Now when you're lucky, the same obstacles that were observed by the onboard sensors are also part of the map. And, of course, the map has its own global coordinate system. To estimate where the car is in the map, you have to match the observations with the map information. And when you do it correctly, this results in a transformation between both coordinate systems-- the local car coordinate system and the global coordinate system of the map. This transformation should be as accurate as possible-- let's say within a range of 10 centimeters or less. If you are able to estimate this transformation, you solve the localization issue. So after this example, we can summarize. First, localization answers the question of where the car is in a given map within an accuracy of 10 centimeters or less. And second, onboard sensors are used to estimate the transformation between local measurements and a given map.
