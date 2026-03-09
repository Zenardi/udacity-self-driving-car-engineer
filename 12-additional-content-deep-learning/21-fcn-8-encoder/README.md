# FCN-8 - Encoder

> Part of: **Scene Understanding**

## Additional Content

Let’s focus on a concrete implementation of a fully convolutional network. We’ll discuss the [FCN-8 architecture](https://people.eecs.berkeley.edu/~jonlong/long_shelhamer_fcn.pdf) developed at Berkeley. In fact, many FCN models are derived from this FCN-8 implementation. The encoder for FCN-8 is the VGG16 model pretrained on ImageNet for classification. The fully-connected layers are replaced by 1-by-1 convolutions. Here’s an example of going from a fully-connected layer to a  1-by-1 convolution in TensorFlow:

```
num_classes = 2
output = tf.layers.dense(input, num_classes)
```
 
To:
 
```
num_classes = 2
output = tf.layers.conv2d(input, num_classes, 1, strides=(1,1))
```
 
The third argument, `1`, is the kernel size, meaning this is a 1 by 1 convolution.
Thus far, we’ve downsampled the input image and extracted features using the VGG16 encoder. We’ve also replaced the linear layers with 1 by 1 convolutional layers, preserving spatial information.
 
But this is just the encoder portion of the network. Next comes the decoder.
