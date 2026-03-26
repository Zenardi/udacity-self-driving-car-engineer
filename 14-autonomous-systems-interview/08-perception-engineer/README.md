# Perception Engineer

> Part of: **Autonomous Systems Interview Practice**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=jvJBciGU5o0)

## Summary

**Sensor Fusion for Perception**
=====================================

This README file provides a summary of key concepts related to sensor fusion for perception, as discussed in the Udacity lesson.

### Key Concepts

* **Sensor Fusion**: The process of combining data from multiple sensors to improve accuracy and robustness.
* **Kalman Filter**: A common algorithm used for fusing data from different sensors, particularly useful for object detection.
* **Optimal Estimation**: The goal of sensor fusion is to obtain the most accurate estimation of the world around us by combining data from multiple sources.
* **Sensor Refresh Rates**: Different sensors have varying refresh rates (e.g., 80 Hertz for radar and 10 Hertz for lidar), which can impact the fusion process.

### Practical Notes

When dealing with different sensor refresh rates, such as a radar refreshing at 80 Hertz and a lidar refreshing at 10 Hertz, you may need to consider techniques like:

* **Weighting**: Assigning weights to each sensor's data based on its refresh rate and accuracy.
* **Data Buffering**: Storing data from slower-refresh-rate sensors (like lidar) in a buffer until the faster-refresh-rate sensor (like radar) has new data available.

Incorporating camera data into the fusion process can provide additional benefits, such as:

* **Visual Odometry**: Using camera data to estimate the robot's or self-driving car's motion and position.
* **Object Detection**: Combining camera data with other sensors' data to improve object detection accuracy.

Note that this is a high-level overview of sensor fusion for perception, and further study and experimentation are necessary to fully understand and implement these concepts.

## Transcript

Hi, Vienna. It's really nice to meet you and I'm glad to have you in today for our position. Yes, nice to meet you, too. I'm glad to be here. So, one of the first things I want to ask you is specific to the role for perception around sensor fusion. Say, you had a robot or a self-driving car that had radar and lidar sensors on it, how would you go about fusing that data to help you do something like object detection? I think I'd probably just go for a common filter that tends to be really useful for doing things like that. I can take some of the the less precise location estimates that you would get with a radar, for example, fuse that with the more exact lidar and come up with the optimal estimation for that. Great. In that situation, say that you had different refresh rates between the radar and lidar, how would you be able to deal with that? Can you give me an example of when that might come into play? Sure. Say, if you had a radar that refreshed at, say, 80 Hertz and the lidar only refreshed at 10 Hertz, what would you do in that situation, or would you need to do anything? I'm actually not sure. I'd have to look into that a little more. Okay. Great. It's not something I've really been exposed to so far. Sure.

Along with that, if you also, say, had camera data coming in, how would you use that? Would you bring that in as an input or would you have it, say, that you bring the data out of the radar and lidar, and then use that towards something else? I think I definitely want to incorporate the camera data as well and just really make use of as many sensors and as much data as I could to build up the most accurate estimation of the world around, and really playing to the strengths of each sensor and where they can overlap and share to help correct for each other's weaknesses. Great. Very interesting. Have you worked with any of these types of sensors before? I've been exposed to them a little bit at a high level but not so much the hands-on aspects. Okay. Great. That's all I have here on this topic, so let's go ahead and go into the next one. All right. Sounds good.