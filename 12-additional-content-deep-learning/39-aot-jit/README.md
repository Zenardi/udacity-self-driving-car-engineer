# AOT & JIT

> Part of: **Inference Performance**

## Additional Content

TensorFlow supports both JIT (just in time) and AOT (ahead of time) compilation. 

AOT compilation is the kind used in a C or C++ program; it compiles the program “ahead” of the actual use. A really cool aspect of AOT compilation is you can potentially create a static binary file, meaning it’s entirely self contained. You can deploy it by simply downloading the file and executing it, without concern for downloading extra software, besides necessary hardware drivers, i.e. for GPU use.

JIT compilation doesn’t compile code until it’s actually run. You can imagine as a piece of code is being interpreted machine instructions are concurrently generated. Nothing will change during the initial interpretation, the JIT might as well not exist. However, on the second and all future uses that piece of code will no longer be interpreted. Instead the compiled machine instructions will be used.

Under the hood AOT and JIT compilation make use of XLA (Accelerated Linear Algebra). XLA is a compiler and runtime for linear algebra. XLA takes a TensorFlow graph and uses [LLVM](http://llvm.org/) to generate machine code instructions. LLVM is itself a compiler which generates machine code from its IR (intermediate representation). So, in a nutshell:

TensorFlow -> XLA -> LLVM IR -> Machine Code

which means TensorFlow can potentially be used on any architecture LLVM generates code for.

Both AOT and JIT compilation are experimental in TensorFlow. However, JIT compilation is fairly straightforward to apply. Note JIT compilation is NOT limited to inference but can be used during training as well.

```python
# Create a TensorFlow configuration object. This will be 
# passed as an argument to the session.
config = tf.ConfigProto()
# JIT level, this can be set to ON_1 or ON_2 
jit_level = tf.OptimizerOptions.ON_1
config.graph_options.optimizer_options.global_jit_level = jit_level
```

That’s it! All that’s left to be done is pass the `config` into the session:

```python
with tf.Session(config=config) as sess:
    …
```
