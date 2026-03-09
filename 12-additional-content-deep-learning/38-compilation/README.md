# Compilation

> Part of: **Inference Performance**

## Additional Content

Here’s one way we might run the inference on a single image from the command line:

```sh
python inference.py img1.jpg
```

`inference.py` is a Python program running inference on a TensorFlow graph.

Simplifying a little, the key steps are:

- The operating system starts a Python interpreter
- The interpreter runs the inference.py script
- TensorFlow runtime is started through the Python API.
- TensorFlow loads a saved model graph and weights.
- Start a TensorFlow Session.
- Perform inference on img1.jpg.
- Inference results are returned.

Notice most of the steps have nothing to do with the performing inference on `img1.jpg`. 

A possible improvement is to run a loop that performs inference once an image is received. This way we don’t start the interpreter, load the model, and setup the TensorFlow runtime for every image. The general idea is to reduce overhead as much as possible.

Imagine if, instead of loading Python and TensorFlow runtime, we just used a binary.  A binary is an executable list of machine instructions.  A binary doesn’t use the Python interpreter or TensorFlow runtime. It’s simply data in, Inference data out. The problem, of course, is that compiling the model down to a binary is very difficult. In fact, all of these optimizations are difficult to implement!  Fortunately, many of these are already implemented for us by TensorFlow.
