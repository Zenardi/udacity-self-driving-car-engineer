# One Stage Object Detection

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=VP8OIsJXsLI)

## Summary

**YOLO: A One-Stage Object Detection Algorithm**
=====================================================

This project focuses on the **You Only Look Once (YOLO)** algorithm, a popular one-stage object detection method that eliminates the need for region proposal steps found in two-stage detectors like Faster RCNN.

### Key Concepts
* **One-stage detector**: An object detection algorithm that does not require a region proposal step.
* **Grid cells**: The input image is divided into a grid, where each cell predicts B bounding boxes (B is a hyperparameter).
* **Bounding boxes**: Each box consists of five predictions: four spatial coordinates and one objectness score.
* **Class probability**: A calculation for each grid cell to determine the likelihood of an object in that cell.
* **Multi-task learning**: An approach used by YOLO for end-to-end training.

### Practical Notes
YOLO achieves real-time inference (over 30 FPS) but may underperform with smaller objects, especially when they appear in groups. However, recent iterations like YOLO v2 and v3 have shown significant improvements, often matching or surpassing the performance of Faster RCNN.

## Transcript

Despite improving over its predecessor, Faster RCNN is still a fairly slow algorithm that does not run in real time. Because of the need to compute region proposal first, Faster RCNN is considered as a two-stage object detection algorithm. However, other object detection algorithm do not require this region proposal step. We call them one stage detector and this video, we are going to focus on the most popular of them; YOLO. YOLO stands for You Only Look Once because the algorithm does not need these region proposal step.

How does YOLO work? While the network starts by dividing the input image in a grid. Each grid cells predict B bounding boxes, where B is an hyperparameter. Similarly to anchor boxes in Faster RCNN, these bounding boxes consist in five prediction, the four spatial coordinates, and one abjectness score. Moreover, we also calculate for each grid cell a class probability.

By doing that, we make the assumption that a single cell contain only one object. YOLO also uses a multi-task class to enable end-to-end training. YOLO is much different than Faster RCNN. But how does it translate in terms of performances? While YOLO achieves real-time inference by running over 30 FPS.

However, it does not detect object as well as Faster RCNN, and speed does come at a cost. In particular, YOLO is well-known to underperform with smaller objects that appears in group. For example, in this image, YOLO would have a much harder time to detect all the birds than other object detection algorithm. However, recent iteration of YOLO displayed significant improvements and YOLO v2 and v3 achieved performances on par or better than Faster RCNN. I added a link to the paper in the description below.

## Additional Content

## One Stage Object Detection
*The input image in the video is divided in a 7x7 grid and not a 5 by 5.*
**You Only Look Once (YOLO)** takes a very different approach than FasterRCNN. Instead of relying on a region proposal step, the author of this [2016 paper](https://arxiv.org/pdf/1506.02640.pdf) directly split the input image into a grid. For each element of the grid, the network predicts `B` bounding boxes and objectness scores. 

By getting rid of the region proposal step, YOLO provides much faster inference time than FasterRCNN.

 The authors released two more versions of YOLO. The latest one, YOLOv3 is described [here](https://pjreddie.com/media/files/papers/YOLOv3.pdf). Moreover, other researchers published [YOLOv4](https://arxiv.org/pdf/2004.10934.pdf) and [YOLOv5](https://github.com/ultralytics/yolov5). YOLO remains one of the most popular object detection architectures.
