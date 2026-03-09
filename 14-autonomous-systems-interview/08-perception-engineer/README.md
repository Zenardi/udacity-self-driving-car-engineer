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

<v English>Hi, Vienna.</v> <v English>It&#39;s really nice to meet you and I&#39;m glad to have you in today for our position.</v> <v English>Yes, nice to meet you, too. I&#39;m glad to be here.</v> <v English>So, one of the first things I want to ask you is</v> <v English>specific to the role for perception around sensor fusion.</v> <v English>Say, you had a robot or a self-driving car that had radar and lidar sensors on it,</v> <v English>how would you go about fusing that data to help you do something like object detection?</v> <v English>I think I&#39;d probably just go for a common filter</v> <v English>that tends to be really useful for doing things like that.</v> <v English>I can take some of the the less</v> <v English>precise location estimates that you would get with a radar,</v> <v English>for example, fuse that with</v> <v English>the more exact lidar and come up with the optimal estimation for that.</v> <v English>Great. In that situation,</v> <v English>say that you had different refresh rates between the radar and lidar,</v> <v English>how would you be able to deal with that?</v> <v English>Can you give me an example of when that might come into play?</v> <v English>Sure. Say, if you had a radar that refreshed at, say,</v> <v English>80 Hertz and the lidar only refreshed at 10 Hertz,</v> <v English>what would you do in that situation,</v> <v English>or would you need to do anything?</v> <v English>I&#39;m actually not sure.</v> <v English>I&#39;d have to look into that a little more.</v> <v English>Okay. Great.</v> <v English>It&#39;s not something I&#39;ve really been exposed to so far.</v> <v English>Sure.

Along with that, if you also,</v> <v English>say, had camera data coming in, how would you use that?</v> <v English>Would you bring that in as an input or would you have it, say,</v> <v English>that you bring the data out of the radar and lidar,</v> <v English>and then use that towards something else?</v> <v English>I think I definitely want to incorporate</v> <v English>the camera data as well and just really make use of</v> <v English>as many sensors and as much data as I could to build</v> <v English>up the most accurate estimation of the world around,</v> <v English>and really playing to the strengths of each sensor and where they</v> <v English>can overlap and share to help correct for each other&#39;s weaknesses.</v> <v English>Great. Very interesting.</v> <v English>Have you worked with any of these types of sensors before?</v> <v English>I&#39;ve been exposed to them a little bit at a high level</v> <v English>but not so much the hands-on aspects.</v> <v English>Okay. Great. That&#39;s all I have here on this topic,</v> <v English>so let&#39;s go ahead and go into the next one.</v> <v English>All right. Sounds good.</v>
