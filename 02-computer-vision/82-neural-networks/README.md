# Neural Networks

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=DQx3WJewb58)

## Summary

**Neural Networks and Logistic Regression**
=====================================

This project introduces the concept of neural networks, which are a type of machine learning model that can learn complex patterns in data. We'll start by reviewing logistic regression for multiple classes and then move on to building our first neural network.

**Key Concepts**
---------------

* **Logistic Regression Limitations**: Logistic regression has limitations due to its linearity and the number of parameters required.
* **Neural Networks**: A neural network is an algorithm made up of several linear layers, followed by non-linear activations. This allows for more complex modeling of data.
* **Feed Forward Neural Network**: A feed forward neural network is a type of neural network where each layer is connected to the previous and next layers in a directed acyclic graph (DAG).
* **Neurons**: Neurons perform linear operations similar to linear regression, but with multiple inputs and outputs.
* **Activation Functions**: Activation functions take the output of a neuron and decide whether it should "fire" or not. They must be differentiable and non-linear.
* **Sigmoid Activation Function**: The Sigmoid activation function is defined as `exp(x) / (1 + exp(x))`. It bounds the outputs of a neuron to be between 0 and 1, but has issues with saturation for low and high values of x.
* **ReLU Activation Function**: The ReLU activation function is defined as `max(0, x)`. It's differentiable except at zero and non-linear, making it a popular choice. However, it can lead to the "dying ReLU" problem if not used carefully.

**Practical Notes**
------------------

* When building neural networks, it's essential to use activation functions that are both differentiable and non-linear.
* The Sigmoid activation function has issues with saturation for low and high values of x, making it less desirable in some cases.
* The ReLU activation function is a popular choice due to its simplicity and effectiveness, but requires careful consideration to avoid the "dying ReLU" problem.

**Code Patterns**
----------------

```python
import numpy as np

# Define a neural network with one hidden layer
def neural_network(x):
    # First layer: linear transformation
    z = np.dot(W1, x) + b1
    
    # Activation function (ReLU)
    a = np.maximum(0, z)
    
    # Second layer: linear transformation
    z2 = np.dot(W2, a) + b2
    
    # Output layer: softmax activation
    y = np.exp(z2) / np.sum(np.exp(z2))
    
    return y

# Define the weights and biases for each layer
W1 = np.random.rand(5, 6)
b1 = np.zeros((5,))
W2 = np.random.rand(3, 5)
b2 = np.zeros((3,))
```

Note: This is a simplified example of a neural network implementation. In practice, you would need to handle more complex cases and use libraries like TensorFlow or PyTorch for efficient computation.

## Transcript

Before we start studying neural networks, let's backtrack a little bit and review logistic regression. In logistic regression for multiple classes, we have an input such as a traffic sign that's being transformed by the set of weight and fed into an activation function like softmax. What are the limitations of such an approach? Well, one of the main limitations of logistic regression is the linearity and the number of parameters. Logistic regression may be sufficient for a lot of machine learning problems, but some data set require models with more parameters simply because of the complexity.

Moreover, in logistic regression, we made the assumption that the probability of an input belonging to a certain class is linear, which is a pretty strong assumption. Let's now consider this; Instead of a single set of weights, we will add multiples, we will call this set layers. After each layer, we will add an activation function to add some nonlinearity and increase the ability of our algorithm to model complex signals. We will still use the softmax activation for the last activation. Well, this is your first neural network.

We created an algorithm made of several linear layers, followed by non-linear activations. By the way, any layer that is not the input or the output is called a hidden layer. A network made of linear layers and activation functions only is called a feed forward neural network. What is happening in these layers exactly? Where each layer is made of neurons.

Neurons will simply perform a linear operation similar to a linear regression, for example. Because we are consuming feed forward neural network, each neuron in the layer is connected to each neuron in the previous layer. Let's assume that the previous layer has five neurons, as shown here. What it means that in our linear equation, x is a vector of five elements. The coefficient w or weights will also be a vector of five elements.

The bias will be a vector of one element. We can repeat this operation for each of the five neurons in the second layer. In total, we will have 25 weights and five biases for this layer. We can repeat this operation for each of the five neurons in the second layer. In total, we have 25 weights and five biases for this layer.

Well, we could write this layer as a matrix operation, where x is the vector of outputs of the first layer, b is a vector of biases, and w_0 is the matrix of weights. If you've followed me so far, both x and b are vectors of five elements. While w_0 here is simply a matrix of dimension five-by-five, because we have five neurons in the first layer and five neurons in the second layer. There's one more thing we should mention. We can use the bias trick to simplify this calculation.

