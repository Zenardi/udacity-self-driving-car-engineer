# History of Deep Learning

> Part of: **Introduction to Deep Learning for Computer Vision**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=rzcrRroQlZw)

## Summary

**Deep Learning and Neural Networks**
=====================================

This project introduces the fundamental concepts of neural networks, including their structure, terminology, and history.

### Key Concepts

* **Artificial Neural Network (ANN)**: an artificial network that resembles the structure of a biological neural network in the brain
* **Neural Network**: a network composed of interconnected nodes or "neurons" that process information
	+ **Layers**: vertical stacks of neurons, with input and output layers, and one or more hidden layers
	+ **Feedforward Neural Network**: a type of neural network where each neuron is connected to every neuron in the previous layer and next layer
* **Deep Learning**: a subfield of machine learning that uses deep neural networks with many layers to analyze data
* **Backpropagation Algorithm**: an algorithm created by Yann LeCun in 1989 for training neural networks, which is still at the core of modern neural network training

### Practical Notes

This project does not include any practical steps or code patterns. However, it provides a historical context and overview of the field of deep learning, including its key milestones and applications.

Some notable points from the lesson include:

* The first deep neural networks date back to the 1970s
* The backpropagation algorithm was created in 1989 by Yann LeCun
* The 1990s are considered the "winter" of deep learning, but scientists continued working on the topic and publishing groundbreaking papers
* The creation of large-scale datasets, such as ImageNet, marked a significant turning point for deep learning
* The introduction of AlexNet in 2012 revolutionized image classification using convolutional neural networks trained on GPUs

This project aims to provide a solid foundation for understanding the basics of neural networks and deep learning.

## Transcript

Before we dive into the history of deep learning, let's introduce a few terms to describe neural networks. By neural network, I actually want to talk about artificial neural network or ANN. This name come from their resemblance to neural networks in our brain. We can see an example of a neural network here. It's shown in this figure represents a neuron and the edges between the neurons represent the connection between them.

Neural networks are organized in layers, represented here as vertical stacks of neuron. This particular network has four layers. The left-most is the input and the right-most, the output layer. Any layer that is not the input or the output is called a hidden layer. This network has two hidden layers, but we'll later see in this course a lot of neural networks with many more layers.

The term deep learning comes from deep neural network where many layers are stacked. In this neural network, each neuron of a layer is connected to each neuron of the previous layer and each neuron of the next layer. We call such a network a feedforward neural network. Neurons received an input signal and are activated or not based on this input. We sometimes say that the neuron is firing when it's activated.

Don't worry, we'll go over all these notions again in the third lesson of this course. For now, I just want you to be familiar with these terms. Let's talk a little bit about the history of deep learning. Because of the recent deep learning revolution, one could assume that this technology is fairly young. However, the first deep neural networks date from the 70s.

The backpropagation algorithm, which is at the core of training neural network, was created in 1989 by Yann LeCun. He created this algorithm to train a network to recognize handwritten digits on mail. The 1990s are considered as the winter of deep learning when neural network were overlooked by many. However, many scientists kept working on the topic, and some groundbreaking papers were published, such as the Long Short-Term Memory paper in 1997. One of the core limitations of deep learning at the time was the hardware.

Training that digit recognition algorithm, for example, took over three days. However, at the beginning of the 2000s, computer became much faster and hours was less of a bottleneck. Deep learning started to be adopted in the industry. 2009 marks the creation of the first large scale data set. A Stanford University professor led the effort to create one of the biggest image data set to date, ImageNet.

With this dataset came a yearly competition where a researcher from both academia and the industry tried to create the best possible image classification algorithm. In 2012, a paper introduced a novel approach to image classification, a neural network called AlexNet. In my opinion, this paper is the single most groundbreaking research in deep learning for computer vision. This paper showed how a convolutional neural network can be trained using multiple graphic processing units or GPUs. It crushed the competition that year, and since AlexNet, a neural network-based approach train on the GPU has always won the competition.

Let's fast forward to 2020. In the past eight years, tens of thousands of papers have been published in the field of deep learning and deep neural network are now everywhere, from your phone where the process camera images to translation tool when natural language processing relies heavily on this technology, and finally, to self-driving cars. Deep neural networks are the core of the self-driving car technology, from digital image processing to 3D point lab processing to decision-making. This is a very exciting field to be working in right now. This course should give you a good introduction to the power of deep learning.

## Additional Content

## History of Deep Learning
**Artificial neural networks (ANN)** or simply neural networks are the type of systems at the core of deep learning algorithms.
* **ANN:** machine learning algorithms vaguely based on human neural networks.
* **Neurons:** the basic unit of neural networks. Takes an input signal and is activated or not based on the input value and the neuron's weights.
* **Layer:** structure containing multiple neurons. Layers are stacked to create a neural network.
