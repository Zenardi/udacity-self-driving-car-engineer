# Solution: Mean Average Precision (mAP)

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Ut6PQR_-f3E)

## Summary

**Mean Average Precision (MAP) Calculation**
=====================================================

This README file provides a summary of the key concepts and practical steps involved in calculating the mean average precision (MAP) given a set of prediction and ground truth values.

### Key Concepts
* **Intersection over Union (IoU)**: A measure of overlap between two bounding boxes, calculated as the ratio of their intersection area to their union area.
* **Precision-Recall Curve**: A plot that shows the trade-off between precision and recall for a given set of predictions.
* **Smooth Precision-Recall Curve**: A smoothed version of the precision-recall curve, created by interpolating between points where the precision changes.
* **Mean Average Precision (MAP)**: The area under the smooth precision-recall curve.

### Practical Notes
To calculate MAP, you need to:

1. Create a data structure that contains bounding boxes, classes, and scores.
2. Sort this list jointly using the confidence score values.
3. Calculate the IoU between each prediction and ground truth bounding box.
4. Identify true positives (IoU > 0.5 and class = 1) and calculate precision and recall for each element in the list.
5. Create a smooth version of the precision-recall curve by interpolating between points where the precision changes.
6. Plot both the original and smoothed precision-recall curves using Matplotlib.
7. Calculate MAP as the area under the smoothed precision-recall curve.

Note: This process involves several steps, including data preparation, IoU calculation, precision-recall curve creation, and smoothing. It's recommended to review this calculation carefully to understand how MAP is calculated.

## Transcript

In this exercise, you were asked to calculate the mean average precision given a set of prediction and a set of ground truths values. First, I created the new data structure that contains bounding boxes, classes, and scores. I sorted this list jointly using the confidence score values. For each element of this list, I calculate the IoU with each ground truths bounding box. If the IoU is above 0.5 and the class is equal to 1, we have a true positive.

Next, I calculate the value of precision and recall and save them to a list. Now that we have a list that contain the pair values of precision and recall, we can create the smooth version of the precision-recall curve. First, I look for the value where the precision changes. I then calculate the maximum of this curve between two of those values and save this maximum to a list. Using this list, I create the smooth curve.

I plot both curves using Matplotlib. Finally, I used the smooth curve to calculate the mean average precision as the area under the curve. This is how your precision-recall curves should look like. In blue, we have the original precision-recall curve, and in orange, you have the smooths' version. Mean average precision is not the most straightforward metric to understand and I encourage you to go over this calculation again.

## Additional Content

## Solution: Mean Average Precision (mAP)
```python
import copy
import json
from collections import Counter

import matplotlib.pyplot as plt
import numpy as np

from utils import calculate_iou, check_results


if __name__ == '__main__':
    # load data 
    with open('../data/predictions.json', 'r') as f:
        preds = json.load(f)

    with open('../data/ground_truths.json', 'r') as f:
        gts = json.load(f)
    
    # sort predictions by scores
    boxes = preds[0]['boxes']
    classes = preds[0]['classes']
    scores = preds[0]['scores']

    predictions = [(bb, cl, sc) for bb, cl,sc in zip(boxes, classes, scores)]
    predictions = sorted(predictions, key=lambda k:k[-1])[::-1] 

    # create precision - recall plot
    total = len(gts[0]['boxes'])
    tp = 0
    curve = []
    for idx, pred in enumerate(predictions):
        for bb in gts[0]['boxes']:
            iou = calculate_iou(bb, pred[0])
            # print(iou)
            if iou > 0.5:
                if pred[1] == 1:
                    tp += 1
        prec = tp / (idx+1)
        rec = tp / total
        curve.append([prec, rec])

    # smooth PR curve
    curve = np.array(curve)
    ct = Counter(curve[:, 1])
    boundaries = sorted([k for k,v in ct.items() if v > 1])
    # get max precision values
    maxes = []
    for i in range(len(boundaries)):
        if i != len(boundaries) - 1:
            loc = [p[0] for p in curve if boundaries[i+1] >= p[1] > boundaries[i]]
            maxes.append(np.max(loc))
        else:
            loc = [p[0] for p in curve if p[1] > boundaries[i]]
            maxes.append(np.max(loc))
    smoothed = copy.copy(curve)
    replace = -1
    for i in range(smoothed.shape[0]-1):
        if replace != -1:
            smoothed[i, 0] = maxes[replace]
        if smoothed[i, 1] == smoothed[i+1, 1]:
            replace += 1 
    
    plt.plot(curve[:, 1], curve[:, 0], linewidth=4)
    plt.plot(smoothed[:, 1], smoothed[:, 0], linewidth=4)
    plt.xlabel('recall', fontsize=18)
    plt.ylabel('precision', fontsize=18)
    plt.show()

    # calculate mAP
    cmin = 0
    mAP = 0
    for i in range(smoothed.shape[0] - 1):
        if smoothed[i, 1] == smoothed[i+1, 1]:
            mAP += (smoothed[i, 1] - cmin) * smoothed[i, 0]
            cmin = smoothed[i, 1]
    mAP += (smoothed[-1, 1] - cmin) * smoothed[-1, 0]
    check_results(mAP)
```
