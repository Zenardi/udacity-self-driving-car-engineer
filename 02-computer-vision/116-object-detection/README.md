# Object Detection

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=feUy03tjWDM)

## Summary

**Object Detection: A Machine Learning Problem**
=====================================================

This lesson covers the basics of object detection, a type of machine learning problem that involves detecting and classifying objects in images using ConvNets. We will explore different algorithms for object detection, including two-stage detectors like RCNN and one-stage detectors like YOLO.

**Key Concepts**
---------------

* **ConvNets**: A type of neural network architecture used for image classification and object detection.
* **Object Detection Algorithms**: Methods for detecting objects in images, including:
	+ Two-stage detectors (e.g. RCNN)
	+ One-stage detectors (e.g. YOLO)
* **RCNN Family of Algorithm**: A family of algorithms that use a two-stage approach to detect objects in images.
* **YOLO Algorithm**: A one-stage detector that detects objects directly from the input image without the need for a separate stage.
* **Mean Average Precision (MAP)**: A metric used to evaluate the performance of object detection algorithms.

**Practical Notes**
-------------------

* To complete the final project, you will need to familiarize yourself with the TensorFlow Object Detection API and learn how to use it to detect objects in images.
* You will also need to implement one of two post-processing methods (not specified which) as part of an exercise.
* The lesson covers tips for training neural networks, including:
	+ Monitoring data loading time
	+ Experimenting with different learning rates using the TensorFlow Object Detection API

## Transcript

Welcome to this lesson on object detection. In this lesson, we will tackle a new type of machine learning problem: object detection. We will learn how to leverage the power of ConvNets to detect and classify objects in images. We will learn about different algorithm for object detection, starting with two stages object detector. We will focus on the RCNN family of algorithm.

We will also briefly review one stage detector as well, where we will focus on the YOLO algorithm. You will get to experiment with these algorithm in the final project when using the TensorFlow object detection API. First, we'll get started with an overview of different object detection algorithm. Despite an ever-growing number of approaches to solve this problem, a few architecture remain very popular. We will take a step back in time to learn how they were developed.

Next, we are going to learn about two post-processing method to get cleaner results from object detection algorithm. You will have to implement one of them as part of an exercise. A new task also means that we need a new metric, and we will study together an object detection metric: the mean average precision. To complete the final project, you will need to get familiar with the TensorFlow object detection API and we will spend some time learning how to use it. Finally, we are going to learn some tricks to train neural networks.

For example, data loading can be a bottleneck when training deep learning algorithm and we will learn how to monitor it. We will also see how to experiment with different learning rates in the TensorFlow object detection API. Finally, I created a step-by-step guide to follow when training new neural network architectures. We have a lot of ground to cover in this lesson, so let's get started now.

## Additional Content

## Object Detection
In this lesson, we will tackle:
- An overview of object detection algorithms
- A post processing method for detections
- A new metric: mean average precision (mAP)
- The TensorFlow object detection API
- Tips and tricks to train and monitor neural networks
