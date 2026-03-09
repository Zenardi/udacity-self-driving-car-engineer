# Semantic Segmentation Revisited

> Part of: **Inference Performance**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=xFcI26kLtiY)

## Summary

**Semantic Segmentation Performance Optimization**
=====================================================

This lesson focuses on addressing the computational intensity of semantic segmentation, a technique used in computer vision. The current implementation of semantic segmentation is not fast enough for real-time applications.

### Key Concepts
* **Computationally intensive**: Semantic segmentation requires significant processing power to perform tasks such as image classification and object detection.
* **Frame rate**: A measure of how many frames per second (FPS) a system can process, with higher FPS indicating faster performance.
* **YOLO (You Only Look Once)**: A bounding box algorithm that runs at 4,290 FPS, compared to the 4-7 FPS of semantic segmentation.
* **Fusion quantization**: An optimization technique used to reduce the computational requirements of neural networks by reducing precision and increasing efficiency.
* **Graph to binary optimizations**: Another optimization technique used to improve performance by converting complex graph-based models into more efficient binary representations.

### Practical Notes
To increase the performance of the semantic segmentation system, we can apply various optimizations such as fusion quantization and graph to binary conversions. These techniques have been shown to improve performance by 3-5 times, making them essential for real-time applications.

## Transcript

<v English>You may have noticed semantic segmentation is computationally intensive.</v> <v English>It's not uncommon for this pipeline to put out four to seven frame per second,</v> <v English>while bounding boxes such as YOLO run at 4,290 FPS.</v> <v English>Semantic segmentation has advantages over bounding boxes obviously.</v> <v English>But in its current state,</v> <v English>the segmentation system is simply not fast enough.</v> <v English>However, with various optimizations,</v> <v English>we can increase the performance of this system by three to five times.</v> <v English>We will cover fusion quantization and graph to binary optimizations next.</v>
