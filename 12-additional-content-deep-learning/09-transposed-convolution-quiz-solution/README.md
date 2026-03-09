# Transposed Convolution Quiz Solution

> Part of: **Fully Convolutional Networks**

## Additional Content

```python
kernel_size = (2,2)
stride = (2,2)
conv = tf.layers.conv2d_transpose(
    x, num_outputs, kernel_size, stride, weights_initializer=custom_init
)
```

* The first argument `x` is the input data.
* The second argument `num_outputs` is the number of kernels/output channels.
* The third argument is the kernel size, `(2, 2)`. Note that the kernel size could also be `(1, 1)` and the output shape would be the same. However, if it were changed to `(3, 3)` note the shape would be `(9, 9)`, at least with `'VALID'` padding.
* The fourth argument, the number of strides, is how we get from a height and width from `(4, 4)` to `(8, 8)`. If this were a regular convolution the output height and width would be `(2, 2)`.
* The final argument is a custom initializer to ensure consistent results in the quiz environment.
Now that you've learned how to use transposed convolution, let's learn about the third technique in FCNs.
