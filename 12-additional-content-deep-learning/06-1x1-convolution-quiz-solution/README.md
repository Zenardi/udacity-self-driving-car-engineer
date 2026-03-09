# 1x1 Convolution Quiz Solution

> Part of: **Fully Convolutional Networks**

## Additional Content

The correct way to create a 1x1 convolutional layer is `tf.layers.conv2d(x, num_outputs, 1, 1, weights_initializer=custom_init)`. 

* `num_outputs` defines the number of output channels or kernels
* The third argument is the `kernel_size`, which is set to **1**.
* The fourth argument is the `stride`, which is set to **1**.
* We use the custom initializer so the weights in the dense and convolutional layers are identical.

This results in a matrix multiplication operation that preserves spatial information.
