# Other Optimizers

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=cQWnRwnlhz8)

## Summary

**Stochastic Gradient Descent (SGD) with Momentum**
=====================================================

This project introduces stochastic gradient descent (SGD), a fundamental algorithm for training machine learning models. We'll explore its limitations and discuss an improvement known as SGD with momentum.

### Key Concepts

* **Local Minima**: A local minimum is a point in the loss function where the optimizer gets stuck, resulting in a sub-optimal solution.
* **Stochastic Gradient Descent (SGD)**: An optimization algorithm that updates model weights based on the gradient of the current batch.
* **Momentum Addition**: Adding a velocity term to SGD to help overcome local minima by updating weights using both the current and previous gradients.
* **Velocity Term**: Defined as the previously calculated velocity scaled by a factor (Mu) minus the learning rate times the gradient.
* **Hyperparameters**: Model parameters that are set before training, such as the learning rate. Hyperparameter tuning is crucial for achieving optimal results.

### Practical Notes

When using SGD with momentum:

* The weights are updated by adding the velocity term to the current update.
* Momentum helps overcome local minima and is a popular method used in conjunction with SGD.
* Other optimization methods exist, such as Adam, RMSprop, Nesterov momentum, and lookahead optimizer.

In practice:

* Picking the correct learning rate is critical for the success of SGD. A too-low learning rate leads to slow convergence, while a too-high learning rate may cause divergence.
* Hyperparameter search is essential when experimenting with machine learning models. This involves trying different values of hyperparameters to achieve optimal results.
* Annealing, or decreasing the learning rate over time, can help improve model performance. Popular methods include stepwise annealing, cosine annealing, and exponential annealing.

Note: The code for implementing SGD with momentum is not provided in this transcript, but it will be covered in subsequent lessons.

## Transcript

We learned about stochastic gradient descent or SGD but other optimizer exist. The first one we need to mention is an improvement over SGD. For neural network, especially the loss function tend to have many local minima. As we can see on this animation. It is possible that the optimizer gets stuck in a local minimum, giving us a sub-optimal solution to our loss minimization problem.

For example, SGD could get stuck in this first local minimum here. The momentum addition to SGD helps to overcome this problem. This method draws its inspiration from physics. We are adding a velocity term to the SGD, updating the weights using not only the gradient of the current batch but also the previously calculated gradient. The velocity term is defined as the previously calculated velocity scale by a factor Mu minus the learning rate times the gradient.

The weights are then updated by adding the velocity. As we can see in this animation, adding the momentum helps our optimizer overcome local minimum. Momentum is a very popular method and almost always added to the SGD optimizer. Despite its simplicity, SGD with momentum is still one of the most popular optimizer but it is worth noting that other very popular method exist, such as the Adam optimizer, the RMSprop optimizer, the Nesterov momentum, and the lookahead optimizer. Some of these method use a secondary variable of the loss to perform updates and add additional scaling factors.

We're referencing the different papers below. If you want to learn more about these optimizers. The SGD optimizer is so popular partially because it comes with a single parameter: the learning rate. However, picking the correct learning rate is critical to the success of SGD, as we will see in this slide. If the learning rate is too low, the SGD algorithm will require too many steps to reach the global optimum.

We may end up with the best possible solution, but at the cost of many extra hours of training, when the learning rate is too high, the optimizer may not even reach the global optimum and lead to divergent behavior. We will see either an increasing or non-decreasing training loss. However, when the learning rate is at the correct value, the model will quickly converge to its global optimum. As a side note, we use the term hyperparameter to differentiate scalers like the learning rate from the models' parameters. When experimenting with machine learning models, we often try different values of these hyperparameters to get the best possible results.

To do so, we perform what we call a hyperparameter search, which you will have to do in the final project of this course. When training machine learning models, we can use a fixed learning rate. However, it is pretty common to decrease the learning rate over time. We can think of it this way. At the beginning of training, we can use a high learning rate to have the model converge faster.

However, after some time, we will need a smaller learning rate to perform final updates and find the global optimum. Reducing the learning rate during training is called annealing, and several methods are popular. Stepwise annealing, for example, decreases the learning rate by a constant factor every n steps. For example, we can decide to divide the learning rate by two every 500 steps. Cosine annealing and exponential annealing, are also two very popular ways to decrease the learning rate.

In the next videos, we will see how to use gradient descent to train neural networks.

## Additional Content

## Other Optimizers
One way to overcome the local minima issue is to add a **momentum term**. This approach is taking its inspiration from physics: the optimizer should gain velocity when taking multiple consecutive steps in the same direction. This velocity will help the optimizer to overcome local minima.

You can read more about momentum in the [original paper](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.57.5612&rep=rep1&type=pdf). 

This paper provides a nice overview of the most common optimizers used in deep learning: [An overview of gradient descent optimization algorithms](https://arxiv.org/pdf/1609.04747.pdf).
### Learning Rates and Annealing
As you will realize in the final project, the learning rate plays a critical role in the success of gradient descent approaches. A very popular approach to improve the performances of gradient descent methods is **learning rate annealing** which consists of decreasing the learning rate during training. Different strategies exist, such as stepwise annealing, cosine annealing or exponential annealing. The term **learning scheduler** is also used.
