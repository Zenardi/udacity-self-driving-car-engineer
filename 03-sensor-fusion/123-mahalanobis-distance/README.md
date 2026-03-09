# Mahalanobis Distance

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=rZP3Mq6ciz8)

## Summary

**Multi-Target Tracking: Data Association Module**
==============================================

The data association module is a crucial component of multi-target tracking systems. It determines which track to update with which measurement by calculating track-measurement pairs that indicate which measurement likely originated from which track.

### Key Concepts

* **Data Association**: The process of determining which track to update with which measurement.
* **Track-Measurement Pairs**: A set of associations between tracks and measurements, indicating the likelihood of each measurement originating from a particular track.
* **Euclidean Distance**: A simple distance metric that calculates the straight-line distance between two points in space. Used for associating measurements with tracks when the measurement is directly comparable to the track state (e.g., LIDAR).
* **Mahalanobis Distance (MHD)**: A more advanced distance metric that incorporates the uncertainty of both the track and measurement. It calculates a weighted distance based on the residual covariance, making it suitable for situations where the track has high position uncertainty.
* **Residual Covariance S**: The estimation error covariance P transformed to measurement space plus the measurement covariance. Used in calculating the Mahalanobis distance.

### Practical Notes

To implement the data association module, you can use either Euclidean distance or Mahalanobis distance as your distance metric. When using Euclidean distance, ensure that the measurement is directly comparable to the track state (e.g., LIDAR). For situations with high position uncertainty in the track, consider using the Mahalanobis distance to incorporate the uncertainty into the association process.

Example code for calculating the Mahalanobis distance:
```python
import numpy as np

def mahalanobis_distance(x, P, h):
    # Calculate residual covariance S
    S = np.linalg.inv(P) + np.linalg.inv(h)

    # Calculate weighted distance
    d = np.sqrt(np.dot((x - h), np.dot(S, (x - h))))

    return d
```
Note: This code snippet is a simplified example and may require modifications to fit your specific implementation.

## Transcript

Well done. You've already covered a big part of the multi-target tracking lesson. You have implemented your own track initialization. We have designed a track management module that calculates a track's score and a track state and to know when to delete old tracks. Finally, you have implemented a visibility reasoning for a sensor fusion molecule.

We have one major topic for multi-target tracking left. How can we decide which track to update with which measurement? This is the task of the data association module. The data association module calculates track measurement pairs that tell us which measurement probably originated from which track. Let's go back to our multi-day target tracking example.

Remember that there are a lot of ambiguous situations that may be through positive track measurement associations, but also measurements without associated tracks or tracks that have not been detected. Let's simplify this image and only keep what the fusion system knows about the environment. We have a number of tricks depicted by circles and a number of measurements depicted by crosses that have to be associated to track measurement pairs. For the association, we make the following assumptions. Each track generates at most one measurement, and each measurement originates from at most one track.

With these assumptions, we have to associate measurements to tracks. A simple approach is to update each track with the closest measurement. We would update this track with this measurement, this trick with this measurement, and so on. That is basically what we will do. We only have to decide which distance measure to use.

Consider this example where we have one measurement and have to decide which of the two tracks to update with the measurement. We could use a simple Euclidean distance between the track position X and the measurement C. Note that in general, we have to transform X to the measurement space with the measurement function h. But for LIDAR, since we measure directly the position, we can compare the state components with the measurement components. Using Euclidean distance, the measurement is closer to the right track, so we would update the right track with the measurement and not the left track.

However, we also have the tracks position uncertainty given by the covariance P. Now imagine that the left track contains a high position uncertainty and therefore a large covariance. Basically, the true position of the track could be somewhere inside this big ellipse. The right track is much more stable and precise. The right ellipse, which contains the possible true locations, is much smaller.

We also see that the measurement lies outside of the right ellipse. It is very unlikely that the measurement originated from the right track. We should better associate the measurement to the left track instead of the right one. Therefore, we need a different distance metric that incorporates the uncertainty. This is exactly what the so-called Mahalanobis distance or MHD does.

Like the Euclidean distance, the image d compares the state position with the measurement. Or in other words, the MHD uses the residual gamma. The main difference is that it also includes the inverse of the residual covariance S. Remember that S basically is the estimation error covariance P transformed to measurement space plus the measurement covariance. You can imagine S as similar to the blue ellipses.

Using the inverse means that a big ellipse will result in a smaller distance and vice versa. Therefore, we rather update an uncertain track with the big covariance ellipse, than a precise track with small covariance. In this example, we would update the left track and not the right one just as desired.

## Additional Content

## Mahalanobis Distance
- The

$\textbf{data association}$

assigns measurements to tracks and decides which track to update with which measurement.
- As a distance measure for this decision, the

$\textbf{Mahalanobis distance}$

is used (note that it actually contains a squared distance):

$$d(\mathbf x, \mathbf z)= \gamma^T\mathbf S^{-1}\gamma = (\mathbf z - h(\mathbf x))^T\mathbf S^{-1}(\mathbf z - h(\mathbf x))$$
