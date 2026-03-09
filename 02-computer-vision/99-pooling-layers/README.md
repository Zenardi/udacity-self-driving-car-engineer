# Pooling Layers

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=MQdrZlLGjxw)

## Summary

**README: Convolutional Neural Networks with Pooling Layers**

This project introduces a new layer for convolutional neural networks (CNNs), called the **pooling layer**. The goal of this layer is to spatially aggregate information, increasing the receptive field of neurons in deeper layers and reducing the number of parameters.

### Key Concepts

* **Receptive Field**: The area in the previous layer that a neuron will consider.
* **Pooling Layer**: A layer that aggregates information over the input volume, increasing the receptive field of neurons and reducing the size of output volumes.
* **Average Pooling** vs. **Max Pooling**: Two types of pooling layers, where average pooling takes the mean value and max pooling retains the maximum value.
* **Filter Size** and **Stride**: Parameters common to both convolutional and pooling layers, which determine how information is aggregated.
* **Computational Complexity**: Pooling layers do not increase computational complexity due to lack of learnable parameters.

### Practical Notes

To implement a pooling layer in a CNN:

1. Choose between average pooling or max pooling based on the specific problem and dataset.
2. Set the filter size (typically 2x2) and stride to control how information is aggregated.
3. Note that pooling layers can lead to loss of information, so use with care.

Example code for implementing a max pooling layer:
```python
import numpy as np

def max_pooling_layer(feature_map, filter_size, stride):
    # Calculate output shape
    output_shape = (feature_map.shape[0] - filter_size) // stride + 1,
                  feature_map.shape[1] - filter_size) // stride + 1
    
    # Initialize output array
    output = np.zeros(output_shape)
    
    # Perform max pooling operation
    for i in range(0, feature_map.shape[0], stride):
        for j in range(0, feature_map.shape[1], stride):
            output[i//stride, j//stride] = np.max(feature_map[i:i+filter_size, j:j+filter_size])
    
    return output
```
This code snippet demonstrates how to implement a max pooling layer using NumPy.

## Transcript

Let's introduce a new layer for our covnets, the pooling layer. The goal of the pooling layer is to spatially aggregate information. Why would we want to do this? I previously introduced the concept of receptive fields. You can think of the receptive field as the area in the previous layer that the neuron will consider.

Because in convolutional neural networks, we are stacking convolutional layer, the size of the receptive field of a neuron in deeper layer is higher than the one of a neuron in shallower layers. Well, thanks to the pooling layer, we are going to increase this receptive field even more than with planned convolutional layer. Let's look at an example. In this network, we have two layers. The first one is a pooling layer, and the second one is a convolutional layer.

Let's consider the receptive field of this neuron because we use this three by three filter, it's receptive field is a three-by-three square. The pooling layer is going to increase the receptive field of this neuron even more. Ultimately, we want the neurons in deeper layers to have larger receptive fields to get information from the whole input image instead of just a limited area. Another advantage of the pooling layer is its ability to decrease the number of parameters. Because we are aggregating information over the input volume, we're going to reduce the size of the output volumes, as we saw in the previous slide.

Finally, the pooling layer has some parameters in common with the convolutional layer, the filter size, and the stride. In the following slide, we are going to see a pooling layer in action. The most common type of pooling layers are average pooling and max pooling layers. Let's consider the following example. We have a feature map from the output of a convolutional layer.

This feature map is a four-by-four array. We are going to use a max pooling layer of filter size 2 and stride 2. For each one of the color-coded area, we're going to retain the maximum value and put it in the output feature map. For example, the maximum value of the red area is six. In a case of average pooling layer, we take the mean value instead of the maximum value.

Let's see some more properties of the pooling layer in the following slide. Pooling layers do not have any learnable parameters, and therefore, they do not increase the computational complexity of the convolutional neural network. Because we are aggregating information with the pooling operation, we also take the risk of losing information. Max pooling is a rather destructive operation, and we are making the assumption that the strongest signal is the most significant. Therefore, pooling operation should be used with care and the filter size should remain on the smaller side.

In general, machine learning engineer tend to favor a filter size of two-by-two for pooling layers. Whereas both pooling methods are popular, max pooling has empirically shown better performances and gained more popularity than average pooling. Finally, it is worth noting that convolutional neural networks do not necessarily require pooling layers, and some modern architecture do not have any. With the convolutional and pooling layers. We now have enough tools to build our first convolutional neural network.

## Additional Content

## Pooling Layers
**Pooling layers** are very common in CNNs. They decrease the number of parameters in the network by aggregating spatial information, usually by taking the mean (average pooling) or the max (max pooling). They do not have any learnable parameters.
