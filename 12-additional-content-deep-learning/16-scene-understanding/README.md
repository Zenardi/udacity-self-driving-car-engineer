# Scene Understanding

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=aMQREc-mP50)

## Summary

**Scene Understanding with Multiple Decoders**
=====================================================

This project explores a technique for scene understanding by training multiple decoders, each responsible for a specific task. This approach enables the creation of a single network that can predict both the class of a pixel and its depth measurement.

**Key Concepts**
---------------

* **Multi-task learning**: Training multiple models simultaneously to perform different tasks.
* **Decoders**: Separate networks trained on individual tasks, such as segmentation or depth measurement.
* **Semantic segmentation**: Predicting the class of each pixel in an image.
* **Depth measurement**: Estimating the distance between objects and the camera.

**Practical Notes**
-----------------

To implement this approach, you can use a single neural network architecture with multiple output branches, each responsible for a specific task. For example, you might use a U-Net or ResNet architecture as the base model and add separate output layers for segmentation and depth measurement. This project focuses on semantic segmentation, but the concepts learned can be extended to other tasks like depth estimation.

Note: The code and implementation details are not provided in this transcript, so you will need to consult additional resources or the original Udacity lesson for specific instructions on how to implement this technique.

## Transcript

<v English>One approach to scene understanding is to train multiple decoders.</v> <v English>Each decoder trains on a separate task.</v> <v English>We might have one decoder for segmentation and another for depth measurement.</v> <v English>This way we can have a single network which not only</v> <v English>predicts the class of a pixel but additionally how far away it is.</v> <v English>You can imagine using this information to reconstruct a rich 3D scene,</v> <v English>kind of like how we human do.</v> <v English>This is in fact, the next step to visual perception.</v> <v English>For now though, we'll keep things relatively</v> <v English>simple focused just on semantic segmentation.</v>
