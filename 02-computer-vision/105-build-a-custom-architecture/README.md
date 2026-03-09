# Build a Custom Architecture

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=QpvVlF1Hfyc)

## Summary

**AlexNet and VGG Architectures**
=====================================

This project explores the AlexNet and VGG architectures, two pioneering deep learning models in computer vision.

### Key Concepts

* **Convolutional Neural Networks (CNNs)**: CNNs are a type of neural network designed for image classification tasks. They use convolutional layers to scan images at different scales.
* **AlexNet**: AlexNet is a CNN that won the 2012 ImageNet competition with a landslide victory. It has around 61 million parameters and uses large filter sizes (11x11) in its first convolutional layer.
* **VGG Architecture**: VGG is another popular CNN architecture that introduced smaller filter sizes (3x3) and deeper networks. It won the 2014 ImageNet competition and brought significant improvements over previous architectures.
* **Convolutional Blocks**: A conv block is a stacked convolutional layer followed by a pooling layer. VGG16 has five conv blocks, each with the same number of filters doubling for each block.
* **Receptive Field**: The receptive field of a neuron is the spatial area where the filter is convolved. Increasing the receptive field can improve performance but also increases the number of parameters.
* **Skip Connections (Residual Learning)**: Skip connections are a technique introduced in ResNet that allows deeper networks to learn residual mappings instead of the original mapping. This approach enables the creation of very deep architectures with improved performance.

### Practical Notes

To implement these architectures, you can use popular deep learning frameworks such as TensorFlow or PyTorch. The key concepts outlined above should be applied when designing and training your own CNN models for image classification tasks.

Some practical steps to keep in mind:

* Use smaller filter sizes (3x3) instead of larger ones (11x11) to improve performance.
* Implement convolutional blocks with increasing numbers of filters to take advantage of the VGG architecture's design.
* Consider using skip connections or residual learning to create deeper networks with improved performance.

Note that this project focuses on understanding the key concepts and architectures rather than implementing them from scratch. You can use pre-trained models and libraries to get started with your own projects.

## Transcript

I previously mentioned the ImageNet competition, a yearly event where teams of researcher try to create the best image classification algorithm possible. Well, in 2012, a CNN named AlexNet won the competition by a landslide. Even though some of the design choices made by AlexNet are a little out of date now, it was such a groundbreaking algorithm in the field of deep learning for computer vision, that I wanted us to learn about it. AlexNet takes a 224 by 224 RGB image as an input. The first layer is a convolutional layer made of 96 filters of size 11 by 11.

It is followed by 3 by 3 max pooling layer. The rest of the architecture is made of convolution and pooling layers. The last few layers are fully connected, and since the ImageNet data-set contains 1,000 classes, the last layer has 1,000 neurons. In total, AlexNet has around 61 million parameters. The most important detail I would like you to remember about AlexNet is the filter size of the first convolutional layer.

As we will see, such a large filter size is a design decision that was quickly abandoned in more modern architecture. Overall, AlexNet is not particularly used anymore, unlike the VGG network that we are going to study in the following video. Whereas AlexNet is not an architecture that you will encounter in modern CNNs, the VGG architecture is one that is still very popular nowadays. The VGG algorithm won the 2014 ImageNet competition and brought the following improvements: It uses smaller filter sizes for the convolutional layers and is much deeper than previous architectures. Two version of the VGG architecture exist.

VGG16 and VGG19 with 16 and 19 layers respectively. In this video, we are going to look at the VGG16 version. The VGG introduced the notion of convolutional block or conv blocks. A conv block is made of stacked convolutional layer followed by a pooling layer. For example, VGG 16 has five conv blocks.

In this architecture each convolutional layer in a block has the same filter size 3x3, and the same number of filters, whereas the filter size remain constant in this network, the number of filters doubles for each conv block. This approach remains one of the most common design of convolutional neural networks. What are the pros of using smaller filter sizes in comparison to larger one, like in AlexNet? Remember when I mentioned that the spatial area where the filter is convolved is called the receptive field of a neuron? If you start multiple convolutional layer with 3x3 filter, you increase the receptive field of the neurons in the last layer.

