# Convnet Layers and Parameters

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=0gSk4jbHkww)

## Summary

**README: Understanding Convolutional Layers**

Convolutional layers are a fundamental component of deep learning models, particularly in image recognition tasks. This summary provides an overview of key concepts related to convolutional layers, including their structure, parameters, and assumptions.

**Key Concepts**

* **Convolutional Layer Structure**: A convolutional layer consists of multiple filters that scan the input image to detect features at different spatial locations.
* **Filter Size and Stride**: The filter size determines the number of pixels considered by each filter, while the stride controls how many pixels are skipped between consecutive applications of the filter.
* **Shared Weights and Biases**: In a convolutional layer, it is assumed that all neurons at the same depth share weights and biases, reducing the total number of parameters.
* **Feature Detectors**: Filters in a convolutional layer act as feature detectors, identifying specific patterns or features in the input image.
* **2D Feature Maps**: Visualizing 2D feature maps helps understand what the neural network is learning from the input data.

**Practical Notes**

* To calculate the number of parameters in a convolutional layer, you can use the following formula: `number_of_parameters = (filter_size^2) * number_of_filters + number_of_filters`
* Understanding the number of weights and biases in each layer is crucial to prevent overfitting and optimize model performance.
* Modern convolutional architectures often have millions of weights, while mobile-oriented models may have fewer than a million.

Note: This summary focuses on the key concepts introduced in the lesson. For more detailed information or code examples, please refer to the Udacity course materials.

## Transcript

Let's use the following example to count the number of parameters in a convolutional layer. We have our 64 by 64 by three input image. The first layer of our network is a convolutional layer with the following hyperparameters; the stride is equal to one, we do not use padding, we use a filter size of three, and we use 32 filters. Using this formula, we can calculate the output size and we get an output volume of the following dimension, 62 by 62 by 32. Each element of this output is a neuron that has three by three by three weights and one bias parameter.

Let's do some quick math. Each neuron of this layer has 28 parameters. We have in total over 123,000 neuron in this layer. Given the number of weights per neuron, the number of trainable parameters for the first layer reaches over there million. I initially claimed that convolutional layer were improving over feedforward layer partially because they reduced the number of weights.

However, three million weights is very high for a single layer. Well, we are actually going to make the assumption that all the neurons at the same depths are sharing weights and biases. Instead of 62 by 62 by 32 neurons in our layer, we will only have 32 neurons. This is bringing down the number of parameter for this layer to 32 by 28, which is a little less than 900. Why can we make this assumption?

In a convolutional layer, a filter act as a feature detector. With this assumption, we are saying that a feature learned at a particular spatial location should also be useful at a different spatial location. Let's look at this image for example. Well, for example, if one of our filter is a left ear feature detector, wouldn't it be useful to have this filter available at other spatial locations? To better understand the role played by the filter, we can visualize the 2D feature maps of each filter.

This is a great way to understand what our neural network is learning. Let's consider the following architecture. We have a very small convolutional neural network with only two convolutional layers. How many parameters does our cabinet have? For the sake of simplicity, we will consider that both layers are using a stride of one and no padding.

They are also both using a filter size of three. Because the input of our first layer is a RGB image, its depth is equal to three. Therefore, each neuron in the first layer will have 27 weights and one bias. Because we have 64 neurons in this layer, the total number of weights for this first convolutional layer of our network is 27 times 64, which is equal to 1,728. The second layer, however, takes an input volume of depth 64.

Hence, each neuron of the second layer will have three by three by 64 weights, which is equal to 577. Because these layers has 128 neurons, the total number of weights in the second layer is 577 times 128, which is over 73,000. Modern convolutional architecture have a few millions of weights in general, but some mobile-oriented models barely reached a million. Being able to count the number of weights in the network is pretty important as you want to keep in mind the number of learning parameters in case you're starting to overfit. It is also important to understand how the parameters of each layers affect the total number of parameters.

With this, we are now done with the convolutional layer and we can focus on other types of layer present in convolutional neural networks.

## Additional Content

## Convnet Layers and Parameters
*At approximately 3:05, the math performed on the slide includes the bias parameter in the math, which I do not include while talking, leading to 27x64 instead of the 28x64 on the slide.*
A filter acts as a **feature detector** in convolutional layers, and the deeper the layer, the more specialized the filters are. For example, when training an algorithm to classify dog and cat images, a filter in a deep layer might be a *left ear detector*.

The number of parameters in a convolutional layer is determined by the filter size, the number of filters and the depth of the input volume `D`. If we consider a `3x3` filter size with `32` filters:
* each filter has `3x3xD + 1` learnable parameters
* the whole layer has `(3x3xD+1)x32` learnable parameters

CNNs have in general a few millions parameters but some mobile-oriented architectures barely reach one million.
