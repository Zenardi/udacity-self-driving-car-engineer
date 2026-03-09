# Solution: Geometric Transformation

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=rcd7lbkZQYY)

## Summary

**Geometric Transformations for Images and Bounding Boxes**
===========================================================

This project involves implementing multiple geometric transformations, including horizontal flipping and resizing, as well as random cropping. These transformations affect both the image and its corresponding bounding boxes.

### Key Concepts

* **Horizontal Flipping**: A transformation that flips an image horizontally by negating the x-coordinates of the pixels.
	+ The y-coordinates of the bounding boxes are also affected, but only in terms of their position on the flipped image.
* **Resizing**: A transformation that changes the size of an image while maintaining its aspect ratio.
	+ To resize bounding boxes, calculate the ratio of height and width between the original and resized images using NumPy indexing rules.
* **Random Cropping**: A transformation that randomly selects a region from an image to crop.
	+ Calculate the coordinates of the crop by selecting random upper-left corner coordinates based on the image dimensions and crop size.
	+ Use the IoU function to calculate the intersection area between the original bounding box and the crop, ensuring the new bounding box area is above a certain threshold.

### Practical Notes

* To implement horizontal flipping using Pillow, use the `Image` class's built-in methods for flipping images horizontally.
* For resizing, leverage the `resize()` method of the `Image` class to resize both the image and its corresponding bounding boxes.
* When implementing random cropping, ensure that the new bounding box area is above a certain threshold by calculating the intersection area between the original bounding box and the crop using the IoU function.

## Transcript

In this exercise, you are asked to implement from scratch multiple geometric transformation, horizontal flipping, and resizing. You also had the opportunity to implement random cropping as an additional challenge. This transformation should affect both the image and the bounding boxes. We provided this function to calculate the IoU between two bounding boxes. Thanks to Pillow, the horizontal flipping of an image is relatively straightforward to implement.

However, you also need to flip the bounding boxes. The horizontal flip only affects the y-coordinates of the bounding boxes as shown here. For the resizing transformation, we can also leverage a method of the Pillow image class. To resize the bounding boxes, we first need to calculate the ratio of both height and width between the original image and the new resized one. Using this ratio and the NumPy indexing rules, we can resize the bounding boxes.

The random cropping transformation is slightly more challenging to implement. First, we need to create the coordinates of the crop by using the dimension of the image and the crop size. We randomly select the coordinates of the upper band corner and create the crop using them. To calculate the coordinates of the new bounding boxes, we use the calculate IoU function to get the intersection area of the original bounding box and the crop. We also want to be sure that the new bounding boxes area is over a certain threshold.

Manipulating images and bounding boxes will be extremely useful when working on object detection problems.

## Additional Content

## Solution: Geometric Transformation
```python
import copy
import json
import random

import numpy as np 
from PIL import Image

from utils import check_results, display_results


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
    return intersection / union, [xmin, ymin, xmax, ymax]


def hflip(img, bboxes):
    """
    horizontal flip of an image and annotations
    args:
    - img [PIL.Image]: original image
    - bboxes [list[list]]: list of bounding boxes
    return:
    - flipped_img [PIL.Image]: horizontally flipped image
    - flipped_bboxes [list[list]]: horizontally flipped bboxes
    """
    # flip image
    flipped_img = img.transpose(Image.FLIP_LEFT_RIGHT)
    w, h = img.size
    
    # flip bboxes
    bboxes = np.array(bboxes)
    flipped_bboxes = copy.copy(bboxes)
    flipped_bboxes[:, 1] = w - bboxes[:, 3]
    flipped_bboxes[:, 3] = w - bboxes[:, 1]
    return flipped_img, flipped_bboxes


def resize(img, boxes, size):
    """
    resized image and annotations
    args:
    - img [PIL.Image]: original image
    - boxes [list[list]]: list of bounding boxes
    - size [array]: 1x2 array [width, height]
    returns:
    - resized_img [PIL.Image]: resized image
    - resized_boxes [list[list]]: resized bboxes
    """
    # resize image
    resized_image = img.resize(size)
    w, h = img.size
    ratiow = size[0] / w
    ratioh = size[1] / h
    
    # resize bboxes
    boxes = np.array(boxes)
    resized_boxes = copy.copy(boxes)
    resized_boxes[:, [0, 2]] = resized_boxes[:, [0, 2]] * ratioh
    resized_boxes[:, [1, 3]] = resized_boxes[:, [1, 3]] * ratiow
    return resized_image, resized_boxes


def random_crop(img, boxes, classes, crop_size, min_area=100):
    """
    random cropping of an image and annotations
    args:
    - img [PIL.Image]: original image
    - boxes [list[list]]: list of bounding boxes
    - classes [list]: list of classes
    - crop_size [array]: 1x2 array [width, height]
    - min_area [int]: min area of a bbox to be kept in the crop
    returns:
    - cropped_img [PIL.Image]: cropped image
    - cropped_boxes [list[list]]: cropped bboxes
    - cropped_classes [list]: cropped classes
    """
    # crop coordinates
    w, h = img.size
    x1 = np.random.randint(0, w - crop_size[0])
    y1 = np.random.randint(0, h - crop_size[1])
    x2 = x1 + crop_size[0]
    y2 = y1 + crop_size[1]

    # crop the image
    cropped_image = img.crop((x1, y1, x2 ,y2))

    # calculate iou between boxes and crop
    cropped_boxes = []
    cropped_classes = []
    for bb, cl in zip(boxes, classes):
        iou, inter_coord = calculate_iou(bb, [y1, x1, y2, x2])
        # some of the bbox overlap with the crop
        if iou > 0:
            # we need to check the size of the new coord
            area = (inter_coord[3] - inter_coord[1]) * (inter_coord[2] - inter_coord[0])
            if area > min_area:
                xmin = inter_coord[1] - x1
                ymin = inter_coord[0] - y1
                xmax = inter_coord[3] - x1
                ymax = inter_coord[2] - y1
                cropped_box = [ymin, xmin, ymax, xmax]
                cropped_boxes.append(cropped_box)
                cropped_classes.append(cl)
    return cropped_image, cropped_boxes, cropped_classes


if __name__ == '__main__':
    # fix seed to check results
    np.random.seed(48)

    # open annotations 
    with open('data/ground_truth.json') as f:
        ground_truth = json.load(f)

    # filter annotations and open image
    filename = 'segment-12208410199966712301_4480_000_4500_000_with_camera_labels_79.png'
    gt_boxes = [g['boxes'] for g in ground_truth if g['filename'] == filename][0]
    gt_classes = [g['classes'] for g in ground_truth if g['filename'] == filename][0]
    img = Image.open(f'data/images/{filename}')

    # check horizontal flip
    flipped_img, flipped_bboxes = hflip(img, gt_boxes)
    display_results(img, gt_boxes, flipped_img, flipped_bboxes)
    check_results(flipped_img, flipped_bboxes, aug_type='hflip')

    # check resize
    resized_image, resized_boxes = resize(img, gt_boxes, size=[640, 640])
    display_results(img, gt_boxes, resized_image, resized_boxes)
    check_results(resized_image, resized_boxes, aug_type='resize')

    # check random crop
    cropped_image, cropped_boxes, cropped_classes = random_crop(img, gt_boxes, gt_classes, [512, 512], min_area=100)
    display_results(img, gt_boxes, cropped_image, cropped_boxes)
    check_results(cropped_image, cropped_boxes, aug_type='random_crop', classes=cropped_classes)
```
