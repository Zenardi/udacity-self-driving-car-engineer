# Solution: Pooling Layers

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=zLFV4RXFrtk)

## Summary

**Max Pooling Layer Implementation**
=====================================

This README file provides an overview of implementing a max pooling layer in a neural network, including key concepts, practical steps, and real-world applications.

### Key Concepts

* **Max Pooling**: A technique used in convolutional neural networks (CNNs) to reduce the spatial dimensions of feature maps while retaining important information.
* **Padding**: Adding zeros to the input array to ensure that the filter size and stride can be applied evenly.
	+ **Get Paddings Function**: Calculates the required padding for a given input array, filter size, and stride using the formula: `padding = (filter_size - 1) / 2`.
* **Output Size Calculation**: Uses the formula `output_size = ceil(input_size / stride)` to determine the output size of the array after the pooling operation.
* **Max Pooling Operation**: Loops over the spatial dimensions to calculate the maximum value in each region.

### Practical Notes

To implement a max pooling layer, follow these steps:

1. Implement the `get_paddings` function to calculate the required padding for a given input array, filter size, and stride.
2. Use the calculated padding to pad the input array using NumPy's `pad` function.
3. Calculate the output size of the array after the pooling operation using the formula: `output_size = ceil(input_size / stride)`.
4. Initialize an input array filled with zeros based on the output size.
5. Loop over the spatial dimensions to calculate the maximum value in each region.

Note that max pooling operations should not be applied to the first dimension (batch-size) or the last dimension (number of channels).

## Transcript

In this exercise, you were asked to implement a max pooling layer. Similarly to the convolutional layer, the pooling layer can only take certain combination of filter sizes and stride, because we were asked that this function works with any filter sizes and stride, we had to pad the input array with zeros. To do so, you first have to implement the get paddings function. This function outputs padding given an input array, filter size, and stride. I calculated the required padding using the flow division of each dimension by the stride.

I'm using this paddings to pad the input array using Np.pad. Because we're doing a max pooling operation, I can safely pad with zeros. Next, you are asked to implement a function that calculates the output size of the array after the pooling operation. Well, for this function, I use the formula to calculate the output of a pooling layer we previously discovered. I used the output of this function to initialize an input array filled with zeros.

Finally, I looped over the two spatial dimensions to calculate the max value. You should not calculate the max value over the first dimension, which is the batch-size or the last one, which is the number of channels. With this, you should now have a good understanding of the pooling operation. When I learned about ConvNet for the first time, I reimplemented myself most of the layers to get a better understanding of the underlying mechanism. This is a great exercise and I would definitely recommend you to do it.

## Additional Content

## Solution: Pooling Layers
```python
import argparse

import numpy as np

from utils import check_output


def get_paddings(array, pool_size, pool_stride):
    """ 
    get padding sizes 
    args:
    - array [array]: input np array NxwxHxC
    - pool_size [int]: window size
    - pool_stride [int]: stride
    returns:
    - paddings [list[list]]: paddings in np.pad format
    """
    _, w, h, _ = array.shape
    wpad = (w // pool_stride) * pool_stride + pool_size - w
    hpad = (h // pool_stride) * pool_stride + pool_size - h
    return [[0, 0], [0, wpad], [0, hpad], [0, 0]]


def get_output_size(shape, pool_size, pool_stride):
    """ 
    given input shape, pooling window and stride, output shape 
    args:
    - shape [list]: input shape
    - pool_size [int]: window size
    - pool_stride [int]: stride
    returns
    - output_shape [list]: output array shape
    """
    w = shape[1]
    h = shape[2]
    new_w = (w - pool_size) / pool_stride + 1
    new_h = (h - pool_size) / pool_stride + 1
    return [shape[0], int(new_w), int(new_h), shape[3]]


if __name__ == '__main__':
    parser = argparse.ArgumentParser(description='Download and process tf files')
    parser.add_argument('-f', '--pool_size', required=True, type=int, default=3,
                        help='pool filter size')
    parser.add_argument('-s', '--stride', required=True, type=int, default=3,
                        help='stride size')
    args = parser.parse_args()   

    input_array = np.random.rand(1, 224, 224, 16)
    pool_size = args.pool_size
    pool_stride = args.stride

    # padd the input layer
    paddings = get_paddings(input_array, pool_size, pool_stride)
    padded = np.pad(input_array, paddings, mode='constant', constant_values=0)

    # get output size
    output_size = get_output_size(padded.shape, pool_size, pool_stride)
    output = np.zeros(output_size)

    idx = 0
    for i in range(0, input_array.shape[1], pool_stride):
        jdx = 0
        for j in range(0, input_array.shape[2], pool_stride):
            local = padded[:, i: i + pool_stride, j: j + pool_stride, :]
            local_max = np.max(local, axis=(1, 2))
            output[:, idx, jdx, :] = local_max
            jdx += 1
        idx += 1
    check_output(output)
```
## Extra Resources
- [Pooling layers for CNN](https://machinelearningmastery.com/pooling-layers-for-convolutional-neural-networks/)
