# Backpropagation

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=20Tuqg4ohKg)

## Summary

**README: Backpropagation and Chain Rule**

This project explores the concept of backpropagation in neural networks, which is a mechanism for updating the weights of neurons based on the gradient of the loss function. The chain rule, a fundamental concept in calculus, is used to calculate the derivative of composite functions.

**Key Concepts**

* **Chain Rule**: A method for calculating the derivative of a composite function by combining the derivatives of individual functions.
	+ Formula: `(df/dg) = (df/dx) * (dg/dx)`
* **Backpropagation**: A mechanism for updating the weights of neurons in a neural network based on the gradient of the loss function.
* **Sigmoid Function**: A mathematical function used to introduce non-linearity into neural networks, defined as `σ(x) = 1 / (1 + e^(-x))`.
* **Derivative of Sigmoid Function**: Using the chain rule, the derivative of the sigmoid function can be calculated as `(dσ/dx) = σ(x) * (1 - σ(x))`.

**Practical Notes**

* The backpropagation mechanism involves two passes: a forward pass to calculate the output of each node, and a backward pass to calculate the local gradient of each node with respect to its input.
* The chain rule is used to calculate the derivative of composite functions, such as the sigmoid function.
* In practice, backpropagation is used in conjunction with an optimizer (such as SGD) to update the weights of neurons in a neural network.

Note: This summary provides a high-level overview of the key concepts and practical notes. For more detailed information, please refer to the original transcript or additional resources.

## Transcript

Let's now dive a little deeper in the optimization problem created when trying to fit a model to a dataset. Remember that SGD and other optimizer use a derivative of the loss function to update the weights of the algorithm. Whereas logistic regression is made of a single layer of weights, neural networks are made of many layers with non-linear activation, we need to have a mechanism to update the weights of the neurons using the gradient of the loss. Such a mechanism is called backpropagation. We are propagating the gradient from the last layer to the first one.

But before we can learn about backpropagation, we need a small calculus reminder of the chain rule. What is the chain rule? The chain rule is a way to calculate the derivative of a composite function. Let's consider two function with the same domain, g and f. The derivative of f of g is equal to the derivative of f, f prime composed with g times the derivative of g, g primes.

Let's use this chain rule to calculate the derivative of the sigmoid function. The sigmoid function can also be written as follow by dividing the numerator and the denominator by exponential of minus x. We can use this definition to calculate the derivative of sigma with respect to x. To do so, we can express sigma as the composite of two functions, f and g. We'll define f as a reciprocal function and g as 1 plus exponential of minus x.

Using the chain rule, we can calculate the derivative of the sigmoid. Because we know that the derivative of the reciprocal function is minus 1 over x squared, the first part of the derivative is minus 1 over 1 plus exponential of minus x squared. We also know the derivative of an exponential function and we can calculate the derivative of one plus exponential of minus x. Bringing everything over the same denominator, we now have the derivative of sigma. I hope this example helped you refresh your knowledge of the chain rule.

Let's now dive in the backpropagation mechanism. Now that we have reviewed the chain rule, we have all the tools to understand backpropagation. First, let's remember the initial problem. How do we calculate the gradient of the loss with respect to each neuron's weights? Well, we're going to use something called backpropagation.

Let's consider the sigmoid function once again as an example. We can express that function as a succession of the following operation. First, we multiply the input by minus one. Then we compose it with the exponential function. We add one to the output and compose everything with the reciprocal function.

This circuit view is the way I learned backpropagation. I find it particularly useful to understand this mechanism. Let's now consider an example. The input of our circuit X0 has a value of two. First of all, we do a forward pass, meaning that we're going to calculate the output of each node of this circuit.

We multiply the input by minus one, feed it in the exponential function, added one, and finally, compose it with the reciprocal function. In a second time, we can backpropagate the gradients, meaning that we are going to calculate the local gradient of each node with respect to its input. In a second time, we can backpropagate the gradient, meaning that we're going to calculate the local gradient of each node. Let's calculate together the first value of the local gradient. The derivative of the reciprocal function is minus one over x square.

The previous gradient value is equal to one. Therefore, the local gradient is equal to minus 1 over 1.14 squared times 1, which is minus 0.77. Let's move it to the next node. While the derivative of this function is one, so the local gradient is 1 times minus 0.77. Let's keep moving on to the next node.

The derivative of exponential x is exponential x. Following the chain rule, the local gradient is exponential of minus 2 times minus 0.77. We can apply this logic one more time to the last node to compute its gradient. Hopefully, this view gives you a good understanding of the backpropagation mechanism. In a neural network, each node would be a layer made of many neurons.

But the main idea behind backpropagation remains the same. We can use these local gradients to update the weights using SGD or another optimizer.

## Additional Content

## Backpropagation
The **chain rule** allows you to decompose the calculation of the derivative of a composite function. Because we can think of an ANN as a giant composite function, the chain rule is at the core of the **backpropagation** algorithm. Backpropagation is the mechanism used to calculate the gradient of the loss with respect to each weight of the neural network.  
### An Example Backpropagation Calculation
The circuit approach is an intuitive way to understand the backpropagation algorithm. Using the chain rule, we can backprogate the gradient from the last node to the first. 

For example, the input to the third node is `-2` and this node applies the exponential function to its input. The output of this node is `exp(-2) = 0.14`. When backpropagating the gradient, we get a value of `-0.77` before this node. Thanks to the chain rule, and because the derivative of the exponential function is the exponential function, we can backpropagate the gradient as follow: `exp(-2) * (-0.77) = -0.10`.
