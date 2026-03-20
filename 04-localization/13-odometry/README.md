# Odometry

> Part of: **Introduction to Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=IusJ3cTusp8)

## Summary

**Odometry Method for Calculating New Position**
=====================================================

This README file summarizes the key concepts and practical notes from a lesson on using odometry, or motion sensor data, to calculate a mobile robot's new position.

**Key Concepts**
---------------

* **Odometer**: A device that measures how many times the wheels of a vehicle or robot have turned.
* **Wheel sensors**: Sensors attached to each wheel that measure rotation and provide odometry data.
* **Circumference of the wheel**: The distance around the outside of a wheel, used in calculations to determine distance traveled.
* **Distance traveled**: Calculated using the circumference of the wheel and odometry data from wheel sensors.
* **New position calculation**: The new position is calculated by adding the x and y components of the odometry data multiplied by the circumference of the wheel to the starting position.

**Practical Notes**
-------------------

To calculate a mobile robot's new position using odometry, you need:

```python
new_position = starting_position + (odometry_x * wheel_circumference, odometry_y * wheel_circumference)
```

Where `odometry_x` and `odometry_y` are the x and y components of the odometry data, and `wheel_circumference` is the distance around the outside of a wheel.

Note: Odometer measurements might fail to report accurate position estimates in situations such as:

* Slippery or uneven terrain
* Wheel slippage or loss of traction
* Sensor malfunctions or errors

## Transcript

Now that you know one way to calculate the car's new position, let's look at another commonly used method using odometry, or motion sensor data. For mobile robots, odometry calmly comes from wheel sensors that measure how many times the wheels of the vehicle or robot have turned. For instance, the sensor on this wheel would tell us it has turned twice. Given the circumference of the wheel and this odometry data, you can measure the distance traveled, as indicated by the red line. More specifically, the new position of the car is the starting position of the car plus the x and y components of the odometry, multiplied by the circumference of the wheel. Awesome. With this knowledge, next I want you to think about when odometry measurements might fail to report accurate position estimates.
