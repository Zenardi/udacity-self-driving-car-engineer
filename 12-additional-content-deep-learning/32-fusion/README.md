# Fusion

> Part of: **Inference Performance**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=JOksFH3vQgk)

## Summary

**Graph Operations Fusion**
=====================================

This project demonstrates the concept of fusing graph operations to reduce the number of operations and accelerate data passing through the graph. By combining multiple operations into a single kernel, we can save memory and time.

### Key Concepts
* **Fusion**: Combining multiple graph operations into a single operation to reduce overhead and improve performance.
* **Temporary tensors**: Intermediate results stored in memory during graph operations.
* **Kernel execution**: The process of executing a kernel on the GPU, which incurs an overhead each time it is called.
* **Flexibility trade-off**: Fusing operations reduces flexibility in network architecture, but is beneficial for inference where the architecture is fixed.

### Practical Notes
To implement fusion manually, we can write a single kernel that performs multiple fuse operations together. However, this approach can lead to complex and hard-to-understand code. Instead, we can use an optimizer to automate the fusion process, allowing us to write easier-to-understand code while still reaping performance benefits.

Example code:
```python
# Manually fusing three operations together
def fused_kernel(x, y, z):
    # Perform batch normalization on x
    x = tf.nn.batch_normalization(x)
    
    # Feed into value function
    x = tf.value(x)
    
    # Feed into convolution function
    x = tf.conv2d(x, kernel_size=3)
    
    return x

# Using an optimizer to automate fusion
optimizer = tf.keras.optimizers.Adam()
model.compile(optimizer=optimizer)
```
Note: The code examples are simplified and not actual implementation details.

## Transcript

<v English>So, what are we fusing?</v> <v English>We're fusing graph operations.</v> <v English>This fusion reduces the number of operations</v> <v English>and accelerates the data passing through the graph.</v> <v English>Consider a three layer pipeline: batch normalization,</v> <v English>feeding into a value,</v> <v English>feeding into a convolution.</v> <v English>This implementations require each layer to store temporary tensors.</v> <v English>We can fuse all three operations together and avoid storing all these extra tensors.</v> <v English>Even better, the fuse operation only execute one kernel on the GPU instead of three.</v> <v English>Each time a kernel is called, there is an overhead.</v> <v English>Fusing kernels therefore, limits the overhead so the overall applications runs faster.</v> <v English>Fusing saves both memory and time.</v> <v English>Of course, fusing could be beneficial in training as well as inference.</v> <v English>The trade off is that fusing reduces the flexibility of the network.</v> <v English>During training, we might want to preserve the flexibility of the model in case</v> <v English>we want to add or remove layers or transfer part of the network.</v> <v English>By the time we get to inference,</v> <v English>we're no longer changing the network architecture,</v> <v English>so we can fuse operations more aggressively.</v> <v English>It's important to know we could do this manually by coding up</v> <v English>a single kernel that performs the three fuse operations together.</v> <v English>However, the compiler is capable of doing this on its own,</v> <v English>allowing us to write understandable code and still reap performance benefits.</v> <v English>We can automate this process using an optimizer that will fuse common layers together.</v> <v English>This allow us to write easier to understand code and manipulate it,</v> <v English>while the final version after the optimization,</v> <v English>we'll have all the performance advantages by applying tricks like fusion automatically.</v>
