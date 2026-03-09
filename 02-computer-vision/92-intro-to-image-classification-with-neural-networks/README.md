# Intro to Image Classification with Neural Networks

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=pH0PMjPKifM)

## Summary

**Convolutional Neural Networks (CNNs)**
=====================================

This lesson introduces Convolutional Neural Networks (CNNs), a type of neural network particularly suited for analyzing image data. We'll explore why CNNs are perfect for image classification, object detection, and semantic segmentation.

### Key Concepts

* **Convolutional Neural Networks (CNNs)**: A type of neural network designed to process data with grid-like topology, such as images.
* **ImageNet Competition**: A competition where researchers aim to achieve the best performance on large-scale image classification datasets. CNN architectures have dominated this competition since 2012.
* **Feed-Forward Neural Network Limitations**: Traditional feed-forward neural networks are not well-suited for image data due to their lack of spatial hierarchy and translation invariance.
* **Convolution Layer**: A critical component of CNNs, responsible for scanning the input data with a set of learnable filters to extract relevant features.
* **Pooling Layers**, **Dropout**, and **Batch Normalization**: Common types of layers used in modern CNN architectures to improve performance and stability.

### Practical Notes

* To create custom convolutional neural network architectures, you'll need to understand how to organize the various layers, including convolutional, pooling, dropout, and batch normalization.
* We'll explore classic and modern CNN architectures, such as ResNet and VGG, and learn about augmentations, a technique for virtually increasing the size and variability of image datasets.

## Transcript

Welcome for the next lesson of this course. In this lesson, we are going to concentrate on a special type of neural networks, convolutional neural networks. We're going to see why these networks are perfect for analyzing image data. Let's get started. Convolutional neural networks or CNN or convnets are type of neural network particularly suited for image data.

I previously mentioned the ImageNet Competition, where a team of researchers tried to get the best possible performances on the classification datasets over one million images. Well, since 2012, this competition has been dominated by CNN architectures. Convnets are now at the core of most deep learning algorithm for computer vision, from image classification to semantic segmentation or object detection. I cannot wait for you to unleash the power of convolutional neural networks. I use them every day and I'm still amazed by their performances.

This lesson is going to be organized as follow. First, we're going to see why the feed-forward neural network introduced previously and not suited to image data. We will introduce the convolution layer as a solution. We're going to spend a lot of time talking about this layer, and it is critical that you get a good understanding of its properties. Convnets are not only made of conditional layers, but also other types of layer, such as pooling layers, dropout, or batch normalization, which are very common to find in modern architectures.

We will then learn how to organize these layers to create custom convolutional neural network architectures to classify traffic signs. We'll spend some time studying classic and modern convnet architecture, such as ResNet or VGG. Finally, we will spend the last part of the lesson learning about augmentations, a way to virtually increase the size and variability of your image datasets. Convnets are very exciting addition to feed-forward neural network, and I'm really excited for you to learn about them.

## Additional Content

## Intro to Image Classification with Neural Networks
This lesson will focus on **Convolutional Neural Networks**, also known as **CNNs** or **Convnets**. CNNs are a special type of neural network particularly well suited to image data. Since 2012, the [ImageNet competition](http://www.image-net.org/) has always been won by CNN architectures.
In this lesson, we will tackle:
- Limitations of feed-forward networks 
- The convolution layer (conv layer)
- Pooling layers, dropout and batch normalization (batchnorm)
- Build a custom architecture to classify traffic signs
- Modern architectures
- Augmentations
