# Big Picture

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=afh_9W2pyL4)

## Summary

**Modeling Fundamentals**
=======================

This project covers the basics of machine learning models, including definitions, key concepts, and practical applications.

**Key Concepts**
---------------

* **Model**: A set of computations that extract information from an input or observation. In this context, a model is used to process data and make predictions.
* **Loss Function (Cost Function)**: A function that maps the outputs of the model to a single real number, indicating how well the model is performing. A low cost means good performance, while a high cost indicates room for improvement.
* **Metric**: A function that quantifies the performance of an algorithm. Metrics provide meaningful information about a model's accuracy and effectiveness.

**Practical Notes**
------------------

When working with machine learning models, it's essential to understand the difference between loss functions and metrics. Loss functions are typically differentiable, while metrics may not be. This distinction is crucial when evaluating model performance.

In this project, we'll explore three algorithms:

* **Linear Regression**: A linear model that predicts a continuous output variable based on one or more input features.
* **Logistic Regression**: A binary classification algorithm that uses logistic functions to predict the probability of an event occurring.
* **Neural Networks**: A type of machine learning model inspired by the structure and function of the human brain. Neural networks can be used for both regression and classification tasks.

These algorithms will be discussed in more detail, along with their corresponding loss functions and practical applications.

## Transcript

Let's start with a few definitions. We have been talking about models since the first lesson of this course. But what is a model exactly? Well, in our case, a model is a set of computations that extract information from an input or observation. We will also be using the term loss or cost function a lot in this lesson.

A loss or cost function is a function that maps the outputs of the model to a single real number. A low cost means that our model is doing a great job and a high cost means that there is space for improvement. Finally, we should define metrics. In machine learning, a metric is a function that quantify the performances of an algorithm. We have seen multiple metrics already, such as precision, recall, or accuracy.

By the way, why do we need both the loss function and a metric? Don't they both quantify a model's performances? First of all, a loss function must be differentiable, as we will see in the following slides, which is often not the case for metrics. Secondly, the loss does not necessarily give us meaningful information on the model's performances, but rather describe how good a model is at fitting the data. Let's see how everything fits in together.

In a case of traffic sign classification, the input or observation is an image of a traffic sign. We feed this image to model, for example, the neural network, and we get an output. This output can take different shapes depending on the model. But in the case of multi-classes classification, it is a vector. This output will be used to calculate both the loss and the metrics.

In this lesson, we will study three different algorithms, linear regression, logistic regression, and neural networks, and the corresponding loss function. Let's get started with linear regression.

## Additional Content

## Big Picture
In this course, we will create ML **models** to predict an output based on an input observation. To estimate the fit of our model, a **loss function** will be used and the performances of the model created will be quantified with a chosen **metric**.

- **Model:** a set of computations that extracts pattern from an input.
- **Loss function / cost function:** A function that maps the outputs of a model to a single real number.
- **Metric:** a function that quantifies the performances of an algorithm.
