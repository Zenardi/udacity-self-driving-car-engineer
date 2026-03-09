# Visibility

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=RYvzvb279mQ)

## Summary

**Tracking Flowchart and Sensor Fusion**

This README file summarizes the key concepts and practical steps introduced in the Udacity lesson on tracking flowcharts and sensor fusion. The lesson covers the importance of considering sensor visibility when managing tracks.

### Key Concepts

* **Track Score**: a value that increases or decreases based on measurements, used to determine the track state.
* **Sensor Fusion**: combining data from multiple sensors to improve accuracy and robustness.
* **Visibility Reasoning**: determining whether an object is in the visible area of a sensor.
* **Detection Probabilities**: calculating the probability that an object is visible for each sensor.

### Practical Notes

To implement visibility reasoning, you will need to:

* Calculate whether an object is within the field of view of each sensor using a simple formula.
* Modify the track management module to consider sensor visibility when updating track scores.
* Use detection probabilities or occlusion reasoning (optional) to improve accuracy.

Example code for calculating visibility:
```python
def is_visible(obj, sensor):
    # Calculate if obj is within sensor's field of view
    return (obj.x - sensor.x)**2 + (obj.y - sensor.y)**2 <= sensor.range**2
```
Note: This is a simplified example and actual implementation may vary depending on the specific requirements and sensors used.

## Transcript

Here we are in the tracking flowchart. So far we have covered the fall law green boxes. When a track gets updated with the measurement, we increase the track score and check if you have to set a new track state. For example, confirmed instead of tentative. On the other hand, if a track does not get updated with a measurement, we decrease the track score.

In case we have unassigned measurements left, we initialize new tracks. Finally, if a track has a very low track score or a big position uncertainty, we delete this track. There is one more important topic to cover in the track management. We said, that if a track was not detected by a sensor, we decrease the score. But remember that this lesson is about sensor fusion, so we have a Lidar and a camera whose field of use may differ.

For example, we have a Lidar with a big opening angle depicted by this blue area here, and we might have a camera with a smaller opening angle. In reality, we may even have many sensors that do not have an overlapping field of view at all. Consider, for example, those surround cameras from the Rameau open data set. Now, imagine there's a target that can only be seen by our Lidar. What will happen in our current track management module?

Assume that in every measurement cycle, the Lidar will detect the object, so the track score will increase. But in the following camera measurements cycle, the camera will not deliver any measurements because the target is not visible for the camera, so the score will decrease again. Therefore, the score will oscillate and stabilize around 0.5. This is not what we want because we know that the camera can't see the object, so only Lidar detections should be counted and the track score should tend toward one. Otherwise, with the track score around 0.5, the track state can never go above a tentative state.

Even worse, think of what happens, if the red track has been in the common field of view and has been confirmed before then, the score will drop to 0.5 once the object can only be seen by one sensor. The track management will delete the track even though it is perfectly visible by the Lidar. To avoid these problems, we need a visibility reasoning. The track management module needs to consider whether an object is in the visible area of a sensor on not. More advanced sensor fusion systems will use detection probabilities for each sensor that consists of a probability that the object is visible for this sensor.

One could also include occlusion reasoning through other dynamic objects. In our case, we will use a simple calculation whether an object is in a sensor's field of view. If yes, the track management will be executed. But otherwise, the track score will remain the same, as before. With this visibility reasoning, the red object can be confirmed only by Lidar and the tracks score will tend toward one.

In the next exercise, I want you to implement this sense of visibility check.

## Additional Content

## Visibility
- In sensor fusion systems, each sensor typically has a different field of view.
- We need a detection probability or visibility reasoning to avoid oscillating track scores.
