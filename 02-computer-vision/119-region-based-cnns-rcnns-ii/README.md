# Region-Based CNNs (RCNNs) II

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=jcZdeUQiFoI)

## Summary

**README: Understanding Fast-RCNN and Faster-RCNN**

Fast-RCNN and its successor, Faster-RCNN, are two algorithms developed to improve the efficiency and accuracy of object detection in images. This summary provides a detailed overview of the key concepts, practical steps, and real-world applications of these algorithms.

**Key Concepts**

* **Region of Interest (ROI)**: A ROI is described by four coordinates and is used to determine if an image region contains an object.
* **Fast-RCNN**: Introduced a multi-task loss that combines classification and regression problems, enabling end-to-end training of the model.
* **Faster-RCNN**: Replaces selective search with a Region Proposal Network (RPN) to generate regions of interest, improving efficiency.
* **Region Proposal Network (RPN)**: A network that takes feature maps as input and generates proposals for bounding boxes and objectness scores.
* **Anchor Boxes**: Fixed-size windows slid over the feature map to generate anchor boxes with different scales and aspect ratios.

**Practical Notes**

* Fast-RCNN relies on selective search to generate regions of interest, which can be a slow process.
* Faster-RCNN uses an RPN to generate regions of interest, improving efficiency compared to Fast-RCNN.
* To train the RPN, positive anchors (those that overlap with ground-truth bounding boxes) and non-positive anchors are defined, and a multi-task loss is used.

Note: This summary provides a high-level overview of the key concepts and practical steps involved in understanding Fast-RCNN and Faster-RCNN. For more detailed information, refer to the original papers or re-watch the Udacity lesson videos.

## Transcript

Even though SPPnet was a tremendous improvement over the RCNN algorithm in terms of complexity and runtime, it is still had one major limitation. Three different models needed to be trained. An object proposal model to determine if a region is an object or not, a classifier model to classify the different objects, and the regressor model for the bounding boxes. Well, fast-RCNN takes a slightly different approach. During training, regions of interest or ROI are being generated for each image.

A region of interest is simply described by its four coordinates. Similarly to a bounding box, This image is fed into a CurveNet and each ROI is fed to a ROI pooling layer, which is similar to a one-level SPP layer. If you have followed me so far, the ROI pooling layer will output a fixed-length vector. Such vector will then be fed into the classifier and the bb box regressor. The mechanism to enable fast-RCNN to be faster than SPPnet are actually a little more complex and you should read the paper if you want a deeper understanding of this algorithm.

The main points I want you to remember about fast-RCNN are the following: fast-RCNN introduced a multi-task loss that combines the classification and regression problems. It also enabled end-to-end training, meaning that each modules are trained together. It is important that you remember the region of interest or ROI, as it is frequently used in other research paper for object detection. Overall, fast-RCNN is both faster and better than SPPnet and RCNN. But the RCNN saga is not over and the author actually came up with more ideas that we will tackle in the next videos.

What is the main bottleneck of the Fast-RCNN algorithm? Well, it still relies on selective search to generate regions of interest, which is a somewhat slow process, while Faster-RCNN, the last child of the RCNN family, gets rid of this step by introducing a region proposal network or RPN. What's the idea behind the RPN? Where the author estimated that the feature maps created by the Com-nets could be used to calculate region of interest, in addition to use them for classification and regression. This is exactly what an RPN does as shown by this figure on the right.

It takes the feature maps and generate proposals which are a set of bonding boxes and objectness scores. Once the region of interests are generated with the RPN, the rest of the algorithm works similarly than a Fast-RCNN model. But how does this RPN exactly work? We'll take a deeper look in the next slide. How does this RPN generates region of interest exactly?

Well first, we need to introduce another very important concept, anchor boxes. In the region proposal network, we are going to slide a window over the feature map. For each location of the sliding window on the feature map, we will generate k anchor boxes, with k being a hyperparameter. Anchor boxes have different scales and different aspect ratio. Let's take a step back and try to understand what's going on here.

We're training an algorithm to learn region of interest from feature maps. This algorithm works as follow; it slides a window over the feature map. Each window is being mapped to fixed-size vector. That vector is being fed to two fully convolutional layers. One that estimates the objectness score and the other one that regresses the ROI coordinates.

How do we train this model? We define positive anchors and non-positive anchors. Positive anchors contain an object if they overlap with the ground-truth bonding boxes. We also use a multi-task class to train the RPN. But the regression part of the loss is only used for positive anchors.

Hopefully, now you have a good understanding of the Faster-RCNN networking. I encourage you to re-watch these videos and read the original papers to further your understanding of the RCNN algorithm. Despite being a relatively old paper, in terms of deep-learning research, Faster-RCNN is still one of the most used object detection algorithm. In the next video, we will tackle one more object detection algorithm.

## Additional Content

## Region-Based CNNs (RCNNs) II

### Fast-RCNN
The [Fast RCNN](https://arxiv.org/pdf/1504.08083.pdf) improves over RCNN and SPPNet by using a **multi-task loss** and taking an **end to end** training approach, meaning that a single loss function is used for both classification of the object and regression of the bounding boxes. Therefore, the model can be trained as a single entity, instead of having to train the different modules separately. This model also uses **region of interest (ROI) ** pooling, a 1 level SPP layer. 
### Faster-RCNN
The [Faster RCNN architecture](https://arxiv.org/pdf/1506.01497.pdf) is the latest iteration of the RCNN family. 

It improves over RCNN and FastRCNN by not relying on selective search. Instead, it uses a **Region Proposal Network (RPN)** to generate the ROIs. The RPN uses the feature maps of the last convolution layer to generate the ROIs. The RPN uses a sliding window over the feature maps and for each position of this window, it generates k **anchor boxes**. These anchors boxes are used to determine if the region contains an object or not. 

Thanks to a multitask loss function, all the components of FasterRCNN are trained simultaneously.
