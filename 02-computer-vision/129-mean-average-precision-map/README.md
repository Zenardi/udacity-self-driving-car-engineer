# Mean Average Precision (mAP)

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=IaY1g88merY)

## Summary

**Object Detection Metric: Mean Average Precision**
=====================================================

This project introduces a new metric designed for object detection problems, called mean average precision (MAP). The MAP is a measure of an algorithm's ability to detect objects accurately.

### Key Concepts
* **Precision**: the ratio of true positives to total predictions. A prediction with an IOU over 0.5 with a ground truth bounding box is considered a true positive.
* **Recall**: the ratio of true positives to actual number of objects in the image.
* **Average Precision (AP)**: calculated by taking the area under the precision-recall curve, smoothed by taking the maximum precision for each recall level.
* **Mean Average Precision (MAP)**: the mean of the average precision of each image in a dataset.

### Practical Notes
To calculate the MAP:

1. Order predictions by decreasing confidence scores.
2. For each prediction, determine if it's a true positive and calculate precision and recall.
3. Repeat step 2 for all predicted bounding boxes.
4. Build a precision-recall plot using the calculated values.
5. Smooth the curve by taking the maximum precision for each recall level.
6. Calculate the area under the smooth curve to get the average precision.
7. Take the mean of the average precision of each image in the dataset to get the MAP.

Note: The AP50 and AP75 metrics are variants of the AP metric, where a different IOU threshold is used to determine true positives (0.5 for AP50 and 0.75 for AP75).

## Transcript

Previously, we learned how to calculate precision and recall for object detection. We looked at this image where all the cars detected but one of the car detection is a traffic sign. The precision of our algorithm for this image is 4 over 5, and the recall is one because all the cars are detected. We also described as true positive a prediction with an IOU over 0.5 with a ground truth bounding box. We are now going to use this concept to build an object detection metric.

In this video, we're going to define a new metric designed for object detection problem, the mean average precision. Let's consider an image containing four cars. Our car detection algorithm predicted five bounding boxes. First, we are going to order the predictions by decreasing confidence scores. Then we are going to consider each prediction, determine if it's a true positive, and calculate precision and recall.

In this table, I've listed all five prediction in decreasing confidence score order. Let's consider the first prediction. We are assuming that this prediction is a true positive. Therefore, with this prediction only, we have a precision of one and a recall of 0.25 because we have detected one car out of four. Let's now consider the first two predictions.

The second prediction is also a true positive, so the precision is still one. However, we have now detected another car and the recall is now 0.5. Let's include the third prediction now. The third prediction is a false positive. Therefore, the precision is now two out of three and the recall does not change.

We repeat this operation and add one prediction at a time. We stop once we have calculated the precision and recall for the set containing all the predicted bounding boxes. Now that we have built this table, we can calculate the average precision for this image. To do so, we start by building a precision-recall plot using the value we calculated previously. We smooth this precision-recall curve by taking the maximum precision for each recall level.

The average precision for this image is calculated by taking the area under the smooth curves. The mean average precision is the mean of the average precision of each image in the data set. In research papers you will see terms such as AP50 or AP75. Well, it means that we are considering different IOU threshold to determine if a prediction is a true positive or not. AP50 means that we use a 0.5.

threshold, whereas AP75 means that we use is 0.75 threshold. Well, with this video, we now have all the components to build object detection model. In the next video, we're going to learn how to use the TensorFlow object detection API.

## Additional Content

## Mean Average Precision (mAP)
**Mean Average Precision (mAP) ** is the to-go metric of the object detection task. You will find multiple variations of the mAP metric in the literature. The [COCO challenge webpage](https://cocodataset.org/#detection-eval) provides a good description of the different metrics. The [pycocotools](https://github.com/cocodataset/cocoapi/tree/master/PythonAPI/pycocotools) Python library provides an easy way to evaluate your object detection results.
