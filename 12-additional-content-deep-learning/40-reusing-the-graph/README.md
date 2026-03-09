# Reusing The Graph

> Part of: **Inference Performance**

## Additional Content

So once we’ve optimized the graph and saved it to a file how do we use it?

First load the graph from the binary protobuf file:

```python
from graph_utils import load_graph

sess, _ = load_graph(‘your_graph.pb’)
graph = sess.graph
```

Once the graph is loaded we can access operations and tensors with the `get_operation_by_name` and `get_tensor_by_name` `tf.Graph` methods respectively. We could also retrieve all the operations with of a `tf.Graph` with the `get_operations` method, which is very useful if we are unsure which operation to use. In this case we want to pass an image as input and receive the softmax probabilities as output:

```python
image_input = graph.get_tensor_by_name('image_input:0')
keep_prob = graph.get_tensor_by_name('keep_prob:0')
softmax = graph.get_tensor_by_name('Softmax:0')
```

Then we can take an image and run the computation in a session as we normally would. `keep_prob` is related to the dropout probability.

```python
probs = sess.run(softmax, {image_input: img, keep_prob: 1.0})
```
