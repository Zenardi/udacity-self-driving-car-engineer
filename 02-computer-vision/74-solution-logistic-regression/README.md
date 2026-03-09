# Solution: Logistic Regression

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=5rOMtMWyDT0)

## Summary

**Softmax Function and Logistic Regression Model Implementation**
===========================================================

This project involves implementing the softmax function and a logistic regression model in TensorFlow. The goal is to understand how to use various TensorFlow functions, such as `tf.boolean_mask`, `tf.log`, `tf.reshape`, and `tf.matmul`, to build a machine learning model.

**Key Concepts**
---------------

* **Softmax Function**: A mathematical function that takes the output of a neural network and normalizes it into probabilities.
* **TensorFlow Math Functions**: Various functions in TensorFlow, such as `tf.boolean_mask` and `tf.log`, used for mathematical operations on tensors.
* **Matrix Product**: The result of multiplying two matrices using the `tf.matmul` function.
* **Logistic Regression Model**: A type of machine learning model that uses a sigmoid function to predict probabilities.

**Practical Notes**
------------------

To implement the softmax function and logistic regression model, you will need to:

* Use the `tf.boolean_mask` function to match logits with labels
* Calculate the logarithm using the `tf.log` function
* Reshape input data using the `tf.reshape` function
* Calculate matrix products between inputs and weights using the `tf.matmul` function
* Apply a softmax function to get output probabilities
* Use the `tf.argmax` function to find the index of the highest probability
* Cast tensors from one type to another using the `tf.cast` function

Note: The `tf.cast` function is used in the next exercise to train a logistic regression algorithm.

## Transcript

By leveraging the TensorFlow exponential function, as well as the TensorFlow math reduce sum function. You can implement the softmax in a few lines, as you can see here. Then you are asked to implement the cross-entropy loss. We can use the tf.boolean_mask function to match the logits and the tf.log function to calculate the logarithm. You were then asked to implement the logistic regression model.

However, we added an extra constraint where the input x is an RGB image. First, you had to reshape this input by using the tf.reshape function. Then you can use the tf.matmul function to calculate the matrix product between the inputs and the weights. Finally, we use a softmax function to get the outputs. The last function to implement was the accuracy.

First, you had to use the tf.argmax function to find the index of the highest probability. To use the comparison operator, you need to be sure that the tensors have the same data type. The last function to implement was the accuracy. We use the tf.argmax function to find the index of the highest probability. To use the comparison operator, you need to be sure that the tensor have the same data type.

We use tf.cast to cast the tensor from one type to another. In the next exercise, you will be using this free function to train a logistic regression algorithm.

## Additional Content

## Solution: Logistic Regression
```python
import tensorflow as tf

from utils import check_softmax, check_acc, check_model, check_ce


def softmax(logits):
    """
    softmax implementation
    args:
    - logits [tensor]: 1xN logits tensor
    returns:
    - soft_logits [tensor]: softmax of logits
    """
    exp = tf.exp(logits)
    denom = tf.math.reduce_sum(exp, 1, keepdims=True)
    return exp / denom


def cross_entropy(scaled_logits, one_hot):
    """
    Cross entropy loss implementation
    args:
    - scaled_logits [tensor]: NxC tensor where N batch size / C number of classes
    - one_hot [tensor]: one hot tensor
    returns:
    - loss [tensor]: cross entropy 
    """
    masked_logits = tf.boolean_mask(scaled_logits, one_hot) 
    return -tf.math.log(masked_logits)


def model(X, W, b):
    """
    logistic regression model
    args:
    - X [tensor]: input HxWx3
    - W [tensor]: weights
    - b [tensor]: bias
    returns:
    - output [tensor]
    """
    flatten_X = tf.reshape(X, (-1, W.shape[0]))
    return softmax(tf.matmul(flatten_X, W) + b)


def accuracy(y_hat, Y):
    """
    calculate accuracy
    args:
    - y_hat [tensor]: NxC tensor of models predictions
    - y [tensor]: N tensor of ground truth classes
    returns:
    - acc [tensor]: accuracy
    """
    # calculate argmax
    argmax = tf.cast(tf.argmax(y_hat, axis=1), Y.dtype)

    # calculate acc
    acc = tf.math.reduce_sum(tf.cast(argmax == Y, tf.int32)) / Y.shape[0]
    return acc


if __name__ == '__main__':
    # checking the softmax implementation
    check_softmax(softmax)

    # checking the NLL implementation
    check_ce(cross_entropy)

    # check the model implementation
    check_model(model)

    # check the accuracy implementation
    check_acc(accuracy)
```
