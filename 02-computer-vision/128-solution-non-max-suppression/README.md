# Solution: Non-Max Suppression

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=xc2g9sWXnBw)

## Summary

**Non-Max Suppression Function Implementation**
=============================================

This summary covers the implementation of the non-max suppression function using Python. The goal is to reduce redundant bounding boxes in object detection predictions.

### Key Concepts

* **Bounding Boxes**: These are rectangular regions that enclose predicted objects, defined by their coordinates (x, y, w, h).
* **Confidence Scores**: These are numerical values associated with each prediction, indicating the model's confidence in its accuracy.
* **IOU (Intersection over Union)**: This is a metric used to calculate the overlap between two bounding boxes. It is calculated as the ratio of the intersection area to the union area of the two boxes.
* **Soft NMS**: A variation of non-max suppression that instead of discarding predictions, decreases their confidence scores.

### Practical Notes

To implement non-max suppression:

1. Create a data structure to store both bounding box coordinates and confidence scores.
2. Sort the predictions based on their confidence scores using Python's `sorted` function.
3. Iterate through the sorted list twice:
	* In the first iteration, calculate the IOU for each pair of predictions and compare it with a threshold (0.5 in this example).
	* If the IOU is above 0.5, compare the confidence scores and discard the prediction with the lower score.
4. Save all non-discarded bounding boxes in a new list.

Note that implementing soft NMS involves modifying the code to decrease the confidence score instead of discarding the prediction.

## Transcript

In this exercise, you were asked to implement the non-max suppression function. The data provided consisted in nine predictions, with bounding boxes, and confidence scores. To keep things simple, all the predictions belong to the same class. To start, I created a new data structure that contain both the bounding boxes coordinates, and the confidence scores. I used the Python Sorted function to sort the predictions based on the scores.

I then look twice through this new data structure. I added an IF statement to avoid comparing the same predictions. For each pair of prediction, I calculated the IOU and compared with the required threshold of 0.5. If the IOU is above 0.5, I compared the scores and discarded the bounding boxes if the confidence score is lower. Finally, I saved all the non-discarded bounding boxes in a new list.

If we were to implement soft NMS, we would edit this line and decrease the confidence score instead of discarding the prediction.

## Additional Content

## Solution: Non-Max Suppression
```python
import json

from utils import calculate_iou, check_results


def nms(predictions):
    """
    non max suppression
    args:
    - predictions [dict]: predictions dict 
    returns:
    - filtered [list]: filtered bboxes and scores
    """

    data = []
    for bb, sc in zip(predictions['boxes'], predictions['scores']):
        data.append([bb, sc])

    data_sorted = sorted(data, key = lambda k: k[1])[::-1]
    filtered = []
    for i, bi in enumerate(data_sorted):
        discard = False
        for j, bj in enumerate(data_sorted):
            if i == j:
                continue
            iou = calculate_iou(bi[0], bj[0])
            if iou > 0.5:
                if bj[1] > bi[1]:
                    discard = True
        if not discard:
            filtered.append(bi)
    return filtered


if __name__ == '__main__':
    with open('../data/predictions_nms.json', 'r') as f:
        predictions = json.load(f)
    
    filtered = nms(predictions)
    check_results(filtered)
```
