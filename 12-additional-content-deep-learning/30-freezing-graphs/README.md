# Freezing Graphs

> Part of: **Inference Performance**

## Additional Content

Prior to applying any optimizations we'll want to freeze the TensorFlow Graph such that it's self-contained in a single [protobuf](https://developers.google.com/protocol-buffers/) file. Freezing the graph is the process of converting TensorFlow variables into constants. During inference, variables become unnecessary since the values they store don’t change. We might as well convert them to constants, which the computer can work with faster.

Additional benefits of freezing the graph are:
- Unnecessary nodes related to training are removed
- The model can be contained entirely in one protobuf file (weights and graph definition)
- Simpler graph structure
- Easier to deploy (due to everything being in one file)

For these reasons, freezing the graph is commonly the first transform engineers execute when optimizing their network for inference.

We’ll use a trained fully convolutional model as the practical example.

### Setup

In the AMI navigate to the directory containing the saved graph checkpoint:

```sh
cd /home/ubuntu/inference-walkthrough/src
```

The current directory should contain the following files:

```
base_graph.pb 
checkpoint
ckpt.data-00000-of-0000
ckpt.index
ckpt.meta
graph_utils.py
```

* `base_graph.pb` is a protobuf representation of the graph. Note this does not include weight values, just the structure.
* `checkpoint` and `ckpt.*` files pertain to the saved weights and associated metadata.
* `graph_utils.py` is a Python file containing utility functions for working with the above files and TF graphs.

### Freezing The Graph

Here’s an example of the freeze graph tool:

```sh
~/tensorflow/bazel-bin/tensorflow/python/tools/freeze_graph \
--input_graph=base_graph.pb \
--input_checkpoint=ckpt \
--input_binary=true \
--output_graph=frozen_graph.pb \
--output_node_names=Softmax

```

The `freeze_graph` command requires five inputs:
- The input graph `input_graph` saved in protobuf format.
- The input graph checkpoint, `input_checkpoint`.
- `input_binary` denotes whether the input graph is a binary file. Set this to true if the input is a `.pb` file instead of `.pbtxt`.
- The name of the output graph, `output_graph`, i.e. the frozen graph.
- The names of the output nodes. It’s a good idea in general to name key nodes in the graph and these names will come in handy when using these tools as well.

The result is saved in the `frozen_graph.pb` file. This ends up removing many extraneous operations from the graph. We can get all a graph’s operations with `.get_operations()` method. The `load_graph` method below takes a binary protobuf file as input and returns the graph and list of operations.

```python
def load_graph(graph_file, use_xla=False):
    jit_level = 0
    config = tf.ConfigProto()
    if use_xla:
        jit_level = tf.OptimizerOptions.ON_1
        config.graph_options.optimizer_options.global_jit_level = jit_level

    with tf.Session(graph=tf.Graph(), config=config) as sess:
        gd = tf.GraphDef()
        with tf.gfile.Open(graph_file, 'rb') as f:
            data = f.read()
            gd.ParseFromString(data)
        tf.import_graph_def(gd, name='')
        ops = sess.graph.get_operations()
        n_ops = len(ops)
        return sess.graph, ops

```

```python
from graph_utils import load_graph

sess, base_ops = load_graph('base_graph.pb')
print(len(base_ops)) # 2165
sess, frozen_ops = load_graph('frozen_graph.pb')
print(len(frozen_ops)) # 245
```

As you can see, just freezing the graph substantially reduces the number of operations.
