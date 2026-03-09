# Model Selection

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=_tEQk0T1JiA)

## Summary

**Model Building and Baseline Establishment**
=============================================

This lesson focuses on building a model for classification tasks by establishing a baseline. A baseline is a measure of how well a human or an algorithm can perform on a task.

### Key Concepts

* **Baseline**: A benchmark to evaluate the quality of models, representing either the upper bound (human performance) or lower bound (random guessing).
* **Upper Bound**: Human performance on a task, assuming perfect accuracy.
* **Lower Bound**: Random guessing by an algorithm, resulting in an accuracy of 0.5 for binary classification tasks.
* **Model Iteration**: Starting with simple models and gradually increasing complexity to select the best model.

### Practical Notes

When building a model:

1. Establish a baseline by trying to classify images manually (upper bound) or implementing a random guessing algorithm (lower bound).
2. Start with simple models like linear and logistic regression for regression and classification problems.
3. Iterate on complexity, experimenting with more complex algorithms like polynomial regression or neural networks.
4. Train each model on the training split and evaluate it using the validation set.
5. Keep the training and validation sets consistent when iterating on the model to maintain experiment integrity.

Example code snippets:

* Random guessing algorithm: `accuracy = 0.5` (binary classification)
* Simple models like linear and logistic regression: implementation depends on the programming language and library used.

## Transcript

We now have to deal with building a model. Before we dive into model building, we have to establish a baseline. It will allow us to better assess the quality of our models. These baseline could be an upper bound. For example, how good would a human be at solving this task?

In a case of traffic sign classification, we can safely assume that a human would have an accuracy close to one. While exploring the data, it's actually important to try to classify the different images by yourself. This baseline could also be a lower bound. For example, how good would the algorithm be if he was randomly guessing predictions? Let's say that we have two different types of traffic signs.

If you were to build a random guessing algorithm, the accuracy of such an algorithm would be around 0.5. Any algorithm built later on that has an accuracy under 0.5 is actually worse than random guessing. Once you have established these baselines, you can start building different models. A good rule of thumb is to start from the simplest possible model and iterate on complexity. For example, linear and logistic regression are fairly simple models and usually a good starting point for regression and classification problems.

Then we can iterate using more complex algorithm such as polynomial regression or neural networks. How do we iterate to select the best model? Well, we start with the simplest model, train it on our training split, and evaluate it using the validation set. Once we have evaluated this model, we can experiment with a different one based on our findings. For example, we could try a polynomial regression model.

We train it and realized that it overfits out datasets. We can decide to offer simpler model with less parameters. We can also experiments with different techniques to reduce overfitting. Keep in mind that the training and validation sets have to remain the same when iterating on the model in order to maintain the integrity of our experiments, we may sometimes have to gather more data, in which case, we have to start over the model selection process.

## Additional Content

## Model Selection
ML Engineers get very excited about creating new models. However, before diving into this step of the ML workflow, one must set **realistic expectations**, by setting up baselines. 

A **lower bound baseline** gives you an idea of a minimum expected performance. If you are getting metrics below such baseline, a red flag should be raised and should be concerned that something is wrong with your training pipeline. For example, for a classification problem, the random guess baseline is a good lower bound. Given C classes, the accuracy of your accuracy of your algorithm should be higher than 1/C. 

An **upper bound baseline** gives you a sense of the maximum expected performance. If a client comes to you and asks for an algorithm that classifies images correctly 100% of the time, you can safely let them know that it won't happen. Human performance is a good upper bound baseline. For a classification problem, you should try to manually classify 100s of images to get an idea of what level of performance your algorithm could reach.

Model selection is a **dynamic** part of the ML workflow. It requires many iterations. Unless you have some prior knowledge of the task, it is recommended to start with simple models and iterate on complexity. **Keep in mind that the validation set should remain the same during this phase!**
