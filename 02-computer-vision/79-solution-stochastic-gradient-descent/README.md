# Solution: Stochastic Gradient Descent

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=PS14eHk9M94)

## Summary

**Training Machine Learning Algorithms with Stochastic Gradient Descent**
====================================================================

This lesson covers the basics of implementing a training loop for machine learning algorithms using stochastic gradient descent (SGD) optimization. The key concepts and techniques introduced in this lesson are essential for building and training neural networks.

### Key Concepts
* **Stochastic Gradient Descent (SGD)**: A popular optimization algorithm used to update model parameters during training.
	+ SGD takes as inputs the model parameters, gradients, learning rate, and batch size.
	+ The gradient is scaled by the learning rate and divided by the batch size to prevent overfitting.
* **tf.GradientTape API**: A TensorFlow API for calculating gradients of a loss function with respect to model weights.
	+ Creates a context for calculating gradients using tape.gradient.
* **Cross Entropy Loss**: A common loss function used in classification tasks, calculated using tf.one_hot and cross entropy.
* **Model Updates**: Weights are updated using the SGD optimizer and gradients calculated using tf.GradientTape.

### Practical Notes
To implement the training loop:

1. Use `tf.GradientTape` to create a context for calculating gradients.
2. Normalize input data `x` and feed it into the model.
3. Calculate cross entropy loss using `tf.one_hot`.
4. Use `tape.gradient` to calculate gradients of the loss with respect to model weights.
5. Update weights using the SGD optimizer.

Note: In later exercises, you will simplify this implementation by leveraging the TensorFlow Keras API.

## Transcript

In this exercise, you were asked to implement your first training loop and you trained your first machine learning algorithm. The first function you had to implement was the stochastic gradient descent optimizer. This function takes as inputs the model parameters and the calculated gradients, as well as the learning rate and the batch size. We use the assigned sub method of a TensorFlow variable to subtract the gradient scale by the learning rate. We also divide by the batch size to be sure that the amplitude of the gradient is not dependent on the batch size.

For the training loop, we use the tf.GradientTape API to create a context where we can calculate the gradients. We normalize the input x and feed them into the model. We create the one_hot vector using the tf.one_hot and calculate the cross entropy loss. As we have seen previously, we use tape.gradient to calculate the gradients of the loss with respect to the models' weights. We use these gradients and our implementation of SGD to update the weights.

We keep track of the training accuracy by calculating it for each training batch. Finally, we use tf.mass.reduce_mean to calculate the mean loss and the mean accuracy. The validation loop is much simpler because it does not require any updating of the weight. Therefore, we do not need to use the tf.GradientTape API. We only use the model's predictions to calculate the accuracy.

In later exercises, you will greatly simplify this implementation by leveraging the TensorFlow Keras API

## Additional Content

## Solution: Stochastic Gradient Descent
```python
import argparse
import logging

import tensorflow as tf

from dataset import get_datasets
from logistic import softmax, cross_entropy, accuracy
    
    
def sgd(params, grads, lr, bs):
    """
    stochastic gradient descent implementation
    args:
    - params [list[tensor]]: model params
    - grad [list[tensor]]: param gradient
    - lr [float]: learning rate
    - bs [int]: batch_size
    """
    for param, grad in zip(params, grads):
        param.assign_sub(lr * grad / bs)


def training_loop(lr):
    """
    training loop
    args:
    - lr [float]: learning rate
    returns:
    - mean_acc [tensor]: training accuracy
    - mean_loss [tensor]: training loss
    """
    accuracies = []
    losses = []
    for X, Y in train_dataset:
        with tf.GradientTape() as tape:
            # forward pass
            X = X / 255.0
            y_hat = model(X)
            # calculate loss
            one_hot = tf.one_hot(Y, 43)
            loss = cross_entropy(y_hat, one_hot)
            losses.append(tf.math.reduce_mean(loss))

            grads = tape.gradient(loss, [W, b])
            sgd([W, b], grads, lr, X.shape[0]) 

            acc = accuracy(y_hat, Y)
            accuracies.append(acc)
    mean_acc = tf.math.reduce_mean(tf.concat(accuracies, axis=0))
    mean_loss = tf.math.reduce_mean(losses)
    return mean_loss, mean_acc

def model(X):
    """
    logistic regression model
    """
    flatten_X = tf.reshape(X, (-1, W.shape[0]))
    return softmax(tf.matmul(flatten_X, W) + b)

    
def validation_loop():
    """
    loop through the validation dataset
    """
    accuracies = []
    for X, Y in val_dataset:
        X = X / 255.0
        y_hat = model(X)
        acc = accuracy(y_hat, Y)
        accuracies.append(acc)
    mean_acc = tf.math.reduce_mean(tf.concat(accuracies, axis=0))
    return mean_acc


def get_module_logger(mod_name):
    logger = logging.getLogger(mod_name)
    handler = logging.StreamHandler()
    formatter = logging.Formatter('%(asctime)s %(levelname)-8s %(message)s')
    handler.setFormatter(formatter)
    logger.addHandler(handler)
    logger.setLevel(logging.DEBUG)
    return logger


if __name__  == '__main__':
    logger = get_module_logger(__name__)
    parser = argparse.ArgumentParser(description='Download and process tf files')
    parser.add_argument('--imdir', required=True, type=str,
                        help='data directory')
    parser.add_argument('--epochs', default=10, type=int,
                        help='Number of epochs')
    args = parser.parse_args()    

    logger.info(f'Training for {args.epochs} epochs using {args.imdir} data')
    # get the datasets
    train_dataset, val_dataset = get_datasets(args.imdir)

    # set the variables
    num_inputs = 1024*3
    num_outputs = 43
    W = tf.Variable(tf.random.normal(shape=(num_inputs, num_outputs),
                                    mean=0, stddev=0.01))
    b = tf.Variable(tf.zeros(num_outputs))
    
    lr = 0.1
    # training! 
    for epoch in range(args.epochs):
        logger.info(f'Epoch {epoch}')
        loss, acc = training_loop(lr)
        logger.info(f'Mean training loss: {loss:1f}, mean training accuracy {acc:1f}')
        val_acc = validation_loop()
        logger.info(f'Mean validation accuracy {val_acc:1f}')
```
