# Introduction to Tensorflow

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=i9DY47pX2Kg)

## Summary

**TensorFlow Tensors: A Practical Guide**
=============================================

This guide covers the basics of TensorFlow tensors and how they differ from NumPy arrays.

### Key Concepts

* **Tensors**: Special type of arrays used in TensorFlow, similar to NumPy arrays but with additional features.
* **Conversion between NumPy and TensorFlow Arrays**:
	+ Use `tf.convert_to_tensor()` to convert a 2D NumPy array to a tensor.
	+ Use the `tensor.numpy` method to convert a tensor back to a NumPy array.
* **Tensor Attributes**: Tensors share many attributes with NumPy arrays, such as:
	+ **Shape**: The dimensions of the tensor.
* **Operations on Tensors**:
	+ Element-wise multiplication is possible on tensors.
	+ Broadcasting rules apply to tensors, similar to NumPy arrays.
* **Device Management**:
	+ Use `tensor.device` to get the device where the tensor is loaded (e.g., CPU or GPU).
	+ Move a tensor from one device to another using `tensor.cpu()` or `tensor.gpu()`.

### Practical Notes

When working with tensors, keep in mind that they have additional methods not available in NumPy arrays. Be sure to use the correct conversion functions and attributes to manage your data effectively.

## Transcript

Let's take a break from the theory of machine learning and learn some new TensorFlow features. TensorFlow uses a special type of arrays called tensor. As you will see, tensors have a lot of common is NumPy arrays. Let's start by defining the following; 2D NumPy array. We can convert it to a tensor using the TensorFlow function, convert_to_tensor.

We can also convert any tensor back to a NumPy array by using the tensor.numpy method. Tensors share a lot of similar attributes with NumPy arrays such as shape. Moreover, the same operation, such as element-wise multiplication, are also possible on tensors. Similar broadcasting rules on NumPy array also apply to TensorFlow tensors. Tensors, however, have additional methods that are not available to NumPy arrays.

For example, the tensor.device attribute will output the device on which the tensor has been loaded, such as CPU or GPU. Similarly, we can call tensor.cpu or tensor.gpu to move the tensor from one device to another.

## Additional Content

## Introduction to Tensorflow
Tensorflow **tensors** are data structure sharing many attributes and properties with numpy arrays (such as `.shape` and broadcasting rules).  They do have additional attributes, allowing the user to move tensors from one device to another (cpu to gpu for example).
You can use the workspace below to try out the code in the video.
