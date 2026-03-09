# Solution: Choosing Metrics

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=pmqspFt00D8)

## Summary

**Intersection over Union (IoU) and Precision/Recall Calculation**
===========================================================

This project involves implementing functions for calculating the intersection over union (IoU) between two bounding boxes and evaluating the precision and recall of predicted bounding boxes against ground truth labels.

### Key Concepts

* **Intersection Over Union (IoU)**: a measure of how much two bounding boxes overlap, calculated as the area of intersection divided by the area of union.
* **Bounding Box Coordinates**: four coordinates defining the upper left corner and lower right corner of a rectangle.
* **Max Function**: used to calculate the maximum value between two numbers, ensuring that non-intersecting bounding boxes are handled correctly.
* **Area Calculation**: the area of a bounding box is calculated as the product of its width and height.
* **Precision and Recall Formula**:
	+ Precision = TP / (TP + FP)
	+ Recall = TP / (TP + FN)

### Practical Notes

To implement the IoU calculation function:

1. Calculate the coordinates of the intersection between two bounding boxes using the max function to handle non-intersecting boxes.
2. Calculate the area of both input bounding boxes and subtract the area of the intersection from their union.

To implement the precision and recall calculation function:

1. Use `numpy.where` to find intersecting bounding boxes with an IoU over 0.5.
2. Loop through the values and compare ground truth classes with predicted classes, counting true positives (TP) and false positives (FP).
3. Calculate false negatives (FN) by subtracting the number of unmatched ground truth boxes from the total number of ground truth boxes.
4. Use the precision and recall formula to calculate the final metrics.

Note: This project assumes familiarity with numpy and basic Python programming concepts.

## Transcript

In this exercise, you were asked to implement a function that calculates the intersection of a union between two bounding boxes. Both bounding boxes were defined by four coordinates. Two, for the upper left corner and two for the lower right corner of the bounding box. First, we need to calculate the coordinates of the bounding box created by the intersection of these two bounding boxes. We need to keep in mind that these bounding boxes may not intersect, and this is why I am using the max function here.

Then to calculate the union, we need to first calculate the area of both input bounding boxes. Finally, when calculating the union, we should not forget to subtract the area of the intersection. This function is very useful and we will be reusing it in further exercises. In the second part of this exercise, you were asked to implement a function that calculates precision and recall for a list of predicted and ground truth bounding boxes. We can use the numpy.where function to find where bounding boxes are intersecting with an iou over 0.5.

We can then loop over the values and compare the ground truth classes with the predicted classes. If they are equal, we have a true positive. But if they are not equal, we have a false-positive. To calculate the false negatives, we first get the number of ground truth bounding boxes that have not been matched with any predicted bounding boxes. The false negative are calculated by subtracting this number to the total number of ground truth bounding boxes.

Finally, we use the formula learned in the lesson to calculate precision and recall.

## Additional Content

## Solution: Choosing Metrics
> Correction in the video: The formula for calculating `recall` should be:
`recall  = tps / (tps + fns)`
`iou.py`

```python
import numpy as np

from utils import get_data, check_results


def calculate_iou(gt_bbox, pred_bbox):
    """
    calculate iou 
    args:
    - gt_bbox [array]: 1x4 single gt bbox
    - pred_bbox [array]: 1x4 single pred bbox
    returns:
    - iou [float]: iou between 2 bboxes
    """
    xmin = np.max([gt_bbox[0], pred_bbox[0]])
    ymin = np.max([gt_bbox[1], pred_bbox[1]])
    xmax = np.min([gt_bbox[2], pred_bbox[2]])
    ymax = np.min([gt_bbox[3], pred_bbox[3]])
    
    intersection = max(0, xmax - xmin + 1) * max(0, ymax - ymin + 1)
    gt_area = (gt_bbox[2] - gt_bbox[0]) * (gt_bbox[3] - gt_bbox[1])
    pred_area = (pred_bbox[2] - pred_bbox[0]) * (pred_bbox[3] - pred_bbox[1])
    
    union = gt_area + pred_area - intersection
    return intersection / union


def calculate_ious(gt_bboxes, pred_bboxes):
    """
    calculate ious between 2 sets of bboxes 
    args:
    - gt_bboxes [array]: Nx4 ground truth array
    - pred_bboxes [array]: Mx4 pred array
    returns:
    - iou [array]: NxM array of ious
    """
    ious = np.zeros((gt_bboxes.shape[0], pred_bboxes.shape[0]))
    for i, gt_bbox in enumerate(gt_bboxes):
        for j, pred_bbox in enumerate(pred_bboxes):
            ious[i,j] = calculate_iou(gt_bbox, pred_bbox)
    return ious


if __name__ == "__main__": 
    ground_truth, predictions = get_data()
    # get bboxes array
    filename = 'segment-1231623110026745648_480_000_500_000_with_camera_labels_38.png'
    gt_bboxes = [g['boxes'] for g in ground_truth if g['filename'] == filename][0]
    gt_bboxes = np.array(gt_bboxes)
    pred_bboxes = [p['boxes'] for p in predictions if p['filename'] == filename][0]
    pred_boxes = np.array(pred_bboxes)
    
    ious = calculate_ious(gt_bboxes, pred_boxes)
    check_results(ious)
```
`precision_recall.py`

```python
import numpy as np

from iou import calculate_ious
from utils import get_data


def precision_recall(ious, gt_classes, pred_classes):
    """
    calculate precision and recall
    args:
    - ious [array]: NxM array of ious
    - gt_classes [array]: 1xN array of ground truth classes
    - pred_classes [array]: 1xM array of pred classes
    returns:
    - precision [float]
    - recall [float]
    """
    xs, ys = np.where(ious>0.5)

    # calculate true positive and true negative
    tps = 0
    fps = 0
    for x, y in zip(xs, ys):
        if gt_classes[x] == pred_classes[y]:
            tps += 1
        else:
            fps += 1

    matched_gt = len(np.unique(xs))
    fns = len(gt_classes) - matched_gt

    precision = tps / (tps+fps)
    recall = tps / (tps + fns)
    return precision, recall


if __name__ == "__main__": 
    ground_truth, predictions = get_data()
    
    # get bboxes array
    filename = 'segment-1231623110026745648_480_000_500_000_with_camera_labels_38.png'
    gt_bboxes = [g['boxes'] for g in ground_truth if g['filename'] == filename][0]
    gt_bboxes = np.array(gt_bboxes)
    gt_classes = [g['classes'] for g in ground_truth if g['filename'] == filename][0]
    

    pred_bboxes = [p['boxes'] for p in predictions if p['filename'] == filename][0]
    pred_boxes = np.array(pred_bboxes)
    pred_classes = [p['classes'] for p in predictions if p['filename'] == filename][0]
    
    ious = calculate_ious(gt_bboxes, pred_boxes)
    precision, recall = precision_recall(ious, gt_classes, pred_classes)
    print(f'Precision: {precision}')
    print(f'Recall: {recall}')
```
