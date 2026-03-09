# Multi-Target Tracking Overview

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=oofCSNgJt3I)

## Summary

**Track Management for Multi-Object Tracking**

This README file provides an overview of the key concepts and practical notes from a lesson on track management for multi-object tracking in self-driving cars.

### Key Concepts

* **Multi-Object Tracking**: The ability to track multiple objects (e.g. vehicles) simultaneously using LiDAR measurements.
* **Track Management**: A module responsible for initializing new tracks, deleting old tracks, and providing a confidence value (track score) for each track.
* **Data Association Problem**: Determining which measurement originated from which track.
* **Track State**: A classification of a track as either tentative (uncertain or new), confirm (stable with multiple measurements), or deleted.
* **Track Score**: A confidence value indicating the likelihood that an object exists, ranging from 0 to 1.

### Practical Notes

The lesson covers the following practical steps:

* Predict all tracks to the next measurement timestamp using an Extended Kalman Filter (EKF).
* Associate each measurement with a track using data association.
* Update each track with its corresponding measurement and update the track score accordingly.
* Initialize new tracks when a new vehicle appears in the field of view.
* Delete old tracks that have not been updated for multiple cycles.
* Remove tracks with low confidence or high uncertainty.

The lesson also introduces a flow chart illustrating the overall process, which includes:

1. Predicting all tracks to the next timestamp
2. Associating measurements with tracks
3. Updating tracks and updating track scores
4. Initializing new tracks
5. Deleting old tracks
6. Removing tracks with low confidence or high uncertainty

This lesson builds upon previous knowledge of EKF-based tracking and introduces more complex scenarios involving multiple objects, missed detections, false positives, and track management.

## Transcript

Imagine we're sitting in the left self-driving car and our unbarred LiDAR takes measurements in the pink field of you. In the last lesson, we learned how to trick the red vehicle over time by predicting the track to the next timestamp and then updating with the LiDAR measurements. In reality, however, there might be several objects, for example; two vehicles, and therefore two measurements at the same time stamp. We simply use two track in this case, and in each time stamp, we predict twice and we update twice. Since we get two measurements, both objects have been detected by the LiDAR, therefore, the measurements are true positive detections.

However, the reality is more complicated. We may also have missed detections of false negatives, which means that objects are there, but the LiDAR failed to generate a measurement. This may be caused by occlusions, sensor failures, or low reflectivity of the object. Miss detections are dangerous because we might overrun an object if the sensors fail to perceive them, so we have to handle false negatives in the tracking. In addition, there may be false positive measurements that originated from no vehicle, but from a clutters source.

LiDAR might generate a false positive measurement, for example, if there's a very small but reflective object, like a guard rail reflector lying on the street. These false positive measurements are also called clutter measurements. We have to remove these clutter measurements through sensor fusion, otherwise, there will be so-called ghost tracks, and the self-driving car might do an emergency braking even though there's no obstacle. Finally, there may be new vehicles appearing or other vehicles disappearing from our field of view, so we need a logic to initialize new tracks and to delete old tracks. These tasks might seem simple and are handled by a human driver effortlessly, but remember, all our self-driving car sees, is this.

Based on these measurements, should our self-driving car break or not? To decide this, we need a module called Track management. The track management handles all of the described tasks; it initializes new tracks, deletes old tracks, and provides a tracks score or confidence value, we will learn more about track management in this lesson. Here is the overall flow chart for multi-talented tracking. The green boxes are the topics we will learn in this lesson.

We've already covered the blue boxes in the last lesson, the predict and update steps with an EKF, the difference is that now we have multiple objects in the vehicles environment and we also receive multiple measurements at each time stamp. In the first step, we have to predict all tracks to the next measurement timestamp. Then we have to determine which measurement has originated from which track in order to decide which track to update with which measurement, this is called the data association problem. After we assigned all measurements to all tracks, we update each track with the corresponding measurement. We will also introduce a track score in this lesson, where a highest score means the fusion module is quite certain that there really is an object.

We will introduce a track state, for example, tentative, for uncertain or new tracks, and confirm, for stable tracks that have been detected over many measurements cycles. After the Track has been updated, we may increase the track score and set a new track state. Once we have updated all tracks with the associated measurements, there may be tracks left that have not been updated, if the track is in the census field of view but hasn't been detected, we decrease the track score because the real object might have left our field of view or it might be a false positive ghost track that doesn't exist in reality. We may also have an unsigned measurements left. In this case, a new vehicle might have appeared from around the corner, so we initialize a new track where the measurement indicates.

Finally, we check if there are tracks with a very low confidence or pick uncertainty, and we remove such tracks. After all these steps, we repeat the whole cycle, predict all remaining tracks to the next timestamp, associate the measurements to the track's update, run the track management, and so on.

## Images

![Flowchart of multi-target tracking steps you will learn in this lesson](images/mtt-data-flow.png)
*Overview of multi-target tracking steps you will learn in this lesson*

## Additional Content

## Multi-Target Tracking Overview
A multi-target tracking system has to fulfill the following tasks in addition to a single-target tracking:

- Data Association:
  - Associate measurements to tracks
- Track Management:
  - Initialize new tracks
  - Delete old tracks
  - Assign some confidence value to a track
