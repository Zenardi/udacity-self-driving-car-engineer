# Odometry Errors: Solution

> Part of: **Introduction to Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=znygdVnOQyY)

## Summary

**Odometry and Sensor Errors**
=====================================

This summary covers the key concepts related to odometry, a technique used in robotics to estimate a vehicle's position and orientation by measuring the rotation of its wheels. We'll explore how different road conditions affect the accuracy of odometry.

### Key Concepts
* **Wheel Odometry**: A method for estimating a vehicle's position and orientation by measuring the rotation of its wheels.
* **Sensor Errors**: Wheel odometry can incur large errors due to wheel slip, especially on wet or bumpy roads.
* **Expected Circumference**: On dry paved roads, the wheels travel a distance close to their expected circumference.
* **Distance Vectors**: The sum of the absolute magnitude of all distance vectors is equal to the expected distance traveled.

### Practical Notes
When implementing odometry in a real-world application:

* Be aware that wheel odometry may not be accurate on wet or bumpy roads due to wheel slip and sliding.
* Consider using other sensors, such as GPS or lidar, to supplement odometry data for more accurate positioning.
* On roads with lots of turns, wheel odometry can work well despite changes in the vehicle's heading.

## Transcript

Great. Let's look at each of the possible answers from the quiz. On a sleek wet road wheel encoder odometry will incur large errors, because the wheels will slip, causing them to travel less distance than expected. In addition, the wheels will also slide while braking further contributing to sensor errors. On dry paved roads however, the wheels will travel a distance very close to the expected circumference of the wheel.

Roads with lots of bumps also create problems for odometry, because we are assuming the car travels a straight distance in the direction of its heading. In reality, with a bumpy road, the car is traveling much of its distance not in a straight line but up and down. On a road with lots of turns wheel odometry works well because even though the heading of the car is changing it's still moving the expected distance in the direction of its Ya. Notice that despite the fact that the distance vectors for this car are of different Ya angles the sum of the absolute magnitude of all the vectors is the same as the expected distance traveled.