Let's look at an example of three stacked convolutional layer, which is similar to what we have in the last conv blocks of the VGG16 architecture. Let's look at an element of a depth slice of the last output volume. The filter size of the last layer is 3x3. We can draw the receptive field of this element. We can repeat this operation for each element of this array and then we can repeat this operation again and obtain a 7x7 square.

Basically a block of three convolutional layer with a filter size of 3x3, has the same receptive field than a single convolutional layer with a 7x7 filter size. How is that an improvement? Having three layers introduces more non-linearity in our system. Which is great because we are trying to understand complex signals and it also reduces the number of parameters. Indeed, a stack of three convolutional layer with 3x3 filters has less parameter than a single convolutional layer with 7x7 filters.

We will go over this calculation in your future exercise. For now, I want you to remember this convolutional block design and the smaller filter sizes. There is one last architecture that I would like us to go over, the resonant model because it introduced another very important concept. But first, let's talk about an issue that architecture like VGG have. VGG was the first way deep convolutional neural network, and researcher realize that going deeper was improving performances.

Naturally, people tried stacking even more layers than VGG. However, they quickly realized that the performances of such network was degrading when extra layers were added. As we can see here, not only the error on the test set is higher for networks with more layers, but also the error on the training set. Overfeeding is not the problem here. Why are larger networks getting worst performances?

Indeed, deeper network should not perform worse than shallower ones. Let's consider the VGG network, for example. If we added a few more convolutional blocks to it, this new network should at least perform as well as the original architecture simply because this newly added layer could learn the identity function. But in practice, researcher did not observe that and the author of the ResNet paper argued that it was way too hard to optimize over larger architectures. To remediate this, they introduced shortcuts or skip connections, which we'll learn about in the next slide.

The author of ResNet decided to add skip connection, meaning that the input of a convolutional block is added to its output. Let's add some formal notation by calling x our input and f of x, the mapping of the input x. Without the skip connection, the curve block is trying to learn f of x. With the skip connection, the curve block is now trying to learn f of x minus x, which is the residual of f of x. The author argue that it is easier to learn the residual mapping than the original mapping.

With this simple trick, they were able to create very deep architecture such as ResNet 101 that contains 101 layers, or ResNet 152 that contains 152 layers. Thanks to this approach, the author won the 2015 ImageNet competition. Skip connection are a very important component of modern architecture. The ResNet model remain one of the most popular model to date for image classification.

## Additional Content

## Build a Custom Architecture

### AlexNet
The **Alexnet** architecture was a critical breakthrough in the field of computer vision for deep learning. In this [2012 paper](https://proceedings.neurips.cc/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf), the authors successfully used a CNN trained on GPU to classify images. 







### VGG
In this [2015 paper](https://arxiv.org/pdf/1409.1556.pdf), the authors introduced two very important concepts:
- using smaller filter sizes, in this case `3x3` filters.
- using convolutional blocks: blocks of 2 or 3 convolutional layers followed by one pooling layer. 

By stacking multiple convolutional layers with small filters, we create a block that has less parameters than a single layer with larger filter sizes, while having the same effective receptive field and more non-linearities.
### ResNet
In another very important [paper published in 2015](https://arxiv.org/pdf/1512.03385.pdf), the authors introduced the Resnet architecture. They realized that networks with more layers started underperforming. To solve this and allow for deeper networks, the authors introduced the concept of **residual connections** or **skip connections**. A skip connection simply adds the input of a layer or a block of layers to its output. By doing so, it will alleviate gradient propagation issues linked to activation functions.
### Inception

One last neural network that may be of interest to you is the Inception network, introduced in [this 2014 paper](https://arxiv.org/pdf/1409.4842.pdf). While it is beyond the scope of this course, it also has some interesting and ground-breaking research, such as the use of multiple different sizes of convolutional filters within a "layer", as well as the use even of 1x1 filters, enabling deep networks with often fewer parameters. Make sure to check out the paper if you want to dive deeper!
