# When to Use Deep Learning for Computer Vision

> Part of: **Introduction to Deep Learning for Computer Vision**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=DU3mveQZs8E)

## Summary

**Computer Vision for Self-Driving Cars**
=====================================

This project explores the intersection of computer vision and self-driving cars. We'll examine how analyzing digital images is crucial for creating intelligent vehicles that can navigate complex environments.

### Key Concepts
* **Deep Learning**: a subset of machine learning that has shown exceptional performance in image analysis, outperforming traditional computer vision methods.
* **Computer Vision Methods**: pre-Deep Learning techniques used to analyze images, which may be more suitable for certain tasks or applications due to their lower computational cost.
* **Object Detection**: a task where Deep Learning algorithms excel, but may not be the default choice in all scenarios.

### Practical Notes
When working with self-driving car systems, consider the trade-offs between using Deep Learning and traditional computer vision methods. While Deep Learning approaches tend to outperform classic methods, they come at a computational cost that may be difficult to deploy on hardware-limited systems. Classic computer vision methods can still be useful in many cases, especially when simplicity and efficiency are prioritized.

**Example Use Cases**

* Using traditional computer vision methods for tasks where speed and efficiency are crucial
* Implementing Deep Learning algorithms for object detection and image analysis

Note: This summary is based on the provided transcript. If you'd like me to add or modify anything, please let me know!

## Transcript

Previously, we discovered how computer vision is at the core of the self-driving car technology. Analyzing digital images is critical to create an intelligent car that can navigate complex environments. But to do so, we need performance algorithm to get the best understanding of an image possible. Well, it appears that Deep Learning is doing very well at image analysis and tend to have much better performances than traditional computer vision method. Moreover, Deep Learning algorithms are able to extract signals from complex environments such as busy city centers.

However, the field of computer vision existed way before the Deep Learning revolution. Whereas Deep Learning excels at certain tasks such as object detection, it should not necessarily be the default algorithm when it comes to analyzing images. For example, Deep Learning comes at a computational cost because of the complexity of the algorithm. Because of said complexity, they are harder to deploy in self-driving cars system where hardware is often a limitation. Overall, Deep Learning approaches tend to outperform traditional computer vision method and they are definitely at the core of many self-driving car systems.

However, classic computer vision methods should not be overlooked and they can be particularly useful in many cases.

## Additional Content

## When to Use Deep Learning for Computer Vision
Deep Learning algorithms are now the **state of the art (SOTA) ** in most computer vision problems, such as image classification or object detection. Therefore, they are now in every SDC system. However, using deep learning adds additional constraints to the system because they require more computational power.
