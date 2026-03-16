# Track Score

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=4Djh83AupUA)

## Summary

**Track Scoring for Lidar Data**
=====================================

This project explores the concept of track scoring for lidar data in self-driving cars. Track scoring is a method used to determine whether a detected object is real or a false positive, also known as a "ghost track".

### Key Concepts

* **Tracks**: Representations of detected objects in the environment.
* **Ghost tracks**: False positives that are not actual objects.
* **Track score** (or existence probability): A measure of confidence in a track's validity, ranging from 0 to 1.
* **Normalization**: The process of scaling a value between 0 and 1.

### Practical Notes

To implement track scoring, you can use the following steps:

* Initialize a track score for each detected object to 0.
* For each frame, update the track score by adding the number of detections in that frame, normalized over a fixed window size (e.g. last 5 frames).
* A high track score close to 1 indicates a real object, while a low score close to 0 suggests a false positive.

Example code:
```python
def calculate_track_score(track_id, num_detections, window_size):
    # Calculate the number of detections in the last window_size frames
    num_detections_in_window = sum(num_detections[-window_size:])

    # Normalize the value between 0 and 1
    track_score = num_detections_in_window / window_size

    return track_score
```
Note that this is a simplified example, and more advanced track score calculations or existence probabilities can be used in practice.

## Transcript

Imagine the lidar of our self-driving car generates two measurements and our track list is still empty. In this case, we would initialize two new tracks, Track 1 and Track 2. But how can we determine whether there really is an object? In this example, Track 1 represents a real vehicle that has just appeared in our field of view. When Track 1 continues to go ahead, our self-driving vehicle should react and break.

Track 2, on the other hand, does not represent a real object. The measurement was a false positive clutter measurement, therefore, our track is a so-called ghost track. We should remove this ghost track as soon as possible in order to not do an unnecessary emergency braking. How can we distinguish between a true positive track and a false positive ghost track? To this end, a track score or existence probability can help.

Let's define a very simple track score to monitor our confidence in the track. We can simply define the score as the number of detections in the last n frames, normalized over n. The score could count, for example, how many detections we had in the last five frames. Let's look at our example above and assume that the lidar detects our true positive Track 1 in every frame. The false positive Track 2, on the other hand only originated from a single clutter measurement and is not updated anymore afterwards.

In the first frame, both tracks have been detected, ones in the last five frames, so the initial score is 0.2. In the next time step, the true positive Track 1 is detected again, so we can calculate the score to be 0.4. The false positive Track 2 however, is not updated and the score remains at 0.2. It goes on, Track 1 has a rapidly increasing score until it reaches the maximum at one. Whereas Track 2 gets not updated until the score finally drops to zero again.

That's it, this very simple score can help you distinguish between false and true tracks. Note that you can define your own confidence measure. There are much more advanced tracks score calculations or existence probabilities, but the overall idea remains the same. A value close to one means a high confidence in the track, whereas the low value close to zero means that it might be a false positive ghost track.

## Additional Content

## Track Score
We can define a simple $\textbf{track score}$ by setting:

$$\text{score} = \frac{\#\text{detections in last $n$ frames}}{n}$$

There are many other possibilities to define a track score, confidence or existence probability, you can even define your own!
