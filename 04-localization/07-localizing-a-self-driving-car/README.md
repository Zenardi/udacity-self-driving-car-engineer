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

<v English>Now assume there is</v>
<v English>a car that is totally lost,</v> <v English>which means you, as</v>
<v English>a driver or as a car,</v> <v English>have no clue where you are.</v> <v English>Now you assume that you have a</v>
<v English>global map of the environment.</v> <v English>In this example,</v>
<v English>you can see a map</v> <v English>of the environment around</v>
<v English>the [INAUDIBLE] office</v> <v English>in [INAUDIBLE].</v> <v English>Now, generally</v>
<v English>speaking, localization</v> <v English>answers a question, where</v>
<v English>is our car in a given</v> <v English>map with a high accuracy?</v> <v English>And high accuracy means between</v>
<v English>three and 10 centimeters.</v> <v English>In a traditional way, we use</v>
<v English>global navigation satellite</v> <v English>systems to find the car,</v>
<v English>with respect to the map.</v> <v English>But GPS is not precise enough.</v> <v English>Most of the time,</v>
<v English>GPS has an accuracy</v> <v English>of the worth of a lane--</v>
<v English>about one to three meters.</v> <v English>But sometimes it can be as</v>
<v English>broad as 10 to 50 meters.</v> <v English>Clearly this is not reliable</v>
<v English>enough for a self-driving car.</v> <v English>So you can't trust GPS.</v> <v English>And you have to find another</v>
<v English>technique to localize yourself</v> <v English>inside a given map.</v> <v English>It is common practice to</v>
<v English>use the onboard sensor</v> <v English>data, along with our global</v>
<v English>map, to solve the localization</v> <v English>issue.</v> <v English>So with the onboard</v>
<v English>sensors it is</v> <v English>possible to measure distances</v>
<v English>to static obstacles,</v> <v English>like trees, poles, or walls.</v> <v English>We measure these</v>
<v English>distances, and the bearing</v> <v English>of these static</v>
<v English>objects in the local</v> <v English>coordinate system of our car.</v> <v English>Now when you're lucky,</v>
<v English>the same obstacles</v> <v English>that were observed by</v>
<v English>the onboard sensors</v> <v English>are also part of the map.</v> <v English>And, of course, the map has its</v>
<v English>own global coordinate system.</v> <v English>To estimate where the</v>
<v English>car is in the map,</v> <v English>you have to match</v>
<v English>the observations</v> <v English>with the map information.</v> <v English>And when you do it</v>
<v English>correctly, this results</v> <v English>in a transformation between</v>
<v English>both coordinate systems--</v> <v English>the local car coordinate system</v>
<v English>and the global coordinate</v> <v English>system of the map.</v> <v English>This transformation</v>
<v English>should be as accurate</v> <v English>as possible-- let's say within</v>
<v English>a range of 10 centimeters</v> <v English>or less.</v> <v English>If you are able to estimate</v>
<v English>this transformation,</v> <v English>you solve the</v>
<v English>localization issue.</v> <v English>So after this example,</v>
<v English>we can summarize.</v> <v English>First, localization</v>
<v English>answers the question</v> <v English>of where the car is in a given</v>
<v English>map within an accuracy of 10</v> <v English>centimeters or less.</v> <v English>And second, onboard</v>
<v English>sensors are used</v> <v English>to estimate the transformation</v>
<v English>between local measurements</v> <v English>and a given map.</v>
