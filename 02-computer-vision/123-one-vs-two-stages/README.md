# One vs Two Stages

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=i2I5uEyL3z4)

## Summary

**Object Detection Algorithms: One-Stage vs Two-Stage Detectors**
===========================================================

This summary compares two types of object detection algorithms: one-stage detectors and two-stage detectors. We'll explore their key differences in terms of design choice, speed, accuracy, and practical applications.

### Key Concepts
* **One-Stage Detector**: Directly computes bounding boxes and class probabilities from the input image.
* **Two-Stage Detector**: Uses a region proposal network (RPN) to generate proposals before computing bounding boxes and class probabilities.
* **Speed vs Accuracy Tradeoff**: One-stage detectors are faster but less accurate than two-stage detectors. Recent iterations of one-stage detectors have improved accuracy, but still lag behind two-stage detectors like Faster R-CNN.

### Practical Notes
When choosing an object detection algorithm for a project, consider the tradeoff between speed and accuracy. If you need high accuracy, use a two-stage detector like Faster R-CNN. However, if speed is crucial, consider using a one-stage detector like YOLO. Note that YOLO's original C++ implementation may be less user-friendly than Faster R-CNN's Python implementation in popular object detection libraries.

**Example Use Case**: When benchmarking the performance of an object detection model, use Faster R-CNN as it is generally more accurate and widely supported in Python libraries. However, if speed outweighs accuracy concerns, consider using YOLO.

## Transcript

Let's take some time to compare the two types of object detection algorithm we have learned about so far. One-stage detector directly compute bounding boxes and classes probability from the input image whereas two stages detector did an extra step by using the region proposal network. Well, speed is the main consequence of this design choice. One-stage detector being much faster than two stages. As far as accuracy goes, whereas YOLO was indeed much less accurate than Faster R-CNN recent iteration have yielded to higher performances.

Overall, Faster R-CNN still remain one of the most popular algorithm. My two cents is that the original code of YOLO was released in C++ making it less user friendly than Faster R-CNN, which exist in every object detection Python library. When benchmarking the performances for an object detection problem, I like to use Faster R-CNN. However, if outweighs the limitation, I would use YOLO instead.

## Additional Content

## One vs Two Stages
**Two stage** object detection models, such as FasterRCNN, need a region proposal step to propose ROIs. These regions of interest are then classified. **One stage** object detection algorithms, however, do not require a region proposal step and work directly off the input image. Whereas this initially meant that one stage object detectors were faster but less accurate, recent iterations of YOLO have shown better performances than FasterRCNN. 

However, FasterRCNN remains one of the most popular object detection algorithms, perhaps because of its wide availability in diverse libraries and the inertia of the industry to adopt more recent architectures.
### Further Research

Below are some other popular object detection algorithms:
- [SSD: Single Shot MultiBox Detector](https://arxiv.org/pdf/1512.02325.pdf)
- [CenterNet: Keypoint Triplets for Object Detection](https://arxiv.org/pdf/1904.08189.pdf)
- [Focal Loss for Dense Object Detection](https://arxiv.org/pdf/1708.02002.pdf)
