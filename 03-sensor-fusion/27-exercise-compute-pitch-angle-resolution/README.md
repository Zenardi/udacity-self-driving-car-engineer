# Exercise: Compute Pitch Angle Resolution

> Part of: **The Lidar Sensor**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lbck7cHHy_g)

## Summary

**Extracting Range Images and Understanding Angular Measures**
===========================================================

This lesson builds on previous concepts by guiding you through a practical exercise that extracts range images from frames. You'll complete a function to print the pitch angle resolution in degrees.

### Key Concepts
* **Range Images**: A representation of the distance between objects in an image.
* **Pitch Angle Resolution**: The minimum change in pitch angle that can be detected, measured in degrees (0.32° in this exercise).
* **Angular Minutes**: A unit of measure used to express the accuracy of calibration data.

### Practical Notes
To complete the exercise:

1. Open the file `L1_exercises.pie` and locate the function `print_pitch_resolution`.
2. Complete the function to print the pitch angle resolution in degrees.
3. Verify that the resulting pitch angle resolution is 0.32° when executed correctly.

Note: This lesson also includes a quiz on angular minutes, which you can complete to reinforce your understanding of this concept.

## Transcript

Now, welcome to your first exercise in this chapter here. I assume that you have looked at the previous example and executed the codes to extract range images from frames. Now that you're familiar with the procedure and with the structure of data fields in a way more frame please now complete the function called print underscore, pitch underscore resolution which you will find in the file, L1 underscore exercises dot pie. Your job is to print the pitch angle resolution in degrees to the terminal. If you have done everything correctly, the resulting pitch angle resolution should be at 0.32 degrees.

Once you are ready please also complete the quiz below to get an understanding of the concept of angular minutes which is unit of measure, you will often find the engineering to express the accuracy of calibration data.

## Additional Content

## Exercise: Compute Pitch Angle Resolution

#### Files to work in:
- `basic_loop.py` 
- `lesson1-lidar-sensor/exercises/starter/l1_exercises.py`
Now that you are familiar with the resolution and basic structure of a range image, you will have a look at the data within the cells. From the documentation within `dataset.proto`  (lines 174-178) we know that the inner dimensions of a range image cell are `[range, intensity, elongation, is_in_no_label_zone]`. In this course, we will focus on the first two entries, starting with the actual range information. 

As we have discussed earlier, "range" refers to the straight-line distance between the laser emitter and the target. The direction in space in which the target is located, is given by both the inclination and the azimuth angle. To access the range data, we simply need to access the first layer of the range image, i.e. `ri[:,:,0]`.
