# Mapping Overview

> Part of: **Utilizing Scan Matching**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=At-u7-H5Dd4)

## Summary

**Mapping with Transformation Scans**
=====================================

This lesson covers the concept of mapping using transformation scans, which is an essential technique for creating accurate maps of environments. By applying transformation information to individual scans, you can create a comprehensive map of the environment.

### Key Concepts
* **Transformation scans**: A method of combining multiple scans by applying transformation information to align them properly.
* **Ground truth**: A reference point or data that serves as a basis for comparison or alignment, in this case, the ego car's position and orientation in the environment.
* **Scan matching**: The process of comparing two or more scans to determine their relative positions and orientations.
* **SLAM (Simultaneous Localization and Mapping)**: A technique for creating maps while simultaneously localizing a robot or vehicle within that map.

### Practical Notes
When implementing transformation scans, you can use the following steps:

1. Collect multiple scans of an environment using a simulator or real-world data.
2. Apply transformation information to each scan using techniques such as ICP (Iterative Closest Point) or NDT (Normal Distributions Transform).
3. Use the transformed scans to create a comprehensive map of the environment.

Note that this lesson also touches on the concept of SLAM, which can be used to create maps without any ground truth by applying transformation information from scan matching output.

## Transcript

Now I'd like to talk about doing some mapping with transformation scans, which is a fun thing to be doing when you're driving around and collecting any scans and doing the localization. Well, if you're localizing and you have that scan, you can piece them all together and create a map. In this mapping exercise, you'll actually be driving the car around in the simulator, and in this part, you'll actually be using the transformation information directly from the simulator, so you'll have a ground truth of where the ego car is with its position and orientation in the environment. That'll properly align these scans. Then those scans are applied by that transform and summed all together to create the overall map.

Now, what's really interesting, I think is, you could take this and adapt it. We're talking about scan matching, and here we have like a ground truth. But if that T is from the scan matching that you're applying either from ICP or NDT, then effectively, you can be creating this map yourself without any ground truth, but just that transformation information from your scanned matching output. If you do this, you're solving SLAM, the simultaneous localization and mapping. That can be something very interesting to take a look at and you'll see in some of the research papers, that's also talked about in more detail as well.

## Additional Content

## Mapping Overview
* Having scans with the corresponding transformations can then be summed together to create an overall scan map
* In the upcoming exercise, the transformation information is the ground truth from the simulator, so the map will be perfect (unless there is high latency between scan recording and transformation)
* SLAM (Simultaneous Localization and Mapping) can be done by using the scan matching transformation output instead of the ground truth transformation from the simulator
