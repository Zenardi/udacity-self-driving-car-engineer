# FCN-8 - Decoder

> Part of: **Scene Understanding**

## Additional Content

To build the decoder portion of FCN-8, we’ll upsample the input to the original image size. The shape of the tensor after the final convolutional transpose layer will be 4-dimensional: (batch_size, original_height, original_width, num_classes).
Let’s implement those transposed convolutions we discussed earlier as follows:
 
```
output = tf.layers.conv2d_transpose(input, num_classes, 4, strides=(2, 2))
```
 
The transpose convolutional layers increase the height and width dimensions of the 4D input Tensor.
## Skip Connections
 
The final step is adding skip connections to the model. In order to do this we’ll combine the output of two layers. The first output is the output of the current layer. The second output is the output of a layer further back in the network, typically a pooling layer.
In the following example we combine the result of the previous layer with the result of the 4th pooling layer through elementwise addition (`tf.add`).
 
```python
# make sure the shapes are the same!
input = tf.add(input, pool_4)
```
 
We can then follow this with another transposed convolution layer.
 
```python
input = tf.layers.conv2d_transpose(input, num_classes, 4, strides=(2, 2))
```
 
We’ll repeat this once more with the third pooling layer output.
 
```python
input = tf.add(input, pool_3)
Input = tf.layers.conv2d_transpose(input, num_classes, 16, strides=(8, 8))
```
