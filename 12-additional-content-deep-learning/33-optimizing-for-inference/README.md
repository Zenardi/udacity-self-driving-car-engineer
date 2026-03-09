# Optimizing For Inference

> Part of: **Inference Performance**

## Additional Content

Once the graph is frozen there are a variety of transformations that can be performed; dependent on what we wish to achieve. TensorFlow has packaged up some inference optimizations in a tool aptly called `optimize_for_inference`. 

`optimize_for_inference` does the following:
- Removes training-specific and debug-specific nodes
- Fuses common operations
- Removes entire sections of the graph that are never reached


Here’s how it can be used:

```bash
~/tensorflow/bazel-bin/tensorflow/python/tools/optimize_for_inference \
--input=frozen_graph.pb \
--output=optimized_graph.pb \
--frozen_graph=True \
--input_names=image_input \
--output_names=Softmax
```

We'll use the graph we just froze as the input graph, `input`. `output` is the name of the output graph; we’ll be creative and call it `optimized_graph.pb`. 

The `optimize_for_inference` tool works for both frozen and unfrozen graphs, so we have to specify whether the graph is already frozen or not with `frozen_graph`. 

`input_names` and `output_names` are the names of the input and output nodes respectively. As the option names suggest, there can be more than one input or output node, separated by commas.

Let’s take a look at the effect this has on the number of operations.

```python
from graph_utils import load_graph

sess, optimized_ops = load_graph('optimized_graph.pb')
print(len(optimized_ops)) # 200
```

Cool, Now there are only 200 operations in the graph!
