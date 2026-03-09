# Lesson Summary

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2fmJ_vpR7Gc)

## Summary

**Tracking Multiple Objects Simultaneously**
=============================================

This lesson covers the key concepts and techniques for tracking multiple objects simultaneously, including initializing new tracks, checking sensor visibility range, monitoring track confidence, and evaluating tracking performance.

### Key Concepts

* **Track Initialization**: A function that initializes new tracks from unassigned measurements.
* **Sensor Visibility Range**: A function to check a sensor's visibility range to determine which tracks can be updated.
* **Track Score**: A measure of the confidence in our tracking results, used to monitor track state.
* **Track State**: A variable that monitors the confidence in our tracking results and determines when to delete old tracks.
* **Nearest Neighbor Data Association**: A simple algorithm for associating measurements to tracks.
* **Gating Method**: A technique to reduce computational complexity by filtering out unlikely associations.
* **Root Mean Square Error (RMSE)**: A metric used to evaluate the performance of our tracking system.

### Practical Notes

To implement this lesson, you will need to write functions that initialize new tracks and check sensor visibility range. You will also need to use a nearest neighbor data association algorithm and a gating method to filter out unlikely associations. Finally, you can use RMSE to evaluate your tracking performance in the final project.

## Transcript

Congratulations, you've made it to the end of the lesson. In this lesson, you have learned how to track multiple objects simultaneously. You have implemented a function that initializes new tracks from unassigned measurements, as well as a function to check a sensor's visibility range. We have also defined a track score, and a track state to monitor the confidence in our tracking results, and we have learned when to delete old tracks. You've implemented a simple nearest neighbor data association in order to associate measurements to tracks, and you've implemented a gating method to reduce computational complexity.

Finally, you have learned how to evaluate your tracking performance using root mean square errors. Let's see how you can apply all your new tracking skills to a real-world problem in the final project.

## Additional Content

## Lesson Summary
We have covered the following topics in this lesson:

- Track initialization
- Track deletion
- Visibility reasoning
- Confidence measures
- Data association
- Gating
- Evaluation with RMSE
