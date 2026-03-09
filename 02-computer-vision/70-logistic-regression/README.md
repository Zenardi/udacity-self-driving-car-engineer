# Logistic Regression

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=R8XfDeMo2Yk)

## Summary

**Logistic Regression and Multiclass Classification**
=====================================================

This project introduces logistic regression, a machine learning algorithm used for binary and multiclass classification problems. The goal of this project is to predict the probability that an input belongs to a certain class.

### Key Concepts

* **Regression vs. Classification**: A regression problem predicts a quantity, while a classification problem predicts a class.
* **Logistic Regression**: An algorithm that predicts the probability of an input belonging to a certain class using a linear model and the logistic function (sigmoid).
* **Sigmoid Function**: A mathematical function that maps any real-valued number to a value between 0 and 1, used for binary classification.
* **Softmax Function**: A generalization of the sigmoid function for multiclass classification problems, normalizing a vector into a discrete probability distribution.
* **One-Hot Encoding**: A method for representing classes in a dataset as vectors, where each class is assigned an integer value and represented by a vector with one element set to 1 (and all others set to 0).

### Practical Notes

To implement logistic regression and multiclass classification using the softmax function, you will need to:

* Use the sigmoid function for binary classification
* Use the softmax function for multiclass classification
* Apply one-hot encoding to represent classes in a dataset as vectors
* Choose an activation function (sigmoid or softmax) based on the type of classification problem
* Select a loss function (cross-entropy loss is used with the softmax function)

Note: This project assumes prior knowledge of linear models and regression problems.

## Transcript

We now have a good understanding of a regression problem where we're trying to predict the quantity. In a case of classification problems, we are trying to predict a class. For example, a type of traffic signs. More precisely, we're trying to predict the probability that an input belongs to a class. For this task, we will consider a new algorithm called logistic regression.

In logistic regression, we are predicting the probability that a given input belongs to a certain class. To keep things simple, we want to use a linear model to estimate the probability of a class y given an input x. Meaning that the conditional probability of y given x is linear in x. You will recognize here the linear equation that we saw previously. However, we have one issue with using a linear model.

We cannot enforce the outputs of a linear model to be between zero and one, which is a default requirement if we are trying to model the probability. To meet this requirement, we are going to transform the outputs of our linear model. In this slide, we are going to introduce the logistic function, also called sigmoid. The logistic function is defined as exponential of x divided by 1 plus exponential of x. The logistic functions domain is 01, meaning that regardless of the value of x, sigma of x will fall between zero and one.

This is a great property to use when we are trying to model a probability. Now, we will compose these logistic function with the linear equation shown in the previous slide to create the logistic regression algorithm. Later in this lesson, we will use the term activation function to describe functions transforming the output of a linear operation. The sigmoid function is used for binary classification, where x is a vector of size one. However, we are mostly interested in multiclass classification problem, such as the traffic sign classification problem.

In this case, we need to use the softmax function as our activation function. The softmax function is a generalization of the sigmoid function, but using multiple dimension. The softmax function normalizes a vector x of n components into a discrete probability distribution, meaning that the sum of the element of x will add up to one. This is how the softmax function works. We start by applying the exponential function to each element of the vector x.

Then we divide each element of x by the sum of the element of x. By doing so, we ensure that the sum of the output vector is one. Now that we have a new activation function for the multiclass classification problem, we need a loss function. The cross-entropy loss is used on the vector y hat after it has been normalized by the softmax function. In this equation, y hat is thus a discrete probability distribution.

There is something we haven't addressed though. What is y, the ground-truth, in the case of multi-class classification? According to this equation, the ground-truth must be a vector. Let's solve this mystery in the next slide. To represent the ground-truth y as a vector, we are going to use a method called one-hot encoding.

With one-hot encoding, we are creating a mapping of each class in our dataset to a vector of size equal to the number of classes. One-hot encoded vectors are made of zero, except for a single element equal to one. Let's simplify the traffic sign dataset by assuming that we only have six classes. First, we assign an integer i to its class in the dataset. For example, the traffic lights sign will get assigned four.

Then we create a vector of zeros of dimension one by six. Finally, we set the ith element of this vector to one. Keep in mind that one-hot encoding is not the only approach to encode classes in multi-class classification. We have now defined an algorithm for multi-class classification, as well as a loss function and a way to encode the ground-truth. Now, how do we teach our algorithm to fit the observations?

## Additional Content

## Logistic Regression
For classification problems, we can also use a linear expression to model the probability  `P(Y|X)` of an input belonging to a certain category. Such a model is called **logistic regression** and looks like this: `P(Y|X) = mx+b`. However, given that we want to model a probability, we need a way to constrain `mx+b` to the `[0, 1]` interval. To do so, we are going to use the **logistic function (or sigmoid)**.  The logistic function maps any real number to the `[0, 1]` interval. 

The **softmax function** is the extension of the logistic function to multiple classes and takes a vector as input instead of a real number. The softmax function outputs a discrete probability distribution: a vector of similar dimensions to the input but with all its components summing up to 1. Later in this lesson, we will describe the sigmoid and softmax functions as **activation functions**. 
### Cross-Entropy Loss and One-Hot Encoding
*Error: the subscript `j` in the cross entropy loss formula should be replaced by `i`.*

**Warning**: in the video, the one-hot encoded vector is 1-indexed, which is different from numpy 0-index approach.
The **Cross Entropy (CE)** loss is the most common loss for classification problems. The total loss is equal to the sum over all the observations of the dot product of the ground truth one-hot encoded vector and the log of the softmax probability vector. 

For multiple classes classification problems, the ground truth labels need to be encoded as vectors to calculate. A common approach is the **one-hot encoding** method, where each label of the dataset is assigned an integer. This integer is used as the index of the only non zero element of the one-hot vector.  
**Summary:** for classification problems, the labels need to be encoded to a vector of dimension `C`, where `C` is the number of classes in the dataset. Thanks to the softmax function, the model outputs a discrete probability distribution vector, also of dimension `C`. To calculate the cross entropy loss between the input and the output, we calculate the dot product of the one hot vector and the log of the output.
