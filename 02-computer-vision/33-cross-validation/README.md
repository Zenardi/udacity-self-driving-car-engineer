# Cross Validation

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=zx429-WiMYg)

## Summary

**README: Understanding Model Generalization and Overfitting**

This project focuses on building machinery models that generalize well to new data without overfitting. We explore the concept of overfitting, where a model fits the training data too closely and fails to perform well on unseen data.

### Key Concepts

* **Overfitting**: When a model is too complex and fits the training data too closely, resulting in poor performance on new data.
* **Bias-Variance Trade-off**: The balance between minimizing bias (how good the model is given the training data) and variance (the amount by which the model's parameters change with different training data).
* **Test Error**: The error rate of a model on unseen test data, which can be decomposed into three terms: bias, variance, and epsilon.
* **Bias-Variance Trade-off Curve**: A plot showing how the test error changes as the complexity of the model increases, illustrating the optimal complexity for minimizing test error.
* **Cross-Validation**: A technique for evaluating a model's performance on unseen data by splitting available data into training and validation sets.

### Practical Notes

* When working with large datasets (e.g., over 10,000 images), it is common to use a 90%:10% split between training and validation sets.
* To avoid overfitting the validation set, it's essential to keep a separate test set that has not been used during training or validation.
* When splitting data into training, validation, and test sets, careful crafting of the splits is crucial to ensure that the validation set is representative of unseen data.

This project aims to provide a solid understanding of model generalization and overfitting, as well as practical guidelines for implementing cross-validation and avoiding common pitfalls.

## Transcript

When building a machinery model, we want our model to generalize as well as possible. Let's consider the following example. In the first case, shown by the graph on the left, we fit a linear regression model to our dataset as shown by the blue line. In the other case, shown on the right, we use a polynomial regression model which is a much more complex machine learning model and we observed that this model fits the data precisely. However, how do you think each model is going to perform on new data?.

The linear regression model will better perform on this new data because it's not fitting the original data as closely. We will say that this model generalizes well to new data. However, the polynomial regression model will not perform well on the new data. We'll use the term overfitting to describe this behavior. The challenge of machine learning lies in creating a model that performs well on the available data without overfitting.

We'll cover these in depth in later sections. From now on, we will use the term Training datasets to describe the data that our models have been trained on and the term Test dataset to describe data that has not been used during training. We'll use the test dataset to solve this overfitting issue. In the following videos, we'll describe how to create such datasets. Since we would like our algorithm to generalize to unseen dataset during training, we're going to focus on the performance of our algorithm on the test dataset.

In particular, we are interested in the test error which is the error rate of our model on the test dataset. The test error can be decomposed into three terms. The variance, the bias, and epsilon which we will ignore for the moment. The variance describes the amount by which our model's parameters would change if we were to change the training data. The bias describes how good our model is given the training data.

To minimize the test error, we need to minimize both of bias and the variance which means that we need our model to both perform well on the training data and the test data. However, by minimizing the bias, we tend to increase the variance because we are over-fitting the training data set. Let's look at an example together. We are fitting a model on a particular dataset and we can control the complexity of this model. For example, by increasing the number of parameters.

Well, as the model becomes more complex, the bias in red decreases. Our model has more capacity to fit the training data. However, the variance in purple increases with the complexity as our model becomes more and more specialized to this dataset and loses its capacity to generalize. If we sum both terms, we obtain the test error in blue. The blue curves show the existence of an optimal complexity where the test error is minimized.

Well, this is what we call the bias-variance trade-off. You want your model to be complex enough to have a low bias but not too complex so that you can still generalize to unseen data. As we discussed previously, we would like to evaluate our model on the test data rather than the training data. However, most of the time, we do not have access to a testing dataset and end up using a validation set approach. In that case, we split the available data into two different subsets, training and validation.

A good rule of thumb consists in putting 80 percent of the data in the training set and 20 percent in the validation set. However, when a lot of data is available over 10,000 images, for example, it is pretty common to use a 90 percent,10 percent split. In some cases, you may also want to create a test set by splitting the data into three splits. For example, 75 percent of the data for the training set, 50 percent of the data for the validation set, and the remaining 10 percent for the test set. What is the difference between test and validation sets?

Well, the validation set is used for cross-validation. Meaning that we will use this set to evaluate our model and choose the best possible parameters to minimize the error. We can also use this set to compare models between each other. The test set, however, should only be used once our model has been chosen. But why is that?

Well, when performing many experiments to increase the model's performance on the validation set, we put ourselves at risk of leaking into the validation set. Because of this repeated process, we are slowly leaking information from the validation set into the training set, and we may end up with a model over fitting the validation set, which removed the point of cross-validation. By keeping a separate test set, we can protect ourself from data leakage. Another type of data leakage can happen when the splits are not created carefully. Indeed, the validation set could contain observation that are very close to the train set, which once again, defeat the purpose of cross-validation.

For example, the Waymo dataset is made of sequences of images taken from videos. If we were to split such data randomly between training and validation, we would not have a good validation set because the distribution would be very similar to the one of the training set. For example, we could decide to split images based on Trip IDs such that all the images from the same sequence are in the same split. Cross-validation is a very powerful ID in machine learning, but it requires careful crafting of the data splits.

## Additional Content

## Cross Validation
The goal of our ML algorithm is to be deployed in a production environment. For example, the object detection algorithm you will create in the final project could be deployed directly in a self driving car. But before we can deploy such algorithms, we need to be sure that it will perform well in any environments it will encounter. In other words, we want to evaluate the **generalization** ability of our model. 

We are going to introduce three new concepts:
* overfitting: when the model does not generalize well
* bias-variance tradeoff: why is it hard to create a balanced model
* cross validation: a technique to evaluate how well the model generalizes

### Overfitting
When a model is **overfitting**, it loses its power to generalize. It often happens when the chosen model is too complex and starts extracting noise instead of meaningful features. For example, a car detection model is overfitting when it starts extracting brand specific features of the cars in the dataset (e.g., car logo) instead of broader features (wheels, shape etc).

Overfitting raises a very important question. How do we know if our model will generalize properly or not? Indeed, when a single dataset is available, it will be challenging to know if we created a model that overfits or simply performs well. 

For now, we will use the terms **training data** to describe the data used to teach and create our algorithm and **test data** for any new, unseen data.
### Bias & Variance Trade-off
The **bias-variance tradeoff** illustrates one the most important challenges in Machine Learning. How do we create a model that performs well while keeping its ability to generalize to new, unseen data? The performance of our algorithm on such data is quantified by the **test error**. The test error can be decomposed in further into the bias and the variance. 

The **bias** quantifies the quality of the fit of our model on the training data.  A low bias means that our model has a very low error rate on the training dataset.

The **variance** quantifies the sensitivity of the model to the training data. In other words, if we were to replace our training dataset with another one, how much would the training error rate change? A low variance means that our model is not sensitive to the training data and generalizes well. 

### Validation Sets & Cross Validation
**Cross validation** is a set of techniques to evaluate the capacity of our model to generalize and alleviate the overfitting challenges. In this course, we will leverage the **validation set** approach, where we split the available data into two splits: 
* a **training set**, used to create our algorithm (usually 80-90% of the available data)
*  a **validation set** used to evaluate it (10-20% of the available data)

In further videos, we will see how we can leverage this approach to alleviate the overfitting problem. 

Other cross validation methods exist, such as **LOO (Leave One Out)** or **k-fold** cross validation but they are not suited to Deep Learning algorithms. You can read more about [these other two techniques here](https://www.cs.cmu.edu/~schneide/tut5/node42.html).
