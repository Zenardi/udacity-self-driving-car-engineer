# Lesson Conclusion

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=8gLZEKnuwoY)

## Summary

**Object Detection with Deep Neural Networks**
=============================================

This lesson covers the basics of object detection using deep neural networks, including common architectures and post-processing techniques.

### Key Concepts

* **RCNN (Region-based Convolutional Neural Network) models**: A type of object detection architecture that uses a combination of convolutional and recurrent neural networks to detect objects.
* **YOLO (You Only Look Once) model**: Another popular object detection architecture that detects objects in one pass, without the need for multiple stages or iterations.
* **NMS (Non-Maximum Suppression)**: A post-processing technique used to clean up prediction results by removing duplicate detections and keeping only the most accurate ones.
* **Soft NMS**: An improved version of NMS that uses a soft suppression method instead of hard suppression, allowing for more flexible and accurate object detection.
* **Mean Average Precision (mAP)**: A metric used to evaluate the performance of an object detection model, taking into account both precision and recall.
* **TensorFlow Object Detection API**: A set of tools and libraries provided by TensorFlow for building and training object detection models.

### Practical Notes

When working with deep learning pipelines, it's essential to monitor data transfer between different stages. This can be achieved using various tools, such as:

```python
import tensorflow as tf

# Create a summary writer to log metrics during training
summary_writer = tf.summary.SummaryWriter(log_dir='logs')

# Monitor data transfer and logging during training
with summary_writer.as_default():
    # Log metrics at each step
    tf.summary.scalar('loss', loss_value, step=step)
```

Additionally, when training a neural network on a new dataset, follow these guidelines:

1. Preprocess your data carefully to ensure it's in the correct format.
2. Choose an appropriate object detection architecture and hyperparameters for your specific use case.
3. Monitor your model's performance using metrics like mAP and adjust hyperparameters as needed.
4. Use tools like NMS and Soft NMS to clean up prediction results and improve accuracy.

## Transcript

We're now done with this lesson on object detection with deep neural networks. In this lesson, we reviewed different object detection architectures, such as the RCNN models or the YOLO model. We learned about two post-processing techniques to clean prediction, NMS and Soft NMS. We also discovered a new metric, the mean average precision. We learned how to use the TensorFlow object detection API.

We became familiar with the different data transfer in deep learning pipelines. We learned how to leverage different tools to monitor them. Finally, I put together a few guidelines to follow when training a neural network on a new data-set. I cannot wait for you to use all this knowledge in the final project.

## Additional Content

## Lesson Conclusion
In this lesson, we tackled the following:
- **An overview of object detection algorithms:** one and two stages object detections algorithms (RCNN family and YOLO)
- **A post processing method for detections:** NMS and soft NMS
- **A new metric: mean average precision** and how to calculate it
- **The TensorFlow object detection API:** a framework to train object detection algorithm with TensorFlow
- **Tips and tricks to train and monitor NN:** how to leverage different tools and a recipe to follow when training new architectures
