# FCN-8 - Classification & Loss

> Part of: **Scene Understanding**

## Additional Content

The final step is to define a loss. That way, we can approach training a FCN just like we would approach training a normal classification CNN. 
 
In the case of a FCN, the goal is to assign each pixel to the appropriate class. We already happen to know a great loss function for this setup, cross entropy loss!
Remember the output tensor is 4D so we have to reshape it to 2D:
 
```python
...
logits = tf.reshape(input, (-1, num_classes))
```
`logits` is now a 2D tensor where each row represents a pixel and each column a class. From here we can just use standard cross entropy loss:
 
```
cross_entropy_loss = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(logits, labels))
```
 
That’s it, we now have an end-to-end model for semantic segmentation. Time to get training!
