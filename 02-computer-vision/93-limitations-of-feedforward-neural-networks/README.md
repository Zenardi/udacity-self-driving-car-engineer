# Limitations of Feedforward Neural Networks

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Emtlz3NBq08)

## Summary

**Convolutional Neural Networks (CNNs) for Image Classification**
===========================================================

This project introduces Convolutional Neural Networks (CNNs), a type of neural network designed specifically for image classification tasks.

### Key Concepts

* **Feedforward Neural Networks**: A type of neural network where each neuron is connected to every component of the input vector, resulting in a large number of parameters.
* **Reshaping Input Images**: The process of transforming 2D images into 1D vectors, which can lead to a large number of parameters and scalability issues for higher resolution images.
* **Convolution Operation**: A technique that allows neurons to be connected only to small spatial locations of the input volume, reducing the number of parameters and improving scalability.
* **Locally Connected Neurons**: Neurons in a convolutional layer are organized as a volume and slide over the input volume, connecting only to small spatial locations.

### Practical Notes

This lesson provides an introduction to CNNs and their advantages over feedforward neural networks for image classification tasks. Key takeaways include:

* The need for CNNs due to the limitations of feedforward neural networks in handling high-resolution images.
* The concept of convolutional layers, where neurons are locally connected to small spatial locations of the input volume.

In future lessons, you will have the opportunity to dive deeper into the implementation and application of CNNs.

## Transcript

Why do we need convolutional neural networks? In the previous lesson, didn't we successfully classify traffic sign using simple feedforward neural networks? Well, we did, but if you remember, we had to reshape the input image before feeding it into the network. What actually happened after the reshape operation? Well, each element of the reshaped input image is connected to each neuron in the first layer of our network.

If we consider a 64 by 64 RGB image and reshape it to one-dimensional vector, we created a vector of over 12,000 elements. What happens next in a feedforward neural network? Well, each neuron in the first layer is connected to each component of this vector, which means that each neuron in this layer has over 12,000 weights. If our first layer has 10 neurons, then we just created a new network of over a 120,000 parameters. We can see how this is not going to scale well to higher resolution images and deeper network.

Thankfully, the convolution operation is going to help us with that. What did we learn from the previous slide. Well, we learned that the limitation of the feedforward neural networks are the necessity to reshape the inputs, as well as the fact that each neuron is connected to all neurons in the previous layer. Instead of this approach, we're not going to reshape the image, but instead we'll consider it as an input volume of dimension height, by width, by depths. Neurons will only be connected to small spatial location of the input volume.

We will say that they are locally connected. What does it look like? Well, in a convolutional layer, our neurons will be organized as a volume and it will slide over the input volume. By doing this, we are solving our problem. Neuron in this volume, are only connected to a small spatial location of the input volume.

We will get a chance to do a deeper dive into convolutional layer in the next videos. But first, I wanted to give you a high level understanding of this layer.

## Additional Content

## Limitations of Feedforward Neural Networks
*From 1:32-onward in the above video, the first bullet should say "No resizing is needed".*
Flattening the image is required to use it as an input to a fully connected layer. In the previous lesson, we saw that a fully connected layer of `n` neurons following a layer of `m` neurons has `(m+1)xn` parameters. 

If our network has a single layer of 10 neurons and if we are using images of resolution `64x64x3`, this layer will have 122880 weights and 10 biases. This is not going to scale well with more layers, more neurons and a higher image resolution. Thankfully, convolutional layers will help solve this problem! 
Instead of flattening the image, we are now considering the image as an input volume. The convolutional layer, as opposed to the fully connected layer, will be **locally connected**. Indeed, each neuron in the convolutional layer will only be connected to small portion of the input volume.
