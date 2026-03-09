# Lesson Conclusion

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=R9cmwJunJ6w)

## Summary

**Machine Learning Problems and Algorithms**
=============================================

This project covers the basics of machine learning problems and algorithms, including regression and classification. We will explore the key concepts, loss functions, and performance metrics used in these problems.

### Key Concepts
* **Regression**: predicting a quantity such as age, weight, or speed using L2 loss.
* **Classification**: predicting the probability of belonging to a class using cross entropy loss.
* **Loss Functions**:
	+ L2 loss for regression
	+ Cross entropy loss for classification
* **Performance Metrics**:
	+ Mean square error (MSE) for regression
	+ Accuracy for classification

### Practical Notes
We implemented logistic regression and neural networks in TensorFlow, using gradient descent and iterative optimization algorithms to train the models. We also learned about activation functions used in neural networks and the importance of babysitting the training process.

Note: This project assumes prior knowledge of machine learning concepts and TensorFlow basics.

## Transcript

In this lesson, we studied two types of machine learning problems, regression and classification. This table summarizes the differences between them. In a regression problem, we are trying to predict a quantity such as age, weight, or speed. Whereas in classification, we want to predict the probability of belonging to a class. The loss function used are also different.

In regression we use the L2 loss, whereas in classification we use a cross entropy loss. Keep in mind that many other loss function exist for both of these problems. Finally, we measure the model performances differently. For our regression problem, we use the mean square error but for classification problem, we'll use the accuracy. Later on, we will study one more type of machine learning problem, object detection.

Let's summarize what we have learned in this lesson. We discovered three different machine learning algorithms: linear regression, logistic regression, and neural networks. We also learn about different loss functions that we could use to train these algorithms. We implemented gradient descent and iterative optimization algorithm to train these models. We also learn about the different activation function used in neural networks.

We took a dive into the backpropagation mechanism, a way to propagate the gradient in the neural network. Finally, we learned the importance of babysitting the training of a neural network. In this lesson, we have studied two machine learning problems, classification and regression. You have implemented your first machine learning algorithm in TensorFlow; logistic regression, and neural networks. Congratulations, this is no easy feed, and you are now ready to tackle a new class of algorithm: convolutional neural networks.

## Additional Content

## Lesson Conclusion
In this lesson, we learned about:
- **Linear regression:** a regression approach to model a linear relationship between two variables. We also discovered the L1 and L2 losses.
- **Logistic regression:** a classification algorithm and a classification loss, the Cross Entropy Loss.
- **Optimization with gradient descent:** an iterative algorithm to find the optimal solution of the loss minimization problem.
- **Feed forward neural networks:** a type of neural network made exclusively of fully connected layers. 
- **Backpropagation:** an algorithm using the chain rule to calculate the gradient of the loss in a neural network.
- **Image classification with a neural network:** how to flatten an image to feed it in a feedforward NN.
