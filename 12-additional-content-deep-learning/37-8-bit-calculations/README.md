# 8-bit Calculations

> Part of: **Inference Performance**

## Additional Content

We’ve covered freezing the graph and optimizing for inference, but we haven’t yet covered quantization. So the next optimization we’ll discuss is converting the graph to perform 8-bit calculations. Here’s an example using the `transform_graph` tool:

```sh
~/tensorflow/bazel-bin/tensorflow/tools/graph_transforms/transform_graph \
--in_graph=frozen_graph.pb \
--out_graph=eightbit_graph.pb \
--inputs=image_input \
--outputs=Softmax \
--transforms='
add_default_attributes
remove_nodes(op=Identity, op=CheckNumerics)
fold_constants(ignore_errors=true)
fold_batch_norms
fold_old_batch_norms
fuse_resize_and_conv
quantize_weights
quantize_nodes
strip_unused_nodes
sort_by_execution_order'
```

There’s a lot going on here, which you can find more information in the [TensorFlow Graph Transforms documentation](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/graph_transforms/README.md). 

The gist is that `fold` transforms look for subgraphs that always evaluate to to the same result. Then they consolidate each such subgraph into one `Constant` node. 

`quantize_weights` quantizes values larger than 15 bits. It also adds nodes to convert back to floating point. The `quantize_weights` transform is mainly for reducing graph size. For the desired quantization computation behaviour we’ll need to use `quantize_nodes` as well.

Ok, let’s take a look:

```python
from graph_utils import load_graph

sess, eightbit_ops = load_graph('eightbit_graph.pb')
print(len(eightbit_ops)) # 425
```

There are 425 operations, that’s more than the original frozen graph! Quantization computation requires extra nodes in general so it’s not a big deal. Nodes that have no quantization equivalent are keep as floating point.
