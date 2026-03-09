# Image Classification with a Feedforward Neural Network

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=oo_S2TiEN1E)

## Summary

**Traffic Sign Classification with Neural Networks**
=====================================================

This project involves using a neural network to classify traffic signs from images. The goal is to transform 3D image arrays into 1D vectors that can be processed by the neural network.

### Key Concepts

* **Flattening Layer**: A layer that transforms a 3D array into a 1D vector without learnable weights, allowing it to fit in a feedforward neural network.
* **Gradient Descent and Backpropagation**: Complex mechanisms involved in neural network training that require careful tuning of hyperparameters.
* **Learning Rate**: A critical hyperparameter that affects the convergence rate of the model. A high learning rate can lead to an exploding loss, while a low learning rate may result in slow convergence.
* **No Free Lunch Theorem**: States that no single algorithm is optimal for all types of datasets and tasks, requiring experimentation with different architectures and hyperparameters.

### Practical Notes

When training neural networks, it's essential to:

* Visualize the loss function during training to identify potential issues early on.
* Monitor both the training and validation metrics to catch overfitting or poor performance.
* Experiment with different learning rates and annealing techniques to optimize model convergence.
* Use a GPU for efficient training, but be prepared to troubleshoot any issues that arise.

By following these guidelines and understanding the key concepts involved in neural network training, you'll be well-equipped to tackle complex projects like traffic sign classification.

## Transcript

Now that we have a good understanding of the mechanism behind neural networks training. Let's come back to our original problem, the traffic sign classification. We can use a neural network for this task. However, as we have seen in the previous lesson, an image is a 3D array. To fit such an input in a feedforward neural network, we need to transform this 3D array into a 1D vector.

To do so, we use a flattening layer. Such layer does not have learnable weights but simply transform the array by reshaping it. In later lessons, we'll see how a convolutional neural network take a different approach to this problem. By flattening this image, we are now able to fit it in our neural network. In this course, we will learn a few tricks to correctly train neural networks.

In the following slides, we will learn the first of them. A crucial thing to understand about neural network is the necessity to babysit the training process. Because of the complexity of the mechanisms involved, such as gradient descent or backpropagation, and the different hyperparameters, such as the learning rate, a lot of things can go wrong when training a neural network. Visualizing the loss function during training can help identify mistakes early on. The following graph shows the consequences of different values of learning rate on the last function.

A very high learning rate will lead to an exploding loss. For high learning rate, we will see that the model converges, but reaches a plateau quite early during training. Remember the gradient descent video. This happens when the step taken by the optimizer are too large to find the global minimum. A low learning rate will lead to slowly decreasing loss.

When the learning rate is just right, the loss function will rapidly decay at the beginning of training and then reach a slower decay rate. Keep in mind that annealing the learning rate is a great way to overcome some of these issues. Training neural network often requires a GPU, which can be very expensive. Some training take several hours or even days and the machine learning engineer should be able to quickly identify any issues with the training to save time and money. A low or high learning rate are not the only issues you may be facing while training a neural network because of the no free lunch theorem, which states that no perfect algorithm exist for all types of dataset and tasks, the machine learning engineer has to experiment with different architectures and hyperparameters value.

Some of the algorithm the machine learning engineer creates may actually overfit the training data set and perform poorly on the validation set. In addition to visualizing the loss, the machine learning engineer should also visualize the different metrics on both the training and the validation sets. If our algorithm is well fitted for the task, the validation metrics should closely follow the training metrics. However, if for some reason, our algorithm is fitting the training set, we will observe that the validation metric is much lower than the training metric. By monitoring the loss and the metrics of both the training and validation sets, we will be able to catch early on any problem without training process.

## Additional Content

## Image Classification with a Feedforward Neural Network
Because feed forward neural networks take vectors as inputs, we need to flatten the `HxWxC` image to a `(HxWxC)x1` vector. 
### Babysit Training
Training neural networks is a costly and lengthy process. Because so much can go wrong when training a NN, it is critical for the ML engineer to babysit the training process. **Visualizing the loss and the metrics** will help identify any problems with the training process and allow for the engineer to stop, fix and restart the training.
