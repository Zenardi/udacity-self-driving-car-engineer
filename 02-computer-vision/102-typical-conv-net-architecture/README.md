# Typical Conv Net Architecture

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=oIpiI-R5su8)

## Summary

**Convolutional Neural Networks (CNNs)**
=====================================

A CNN is a type of neural network that can be used for image classification tasks. It's composed of multiple layers, including convolutional, activation, and pooling layers, which are often repeated to form a block.

### Key Concepts

* **Convolutional Layers**: These layers apply filters to the input image to detect patterns or features.
	+ Each filter is a small matrix that slides over the entire image, performing a dot product at each position.
	+ The output of a convolutional layer is a feature map, which represents the presence and strength of different features in the image.
* **Activation Layers**: These layers apply an activation function to the output of the convolutional layer to introduce non-linearity into the model.
	+ ReLU (Rectified Linear Unit) is a popular activation function that outputs 0 for negative inputs and the input value for positive inputs.
* **Pooling Layers**: These layers downsample the feature maps produced by the convolutional layer to reduce spatial dimensions and retain only the most important features.
	+ Max pooling selects the maximum value in each region, while average pooling calculates the average value.
* **Feedforward Neural Network (FFNN)**: This is a type of neural network that uses a fully connected architecture to classify images.
	+ The output volume from the convolutional block is flattened into a vector and passed through one or more FFNN layers.

### Practical Notes

When designing a CNN, it's essential to experiment with different hyperparameters, such as filter size, stride, and number of blocks. A good rule of thumb is to increase the number of filters in each convolutional layer as the depth of the network increases. This allows deeper layers to detect more complex patterns.

In this lesson, we also discussed the concept of embeddings or image representations, which are used to flatten the output volume from the convolutional block into a vector that can be passed through an FFNN.

The example architecture presented in this lesson is LeNet-5, a simple yet powerful CNN designed for handwritten digit classification. It consists of multiple convolutional and pooling layers followed by fully connected (linear) layers.

## Transcript

In the previous videos, we learned about convolutional and pooling layers. Well, now we have enough to start stacking layers and create our first convolutional neural network. A lot of covenant architectures follow the same pattern. We start with a convolutional layer, we then use an activation layer. An activation layer is similar to what we have seen in the lesson on feedforward neural network.

ReLu is one of the most popular activation. This activation layer is followed by a pooling layer, either max or average pooling. These three layers are often described as a block, and many covenant architectures consists in a repetition of this block. Keep in mind that the different layers hyperparameters, so just stride or filter size, as well as the number of blocks in your architecture need to be experimented with. There is no free lunch theorem, and an architecture that works well for problem may not perform as well for another one.

Finally, a good rule of thumb is to increase the number of filters in a convolutional layer with the depth of the network. For example, your first layer may have 16 filter. You second layer 64, and you third 256 filters. Why do we do this? Each filter is going to learn how to detect a pattern or a feature.

Filters in shallow layers are going to recognize simple patterns, such as edges or line. By increasing the number of features with the depth, we allow the filters in deeper layer to combine more features and detect more complex patterns. For example, in the case of traffic sign classification, filters in deeper layer may recognize numbers on the traffic signs. There is something we haven't talked about yet. How the convolutional neural network is going to classify images.

So far, what we have created is a stack of convolution, activation and pooling layers. The output of such a stack is a volume. How do we use this volume to classify the image? Well, we are going to bring back an old friend of ours, the feedforward neural network. We are going to flatten this output volume and fit it into a small feedforward network.

Such network is usually made of two or three layers. The number of neurons in the last layer is equal to the number of classes we are trying to separate. One of the consequences of using a feedforward neural network is a constraint that in imposes on the input image dimensions. Convolutional layer are not sensitive to the image dimension, meaning that you could fit different image sizes to the same layer. However, we need a constant size output volume to know the number of neurons in the first feedforward layer.

Because all the neuron in this layer will be connected to all the neurons of the output volume. By the way, the flatten vector created by reshaping the output volume is called an embedding or image representation. There's a whole field of research that consists in learning the best possible embeddings. Finally, by using linear layers at the end of the network, we are dramatically increasing the number of parameters. Some modern architectures have over 50 million parameters, and more than 80 percent of them are contained in the linear layers.

By the way, we sometimes use the term feature extractor to talk about the convolutional blocks, and the term classifier to talk about the linear layers. Let's look at a first architecture together. I'm very excited to show you a first convolutional architecture, LeNet-5. It's a very simple yet powerful architecture. It was originally designed to classify handwritten digits.

The image size for this network is 32 by 32. The first convolutional layer of this network has six filter of size 5 by 5. By the way, for convolutional layer, padding is defaulted to zero, and stride to one. If I do not mention these parameters, they take the default value. The next layer is an average pooling layer using filter size of 2 by 2, and a stride of two.

We then use another pair of convolutional and pooling layer with a higher number of filters for the convolutional layer. Finally, the last three layers, are fully connected layers or linear layers. Because we're trying to classify digits from 0-9, the last layer has 10 neurons. We can use a ReLu activation for each layer, apart from the pooling layer that do not use activation and the last layer that uses ta softmax. This is your first convolutional neural networks.

This is one of the simplest, yet it performs very well on many problems. We will study more architecture in the following videos. But we first need to talk about two more types of layers you will encounter in neural networks.

## Additional Content

## Typical Convolutional Network Architecture
The following pattern is common in CNNs architectures:
- Convolutional layer 
- Activation
- Pooling

Such block of layers is then repeated. Another common strategy is to **increase the number of filters in convolutional layers with depth**. 

The output of the last convolutional layer is flattened and fed into a classic feedforward NN, called a classifier, similar to the ones seen in the previous lesson. Because the first fully connected layer of the classifier needs a fixed size input, CNNs with such designs require a fixed resolution input image.
