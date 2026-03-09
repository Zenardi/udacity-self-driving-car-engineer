# Fully Connected to 1x1 Convolution

> Part of: **Fully Convolutional Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=xbPtOhkJW1A)

## Summary

**Preserving Spatial Information with Convolutional Layers**
===========================================================

This lesson introduces a technique for using convolutional neural networks (SCNs) to preserve spatial information in images. By replacing fully connected layers with one-by-one convolutional layers, the output tensor remains 4D instead of being flattened to 2D.

**Key Concepts**
---------------

* **Convolutional Layers**: These layers perform element-wise multiplication and summation by sweeping a kernel over the input image.
* **Spatial Information**: This refers to the location-specific features in an image that are preserved when using convolutional layers.
* **Kernel**: A small matrix that slides over the input image, performing calculations at each position.
* **Matrix Multiplication with Spatial Information**: Convolutional layers can be thought of as a form of matrix multiplication where spatial information is preserved.

**Practical Notes**
------------------

When implementing this technique, keep in mind that:

* The number of kernels in a convolutional layer is equivalent to the number of outputs in a fully connected layer.
* The number of weights in each kernel is equivalent to the number of inputs in the fully connected layer.

## Transcript

<v English>Let's use the first special technique in SCNs by replacing</v> <v English>a fully connected layer with one by one convolutional layers.</v> <v English>This will result in the output value with the tensor</v> <v English>will remain 4D instead of flattening to 2D,</v> <v English>so spatial information will be preserved.</v> <v English>This may sound daunting but it's actually simpler than you might think.</v> <v English>At the core, we're still doing the same math as before.</v> <v English>Recall, the output of the convolution operation is the result of sweeping the kernel over</v> <v English>the input with the sliding window and</v> <v English>performing element wise multiplication and summation.</v> <v English>One way to think about this is the number of kernels is</v> <v English>equivalent to the number of outputs in a fully connected layer.</v> <v English>Similarly, the number of weights in each kernel is</v> <v English>equivalent to the number of inputs in the fully connected layer.</v> <v English>Effectively, this turns convolutions into</v> <v English>a matrix multiplication with spatial information.</v>
