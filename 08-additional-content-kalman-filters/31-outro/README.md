# Outro

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=G3soGuQeHGU)

## Summary

**Sensor Fusion and Autonomous Vehicles**
=====================================

This lesson covers the basics of combining LIDAR and RADAR measurements using extended and unsensed comment filters, a crucial skill in autonomous vehicle development. The instructor highlights the importance of sensor fusion in the overall technology stack for self-driving cars.

**Key Concepts**
---------------

* **Sensor Fusion**: Combining data from multiple sensors (LIDAR, RADAR) to create a more accurate representation of the surrounding world.
* **Extended and Unensed Comment Filters**: Techniques used to combine LIDAR and RADAR measurements.
* **Object Level Fusion**: Using sensor fusion output as input for object detection and tracking.
* **Sensor Fusion Block**: A module that combines data from multiple sensors, which can be applied at various processing steps.

**Practical Notes**
------------------

The lesson emphasizes the importance of handling complex scenarios, such as multiple objects in the scene. The instructor notes that the core techniques learned in this lesson are essential for extending the sensor fusion block to handle these more complicated cases. Additionally, the instructor highlights the critical role of sensor fusion in an autonomous driving system, where other components rely on fused data.

Note: There is no specific code or formula provided in the transcript, but the concepts and techniques discussed can be applied to various programming languages and frameworks used in autonomous vehicle development.

## Transcript

<v English>Congratulations, combining LIDAR and</v>
<v English>RADAR measurements with the help of</v> <v English>extended and unsended comment</v>
<v English>filters is incredibly impressive.</v> <v English>These are core skills that we use on</v>
<v English>the Sensor Fusion team at Mercedes-Benz.</v> <v English>>> Let's think about where Sensor Fusion</v>
<v English>fits into the entire autonomous vehicle</v> <v English>technology stack.</v> <v English>First, sensors record the data, then</v>
<v English>there are pre-processing steps such as</v> <v English>clustering algorithms, or more complex</v>
<v English>solutions to detect object hypothesis.</v> <v English>And finally, we can use these hypothesis</v>
<v English>as input for object level fusion.</v> <v English>>> Inside the sensor fusion block,</v> <v English>we combined that data together</v>
<v English>like you did in this lesson.</v> <v English>And this is not the only possible flow,</v> <v English>we can apply sensor fusion at</v>
<v English>each of these processing steps.</v> <v English>>> Once we have the more consistent</v>
<v English>representation of the surrounding world,</v> <v English>we pass the results to other part of</v>
<v English>the autonomous vehicle system Further</v> <v English>down the line, different teams will</v>
<v English>use this data to localize the vehicle,</v> <v English>control the vehicle, and</v>
<v English>plan the vehicle's path.</v> <v English>>> It's also worth thinking about ways</v>
<v English>in which the world is more complicated</v> <v English>that what we've discussed so far.</v> <v English>For example, in this lesson,</v> <v English>we have assumed there is</v>
<v English>only one object to track.</v> <v English>But what if there are many</v>
<v English>cars on the street?</v> <v English>Then you have to find out which</v>
<v English>measurement belongs to which vehicle,</v> <v English>that makes sensor fusion even harder.</v> <v English>>> But the core techniques you have</v>
<v English>learned in this lesson are the key to</v> <v English>extended the sensor fusion block to</v>
<v English>handle these more complicated scenarios.</v> <v English>>> Sensor fusion is a critical part</v>
<v English>of an autonomous driving system and</v> <v English>the other parts of the system</v>
<v English>rely on this data.</v> <v English>>> In future modules, you will learn</v>
<v English>about how the components of this system</v> <v English>used fused sensor data to</v>
<v English>complete their functions.</v> <v English>Good luck on the final</v>
<v English>sensor fusion project.</v>
