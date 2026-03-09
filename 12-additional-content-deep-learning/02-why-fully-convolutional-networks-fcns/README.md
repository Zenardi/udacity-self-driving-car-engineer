# Why Fully Convolutional Networks (FCNs) ?

> Part of: **Fully Convolutional Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=WQ_YOz1o9GM)

## Summary

**Fully Convolutional Networks (FCNs)**
=====================================

A **convolutional neural network (CNN)** is a powerful architecture for image classification tasks. However, when the task requires identifying specific locations within an image, traditional CNNs may not be sufficient.

### Key Concepts
*   **Convolution layers**: These layers apply filters to small regions of the input image, scanning the entire image in a sliding window fashion.
*   **Fully connected (dense) layers**: These layers are used for classification tasks and do not preserve spatial information about the input image.
*   **Soft max activation function**: This function is used as the final layer in traditional CNNs to produce a probability distribution over all classes.

### Practical Notes
When working with images of varying sizes, traditional CNNs may not be effective due to the limitations of fully connected layers. In contrast, **fully convolutional networks (FCNs)** can handle images of any size by preserving spatial information throughout the network. FCNs are particularly useful for tasks like object localization or image segmentation.

**Example Use Case:** Consider a task where you need to identify the location of objects within an image. A traditional CNN may not be sufficient, but an FCN can effectively handle this task while maintaining the ability to work with images of any size.

## Transcript

<v English>A typical convolutional neural network might consist of a series of convolution layers.</v> <v English>Followed by fully connected layers and ultimately a soft max activation function.</v> <v English>This is a great architecture for a classification task like,</v> <v English>is this a picture of a hotdog?</v> <v English>But what if we want to change our task ever so slightly.</v> <v English>We want to answer the question,</v> <v English>"where in this picture is the hotdog?".</v> <v English>The question is much more difficult to answer since</v> <v English>fully connected layers don't preserve spatial information.</v> <v English>But turns out, if you change the C from connected to convolutional,</v> <v English>we can integrate convolutions directly into the layer to</v> <v English>create fully convolutional networks or FCN's for short.</v> <v English>FCN's help us answer where is the hotdog question.</v> <v English>Because while doing the convolution they preserve</v> <v English>the spatial information throughout the entire network.</v> <v English>Additionally, since convolutional operations</v> <v English>fundamentally don't care about the size of the input,</v> <v English>a fully convolutional network will work on images of any size.</v> <v English>In a classic convolutional network with fully connected final layers,</v> <v English>the size of the input is constrained by the size of the fully connected layers.</v> <v English>Passing different size images through the same sequence of</v> <v English>convolutional layers and flattening the final output.</v> <v English>These outputs would be of different sizes,</v> <v English>which doesn't bode very well for matrix multiplication.</v> <v English>We will dive more into details of fully convolutional networks next.</v>
