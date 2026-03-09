# Introduction to Machine Learning Algorithms

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=pQK4_6z6hr0)

## Summary

**Machine Learning Algorithm: Building from Scratch with TensorFlow**
====================================================================

This project is an introduction to building machine learning algorithms from scratch using TensorFlow. We will focus on regression and classification problems, and learn how to build models that can predict outcomes based on observations.

**Key Concepts**
---------------

* **Regression**: predicting a quantity by understanding the relationship between two or more variables
	+ Example: predicting trip duration based on distance
* **Classification**: assigning a class to an input
	+ Example: classifying traffic signs into different categories
* **Linear Regression**: assuming a linear relationship between two variables
* **Logistic Regression**: a classification algorithm that uses logistic function to predict probabilities
* **Feed-Forward Neural Networks**: a type of neural network used for classification and regression tasks
* **Gradient Descent**: an optimization method used to minimize the loss function in machine learning models

**Practical Notes**
------------------

This project involves building three types of machine learning algorithms from scratch:

1. Linear Regression: predicting a quantity based on a linear relationship between two variables
2. Logistic Regression: classifying inputs into different categories using logistic function
3. Feed-Forward Neural Networks: classifying images using back-propagation mechanism

We will use TensorFlow to implement these algorithms and train them on traffic sign data sets. The expertise gained in this project can be applied to many other machine learning problems.

## Transcript

Hi, and welcome back for the next lesson of this course, introduction to machine learning algorithm. In this lesson, you will learn about different machine algorithm, and how to build them from scratch using TensorFlow. Lets get started. In the previous lessons of this course, we introduced the machine learning workflow. We focused on framing a machine learning problem and understanding the data.

In this lesson, we will concentrate on the last step of this workflow, modeling. We can use machine learning for different purposes, but in this course, we will focus on prediction. We are trying to build a model to predict an outcome based on the set of observations. In our case, the observations will be images, and we will try to predict different things, such as object classes or location. In this lesson, we will focus on two types of machine learning problems, regression, and classification.

Let's start with regression. A regression problem is when you're trying to predict a quantity, more precisely, we are trying to understand the relationship between two or more variables. For example, we may be interested in predicting a trip duration based on the distance. In this lesson, we will focus on linear regression, where we assume a linear relationship between two variables. We will also tackle some classification problems using the traffic sign data sets.

In a classification problem, we are trying to assign a class to an input. We will focus on two types of classification algorithm, logistic regression, and feed-forward neural networks. You will build both of them from scratch and train them to classify traffic signs. Linear regression, logistic regression, and neural networks are very common approaches to tackle regression and classification problem, and the expertise you will gain in this lesson can be applied to many other problems. This lesson will be organized as follows.

First, we will focus on linear regression, a type of regression algorithm. Then, we will move to logistic regression. An algorithm for classification. Both algorithm require that you solve an optimization problem, and we will learn about an optimization method called gradient descent. We will then move to the main family of algorithms we will study in this course, neural networks.

We will study back-propagation, a mechanism that propagates the gradient within your networks. Finally, we will see how we can use neural networks to classify images. I'm very excited about this lesson because we are going to start building machine learning algorithm.

## Additional Content

## Introduction to Machine Learning Algorithms
In this course, we focus on the **prediction task**, which consists of predicting an outcome using a set of observations. In particular, we will focus on the following:
- **Regression:** predict a quantity (eg, distance, time) and understand the relation between two variables.
- **Classification:** assign a discrete class (eg, traffic sign) to an input.

This lesson will be organized as follow:
- Linear regression
- Logistic regression
- Optimization with gradient descent
- Feed forward neural networks
- Backpropagation
- Image classification with a neural network
