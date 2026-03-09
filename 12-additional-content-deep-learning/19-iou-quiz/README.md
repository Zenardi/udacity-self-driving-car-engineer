# IoU Quiz

> Part of: **Scene Understanding**

## Additional Content

## IoU Calculation Quiz

For the next quiz we will calculate the IOU metric given ground truth and prediction matrices.  Remember IOU is Intersection over Union, where the Intersection set is an AND operation (pixels that are truly part of a class AND are classified as part of the class by the network) and the Union is an OR operation (pixels that are truly part of that class + pixels that are classified as part of that class by the network).
## TensorFlow IoU

Let's look at the

[`tf.metrics.mean_iou`](https://www.tensorflow.org/api_docs/python/tf/metrics/mean_iou)

function.  Like all the other

[TensorFlow metric functions](https://www.tensorflow.org/api_docs/python/tf/metrics)

, it returns a Tensor for the metric result and a Tensor Operation to generate the result.

[In this case](https://www.tensorflow.org/api_docs/python/tf/compat/v1/metrics/mean_iou)

it returns `mean_iou` for the result and `update_op` for the update operation.  Make sure to run `update_op` before getting the result from `mean_iou`.

```python
sess.run(update_op)
sess.run(mean_iou)
```

The other characteristic of

[TensorFlow metric functions](https://www.tensorflow.org/api_docs/python/tf/metrics)

is the usage of

[local TensorFlow variables](https://www.tensorflow.org/api_docs/python/tf/local_variables)

.  These are temporary TensorFlow Variables that must be initialized by running

[`tf.local_variables_initializer()`](https://www.tensorflow.org/api_docs/python/tf/local_variables_initializer)

.  This is similar to

[`tf.global_variables_initializer()`](https://www.tensorflow.org/api_docs/python/tf/global_variables_initializer)

, but for different TensorFlow Variables.

## TensorFlow IoU Quiz

In this quiz, you'll use this

[documentation](https://www.tensorflow.org/api_docs/python/tf/compat/v1/metrics/mean_iou)

to apply mean IoU to an example prediction. In this code, we'll assign `mean_iou` to `iou`, and `update_op` to `iou_op`.
