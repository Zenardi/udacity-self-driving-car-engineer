# Waymo: Deep Learning

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=wvNYWi--fQc)

## Summary

**Machine Learning in Autonomous Driving**
=====================================

This project focuses on applying machine learning to various aspects of autonomous driving, including perception, behavior prediction, planning, and simulation. The goal is to leverage the power of deep learning models, optimized for TensorFlow, to improve system performance while minimizing energy consumption.

### Key Concepts

* **Supervised Learning**: A traditional approach to machine learning where the model learns from labeled data.
* **Deep Learning**: A subset of machine learning that uses neural networks with multiple layers to learn complex patterns in data.
* **TensorFlow**: An open-source framework developed by Google for training and optimizing neural networks.
* **TPUs (Tensor Processing Units)**: Specialized hardware designed specifically for efficient execution of tensor operations, providing a significant boost in performance over GPUs.

### Practical Notes

To apply machine learning to autonomous driving, you can follow these steps:

1. Choose a suitable deep learning framework, such as TensorFlow, and select the most relevant models for your specific use case.
2. Optimize model size and complexity to balance quality with computational resources.
3. Utilize parallel computation hardware like GPUs or TPUs to accelerate model execution and reduce energy consumption.

Note: This project assumes prior knowledge of machine learning concepts and programming experience with TensorFlow.

## Transcript

We can use machine learning anywhere in the autonomous driving stack. The research team, which I lead, works on projects spanning multiple disciplines including perception, behavior prediction, planning, and even simulation. Traditionally, learning has had a lot of success in the supervised learning setting, which was well-suited and represented in perception. Since then, the uses of machine learning and deep learning specifically have broadened and reached every aspect of our system. TensorFlow is a framework developed by Google for training neural networks.

The amount of deep learning models that we'd like to run on the vehicle keeps increasing. Often, the size of these models is correlated to quality as well. So often you can turn additional computational capability into better quality. As such, we're interested in running a lot of parallel computation optimized for TensorFlow trained models, for example, with as little energy as possible. Recently there has been tremendous strides in the industry to enable this.

Examples of hardware that executes parallel computations really efficiently is GPUs and recently even TPUs, which raise the efficiency a whole other level. Google is one of the leader in TPUs which have been really helpful for us at Waymo even training the models. But this is also hardware that can help random models. The TPU is another type of hardware called Tensor Processing Unit. It's in a way a successful better branding, but also it illustrates additional optimization over GPUs in how computation and memory are distributed for neural network execution.

## Additional Content

## Waymo: Deep Learning

As you might guess, Waymo uses Deep Learning extensively in their autonomous vehicles, including using the TensorFlow library for deep learning models. Below, Dragomir, Distinguished Scientist at Waymo, will walk you through their approach, as well as the hardware used in their vehicles to run deep learning models.

### How Autonomous Vehicles use Deep Learning
### TensorFlow
### Electronic Control Units
### What is a TPU?
