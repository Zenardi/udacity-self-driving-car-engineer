# Bounding Boxes

> Part of: **Scene Understanding**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=uPv4d0Xl8hc)

## Summary

**Object Detection with Bounding Boxes**
=====================================

This project focuses on object detection using a simpler method called **bounding boxes**. In contrast to segmentation, which aims to understand the entire scene, bounding boxes aim to identify and draw a box around specific objects in an image.

### Key Concepts

* **Bounding Box**: A rectangular box drawn around an object in an image to indicate its location.
* **Object Detection**: The task of identifying and locating specific objects within an image or video.
* **YOLO (You Only Look Once)**: An open-source state-of-the-art solution for object detection that performs well even at high frame rates.
* **SSD (Single Shot Detector)**: Another popular open-source model for object detection that is useful for detecting various objects in a scene.

### Practical Notes

When using bounding boxes for object detection, keep in mind their limitations. Bounding boxes are not suitable for complex shapes or scenes with multiple objects of varying sizes and orientations. They can only achieve partial understanding of the scene, making them less effective than segmentation methods for certain applications. However, they are still a useful tool for detecting specific objects such as cars, people, and traffic lights in real-time scenarios.

Example code using YOLO or SSD models is not provided in this lesson, but you can explore these open-source solutions to implement object detection with bounding boxes in your own projects.

## Transcript

<v English>Our first task is object detection.</v> <v English>And for that, we can use bounding boxes.</v> <v English>They are a simpler method of scene understanding compared to segmentation.</v> <v English>In neural network, just has to figure out</v> <v English>where an object is and draw a type box around it.</v> <v English>There are already great open source state of the art solutions,</v> <v English>such as YOLO and SSD models.</v> <v English>These models perform extremely well even at high frame per second.</v> <v English>They're useful for detecting different objects such as cars,</v> <v English>people, traffic lights, and other objects in the scene.</v> <v English>However, burning boxes have their limits.</v> <v English>Imagine drawing and bounding box around a curvy road,</v> <v English>the forest, or the sky,</v> <v English>this quickly becomes problematic or even</v> <v English>impossible to convey the true shape of an object.</v> <v English>At best, bounding boxes can only hope to achieve partial seen understanding.</v>
