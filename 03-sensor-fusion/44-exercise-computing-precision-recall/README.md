# Exercise: Computing Precision & Recall

> Part of: ** Detecting Objects in Lidar**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=MOEFsAGO2V0)

## Summary

**Evaluating Object Detection Performance with Accumulated Metrics**
===========================================================

This lesson introduces a more efficient way to evaluate object detection performance by using accumulated metrics. This approach is particularly useful when working with large datasets.

### Key Concepts
* **Precision**: A measure of how accurate the detector is, calculated as the number of true positives divided by the sum of true positives and false positives.
* **Recall**: A measure of how thorough the detector is, calculated as the number of true positives divided by the sum of true positives and false negatives.
* **True Positives (TP)**: Correctly detected objects that match their corresponding ground truth labels.
* **False Positives (FP)**: Incorrectly detected objects that do not match any ground truth label.
* **True Negatives (TN)**: Undetected objects that do not have a corresponding ground truth label.
* **False Negatives (FN)**: Missed objects that should have been detected but were not.

### Practical Notes
When implementing this approach, you will need to:

1. Use an automatic matching algorithm to compare detections and ground truth labels across multiple frames.
2. Accumulate the true positives, true negatives, false positives, and false negatives over the sequence of frames.
3. Calculate precision and recall using the accumulated metrics.

Note that while this method can be scaled to larger datasets, it is still important to compare your results with official benchmarks, such as those provided by Waymo or 50, to ensure accuracy.

## Transcript

Now, on the last example, you have been manually comparing labels and detections for a single frame. This usually works quite well and also provides you with a good understanding of what's going on with your detector, but it's also as you might have noticed awfully slow and cumbersome to do. In this exercise, you will therefore be using the accumulated true positives, true negatives and false part, false negatives from an automatic matching between detections and ground truth labels so that you can arrive at a better and more well-founded estimate of precision and recall that is not based on a single frame but on the sequence of about 200 friends instead. When compared to official benchmarks, such as way more or 50 for example, this number is still very low but the basic method of collecting data from individual friends, accumulating them and then evaluating that at the end of the processing cycle, this can be easily scaled to larger datasets.

## Additional Content

## Exercise: Computing Precision & Recall
**Files to work in:**

- `basic_loop.py`
- `lesson-2-object-detection/exercises/starter/l2_exercises.py`

To get started, please add the code outlined above into the main loop of `basic_loop.py`, switch to sequence 1 with a frame setting of `[0,200]`  and execute the loop. When the accumulation is complete, open the function `compute_precision_recall` in `l2_exercises.py` and add the code necessary to compute precision and recall. Also, print the number of TP, FP and FN as well as the results for precision and recall to the terminal. Your result should look like the following: 

```text
TP = 552, FP = 50, FN = 188
precision = 0.9169435215946844, recall = 0.745945945945946, conf_thres = 0.5
```

Based on these results, we can assess the detector performance : While a total of 552 vehicles have been detected successfully, 50 phantom detections have occurred and 188 detections have been missed. While this might sound like a lot, we do not have information on the location of these errors: Did they occur within the path of driving? How long did phantom objects pop up? For how many frames did actual vehicles disappear? In practice, the engineering team would need to investigate each case to analyze the circumstances of these errors. Also, as problems such as missed detections and short-lived phantom objects can be removed or at least mitigated by the tracking stage (see lessons after mid-term), it makes sense to not look at frame-to-frame detections but rather at the object tracks over time.

Based on the precision result, we can say that the probability for a detection being an actual vehicle is at ~92%. The recall result provides us with the information that the probability for a vehicle being detected is at ~75%. Note that both values only hold for a confidence threshold of 0.5.
