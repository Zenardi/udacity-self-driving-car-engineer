# Lesson Conclusion

> Part of: ** Detecting Objects in Lidar**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2TpwSQpuliY)

## Summary

**Object Detection using Point Clouds**
=====================================

This summary covers the key concepts, practical steps, and real-world applications discussed in the lesson on object detection using point clouds.

### Key Concepts

* **Point Cloud Data Representation**: Understanding how to represent 3D data as a set of points in space.
* **Feature Extraction**: Methods for extracting relevant features from point cloud data, such as intensity, height, and point density.
* **Convolutional Neural Networks (CNNs)**: Architecture used for detecting objects in point clouds by transforming the point cloud into a bird's-eye perspective.
* **Complex-YOLO Detector**: A specific detector that uses CNNs to search for vehicles in point cloud data.
* **Recall and Precision Metrics**: Evaluating the performance of detectors using well-established metrics.

### Practical Notes

* To implement object detection using point clouds, you can use a library such as Complex-YOLO, which transforms the point cloud into a bird's-eye perspective and feeds it to a CNN for detection.
* When evaluating the performance of detectors, use recall and precision metrics to assess their accuracy.

## Transcript

Now, welcome to the end of this chapter here and also to the end of the entire lesson. You have really come a long way since leaving the lineup basics from the last lesson behind you, and now you have an overview of the most relevant categories for detecting objects based on point Cloud, which basically defend the respective approaches to data representation, to feature extraction, and also in the architecture of the detection network. In addition to this theoretical knowledge, you have also seen how one of the detectors on the market actually works, complex-YOLO in this case, which basically is by transforming a lighter point Cloud into a bird's-eye perspective, then feeding intensity and height and point density to a convolutional neural network to search for vehicles. Lastly, you also know how to assess the performance of detectors using a set of well-established metrics such as recall and precision. I believe that you are now equipped with all the knowledge you will need to tackle the actual midterm project which is about to come up for you.

Now it's the time to collect all your notes and pieces of code you have written so far and proceed to the next part of the course. See you there soon.

## Additional Content

## Lesson Conclusion
You now have an overview of the most relevant categories for object detection based on point clouds. These differ in their respective approaches to data representation, to feature extraction and in the architecture of the detection network. 

Also, you have seen how one of the available detectors actually works, which is by transforming a lidar point cloud into a birds-eye perspective and then feeding intensity, height and point density to a convolutional neural network to look for vehicles. 

Lastly, you know how to assess the performance of object detectors using recall and precision.
