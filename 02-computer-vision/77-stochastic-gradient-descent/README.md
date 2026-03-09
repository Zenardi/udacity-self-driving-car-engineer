# Stochastic Gradient Descent

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=BAfnbGCa13Y)

## Summary

**Batch Gradient Descent and Stochastic Gradient Descent**
===========================================================

This README file summarizes the key concepts of batch gradient descent and stochastic gradient descent, two methods used to update weights in machine learning algorithms.

### Key Concepts
* **Gradient Descent**: A method for minimizing loss functions by iteratively updating model parameters.
* **Batch Gradient Descent**: An optimization technique that calculates the average loss for a set of observations (a "batch") before updating the model's weights. This approach overcomes hardware limitations, but requires careful data loading to avoid bias.
* **Stochastic Gradient Descent**: A variant of batch gradient descent where the batch size is 1 observation. However, in modern machine learning, the term stochastic gradient descent refers to batch gradient descent for any batch size.
* **Data Loading Methods**: Critical when using batch gradient descent. Observations should be shuffled randomly instead of being ordered by class.

### Practical Notes
When implementing batch gradient descent or stochastic gradient descent, consider the following:

* Use a suitable batch size (e.g., 32 or 64) to balance computation speed and accuracy.
* Ensure that data is loaded in a way that avoids bias. Shuffling observations randomly is essential.
* In deep learning frameworks like TensorFlow, stochastic gradient descent is often referred to as an optimizer.

Note: This summary focuses on the key concepts and practical considerations introduced in the lesson. For more information on implementing batch gradient descent or stochastic gradient descent, refer to the Udacity course materials.

## Transcript

In the previous videos, we learned about gradient descent. Ideally, we would like to compute the derivative of the loss function for every single observation in the training set before updating the weights of our algorithm. However, we are often constrained by hardware limitations. Instead, we will use batches of observations. For example, we will calculate the average loss for set of 32 or 64 observation and use it to update the weights using gradient descent.

This is what we call batch gradient descent. This method overcome the hardware limitations, but it can be dangerous if the right data loadings method are not being used. For example, it is critical to shuffle the observations instead of having them ordered by class before using batch gradient descent. Machine learning engineer refer to batch gradient descent as stochastic gradient descent, which is technically gradient descents for batch size of one. However, the term stochastic gradient descent is now used to describe batch gradient descent for any batch sizes.

In deep learning framework such as TensorFlow, stochastic gradient descent is called an optimizer. In the following slide, we will learn about other optimizers.

## Additional Content

## Stochastic Gradient Descent
Because of memory limitations, the entire dataset is almost never loaded at once and fed through the model, as is the case in **batch gradient descent**. Instead, **batches** of inputs are created. Gradient descent performed on batches of just one input at a time is called **stochastic gradient descent (SGD)**, while batches of more than one, but not all at once (e.g. 20 batches of 200 images each), are called **mini-batch** gradient descent.
