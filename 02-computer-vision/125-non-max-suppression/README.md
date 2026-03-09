# Non-Max Suppression

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=REi3UTTUzQA)

## Summary

**README: Non-Max Suppression (NMS) and Soft-NMS**

This project explores the concepts of Non-Max Suppression (NMS) and its variant, Soft-NMS. NMS is a post-processing technique used in object detection algorithms to reduce redundant bounding box predictions.

### Key Concepts

* **Object Detection Algorithms**: Two-stage or one-stage algorithms that generate proposals for objects in an image.
* **Non-Max Suppression (NMS)**: A post-processing step that removes redundant bounding boxes by comparing their confidence scores and intersection over union (IOU) with other predictions.
	+ Sorting predictions based on confidence score
	+ Calculating IOU between predictions
	+ Removing predictions with lower confidence scores when IOU is above a threshold
* **Intersection Over Union (IOU)**: A measure of overlap between two bounding boxes, used to determine redundancy.
* **Soft-NMS**: An alternative to NMS that reduces the confidence score of overlapping detections instead of removing them.

### Practical Notes

To implement NMS or Soft-NMS in an object detection algorithm:

1. Sort predictions based on confidence scores
2. Calculate IOU between predictions
3. Apply NMS or Soft-NMS rules:
	+ For NMS: remove predictions with lower confidence scores when IOU is above a threshold
	+ For Soft-NMS: reduce confidence score of overlapping detections instead of removing them

Example use cases:

* Object detection in images, such as detecting cars or pedestrians
* Reducing redundant bounding box predictions to improve accuracy and efficiency

## Transcript

Whether we use two stages or one stage object detection algorithm, the underlying mechanism is the same. We take an image and generate a high number of proposal that we then classify. This approach has one specific downside. It tends to generate a lot of bounding boxes predictions. To remediate this, we use a post-processing step called non-max suppression, or NMS.

Let's look at the following example. We trained a Faster RCNN model to detect cars. Our model is outputting the following bounding boxes. The first one has a high confidence score of 0.9. The second one has a score of 0.7, and the third one a score of 0.06.

All three bounding boxes are detecting the same object. Well, wouldn't it be great to remove the last two because they have lower confidence? Well, this is exactly what the NMS algorithm does. Let's take a look at some pseudocode, and let's consider a single class object detection algorithm. The NMS algorithm works as follows.

We start by sorting the prediction based on the confidence score. We then calculate the IOU of each prediction with every other prediction. If the IOU is above a particular threshold, let's say 0.5. we then compare the confidence scores of both predictions. The bounding box with the highest confidence score is kept.

By doing that, we basically remove redundancy when the same object is detected multiple times. One of the downside of this approach is its tendency to remove varied prediction in high-density environments. In the following video, we are going to see an alternative to NMS. NMS can lead to disastrous behavior in high-density environment. Let's consider our card detection algorithm one more time, and let's take a look at these two particular detections.

The pink car is detected with a confidence score of 0.8 and the black truck with a confidence score of 0.9. Using NMS, the pink car detection will most likely be removed as it overlap significantly with the black car and has a lower confidence score. How could we improve over the NMS algorithm to avoid this? Well, it would be great to reduce the confidence score of the pink car instead of removing it. By doing that, we are considering the possibility that this detection might be another object.

This mechanism is called Soft-NMS, and it fits in one additional line of pseudocode. We're still sorting the bounding boxes using the convenience score, but instead of discarding the lower confidence bounding boxes, we keep them and decrease their confidence score. The authors of this algorithm offered to decrease the score proportionally to the overlap. Highly overlapping detection are probably the same object and therefore, the score should be decreased by a higher number. Soft-NMS is a very simple, yet powerful addition to the post-processing step of many object detection algorithm.

Now, that we have learned about different object detection algorithm and different post-processing method, we can focus on evaluating this algorithm.

## Additional Content

## Non-Max Suppression
**Non max suppression (NMS)** is a post-processing methods to remove redundant detections. Remember the Region Proposal Network in FasterRCNN? For each location of the sliding window, the network generates `k` anchor boxes. Because of that, object detection algorithms tend to output a large number of bounding boxes. By using the confidence score of each prediction, we can clean these predictions by removing high-overlapping / lower confidence predictions.
### Soft-NMS
In this [2017 paper](https://arxiv.org/pdf/1704.04503.pdf), the authors argued that NMS could actually hurt the performance of object detection algorithm by removing predictions of highly occluded objects. Instead, they proposed the **Soft NMS** algorithm. Soft NMS does not remove predictions that highly overlap higher confidence predictions, but instead reduces their confidence score. By doing so, Soft NMS improves the performance of object detection algorithms in dense environments.