We can add one element to the vector x equal to one, and we can merge the bias parameter in the w matrix. Now, x is a vector of six elements and w is a five by six matrix. You will find more examples of such calculation in the text below. In the following slide, we will learn about the different type of activation function you can find in a neural network. Let's now talk about activation functions.

Activation function take the output of a neuron and decide whether this neuron is going to fire or not. If this neuron is calculating a feature that is relevant to our classification problem, it should fire otherwise, it shouldn't. This firing or activation, depends on the activation function that we use. Because we will be using algorithm like gradient descent to update the weights of a neural network, we want our activation function to be differentiables. Finally, we want our activation function to be non-linear.

Indeed, if we use a linear activation function, we are losing the purpose of stacking layers of neurons. We will just create a fully linear neural network which could be modeled by a single layer. Let's see some activation function in the next slides. When studying logistic regression, we already learned about one activation function, the Sigmoid. As a quick reminder, the Sigmoid is defined as exponential of x divided by 1 plus exponential of x.

The Sigmoid bounds the outputs of a neuron to be between zero and one. These bonding property is great because it will limit the value an output of a neuron can take therefore, avoiding that the output of a neural network, reaches really high values, which could create a problem for the optimizer. This function, has a steep slope between x equal minus 2 and x equal 2. Meaning that small changes of x in this region will lead to significant changes in y. We would get high values for the gradient in this region, and it will have the algorithm to quickly decide if this neuron should fire or not.

One issue with the Sigmoid activation however, is its behavior for low and high values of x. In these regions, the gradient of the Sigmoid will be very small. This could lead to issues when the gradient decent algorithm is used, as the updates of the model weights, depends on the value of the gradient. We say that the Sigmoid saturates for higher and lower values of x. We're going to see another activation function in the next slide.

Let's now learn about another activation function, the rectified linear unit, or ReLU. The ReLU activation, is defined as the maximum between zero and x. When x is negative, this function will output zero, and when x is positive, it will act as a linear function in x. This function is differentiable except in zero, and nonlinear, fitting the requirements of a good activation function. We said that ReLU is a spouse activation function, because it deactivates neuron outputting negative values.

Because ReLU behaves like a linear activation when x is positive, it does not have the saturation property of Sigmoid. However, this property makes ReLU unbonded, which could lead to very high values in our network. The behavior of ReLU for negative values of x is another issue, because it can lead to the dying ReLU problem. It is possible that the gradient of a ReLU unit becomes zero, which would permanently deactivate the neuron. Indeed, in this case, the gradient descent algorithm will not perform any updates and the neuron weights will not be updated anymore during training.

To avoid a dying ReLU problem, we can use the Leaky ReLU activation function. This activation function also behave linearly for negative value of x, but the slope coefficient is usually very small. By doing so, we are not fully deactivating the neuron, and we are giving the neuron the opportunity to be reactivated later during training. Other activation function, such as the hyperbolic tangent, exists. In practice however, the ReLU activation function is still one of the most popular.

Now that we have learned about the different components of a neural network, let's get a better understanding of the weight updating mechanism.

## Additional Content

## Neural Networks
**Feed Forward neural networks (FFNN)** are an extension of the logistic regression algorithm. We can think of logistic regression as a FFNN with a single layer. FFNN are stacking multiple **hidden layers** (any layers that's not the input or output layer) followed by non linear activation, such as the sigmoid or softmax activations. 

FFNN are only made of **fully connected** layers, where each neuron in one layer is connected to all the neurons in the previous layer.
Let's consider a neuron in a layer of a FFNN, containing `n` neurons. The previous layer has `m` neurons. 

This neuron performs a linear operation `wX+b` using the outputs of the previous layer, meaning that `X` is a `mx1` vector. Instead of looping through each one of the `n` neurons, we can use a matrix multiplication to perform all the operations at once. The output of this layer will be obtained by calculating `WX+B` where `B` is the `nx1` vector of biases and `W` is the `nxm` matrix of weights.

To simplify even further, we can incorporate the bias vector `B` in the matrix `W` such that `W` is now of dimensions `nx(m+1)`. We simply need to create a new input vector X of dimensions `(m+1)x1`, where `X[m+1]=1` to get the same result as above.
### Activation Functions
**Activation functions** play a critical role in neural networks because they add non-linearity to the system. The most common activation function is the **ReLU** activation function, but other activation functions like sigmoid or the hyperbolic tangent are also popular.
