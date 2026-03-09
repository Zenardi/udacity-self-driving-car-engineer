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

<v English>Now that you know</v>
<v English>one way to calculate the car's</v> <v English>new position, let's look at</v>
<v English>another commonly used method</v> <v English>using odometry, or</v>
<v English>motion sensor data.</v> <v English>For mobile robots, odometry</v>
<v English>calmly comes from wheel sensors</v> <v English>that measure how many times the</v>
<v English>wheels of the vehicle or robot</v> <v English>have turned.</v> <v English>For instance, the</v>
<v English>sensor on this wheel</v> <v English>would tell us it</v>
<v English>has turned twice.</v> <v English>Given the circumference of the</v>
<v English>wheel and this odometry data,</v> <v English>you can measure the</v>
<v English>distance traveled,</v> <v English>as indicated by the red line.</v> <v English>More specifically, the</v>
<v English>new position of the car</v> <v English>is the starting</v>
<v English>position of the car</v> <v English>plus the x and y components</v>
<v English>of the odometry, multiplied</v> <v English>by the circumference</v>
<v English>of the wheel.</v> <v English>Awesome.</v> <v English>With this knowledge,</v>
<v English>next I want you</v> <v English>to think about when</v>
<v English>odometry measurements might</v> <v English>fail to report accurate</v>
<v English>position estimates.</v>
