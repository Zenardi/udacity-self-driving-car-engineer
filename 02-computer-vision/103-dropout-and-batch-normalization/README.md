# Dropout and Batch Normalization

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=iTNEVVprxPo)

## Summary

**Dropout Layer and Batch Normalization Layer**
=============================================

This README file provides a summary of the dropout layer and batch normalization layer, two key concepts in deep learning.

### Key Concepts

* **Dropout**: A technique used to prevent overfitting by randomly deactivating neurons with a set probability. This is achieved by dropping connections between layers.
	+ Example: Using a probability of 0.5 for each layer, roughly half of the neurons are deactivated.
	+ Properties:
		- Does not have learnable parameters
		- Behaves differently during training and validation
		- Does not drop any neurons during testing
* **Batch Normalization**: A technique used to improve convergence time by normalizing input data.
	+ Works by calculating the mean and variance of the input over a mini-batch, then scaling and shifting the input using learnable parameters gamma and beta.
	+ Properties:
		- Has two learnable parameters: gamma and beta
		- Behaves differently during training and testing
		- Sensitive to batch size; should be used with larger batch sizes

### Practical Notes

* Dropout is often used in modern architectures to prevent overfitting and improve model performance.
* Batch normalization can significantly improve convergence time by normalizing input data.
* Both dropout and batch normalization layers behave differently during training and testing.

**Example Code**
```python
# Dropout layer example
import torch.nn as nn

dropout_layer = nn.Dropout(p=0.5)

# Batch normalization layer example
import torch.nn as nn

batch_norm_layer = nn.BatchNorm2d(num_features=64)
```
Note: The code examples provided are simplified and may not be directly applicable to a specific use case.

## Transcript

The next layer I would like you to know about is do dropout layer. What is the dropout layer? Let's consider an example of a small feed-forward network. Without dropout, we see that each neuron network layer is connected to each neuron of the previous and the next layers. Well, what dropout is going to do is drop some of this connection by deactivating neuron with a set probability.

For example, we can use dropout with a probability of 0.5 for each layer, meaning that roughly half of the neurons of this layer will be randomly deactivated. We will repeat this process for each input of the training data set, meaning that different neurons are deactivated at each training step. This is a great technique to prevent overfitting and potentially improve your model performances. Let's look at some of the properties of the dropout layer. Well, first of all, the dropout layer does not have any learnable parameters, the dropout layer the a particularity of behaving differently during training and validation.

During training, it will follow the behavior that we have described in the previous slide by randomly dropping neurons. However, during testing, it does not drop any neurons. Why is that? Because along the line, we care about the performances of the model and the validation and test sets. Such performances should be deterministic.

What if you were to deploy model to production that randomly performs poorly? This would be terrible. The power of dropout comes from its capacity to prevent overfitting because it artificially reduces the number of parameters. It is a great tool and often used in modern architectures. Dropout has also some interesting properties that out of the scope of this course, but I included some of the research papers below.

In this video, we are going to focus on another very popular layer, the batch normalization layer, or batch norm. The batch norm layer works as follows. During training, we are going to calculate the mean value of the input of this layer as well as the variance. Both mean and variance are calculated over the entire mini-batch. This layer also has two learnable parameters, gamma and beta.

Let's see how all of these fits together. First, we are going to normalize the input x by removing its mean and dividing it by the square root of its variance. The epsilon parameter ensures that we never have a denominator of zero. This normalized input will be multiplied by gamma and added beta. Why are we doing such an operation?

Well, the main improvement of the batch norm layer is over the convergence time of the neural network. Neural networks with batch normalization layer are converging much faster than neural network without. The batch norm layer is actually scaling the inputs. The batch norm layer is often located after the convolution layer but before the activation layer. Because the batch norm uses batch statistics, it is actually sensitive to the batch size and should be used with larger batch sizes.

Finally, similarly to the dropout layer, the batch norm behaves differently at training and testing. During training, it calculates statistics over mini-batches. During testing, however, the statistic calculating during training are used instead of the test mini-batches statistics. This layer has such behavior simply because the batch size should not influence the prediction at testing time. Well, with these two more layers, we are now ready to look at deeper and more modern convolutional neural network architectures.

## Additional Content

## Dropout and Batch Normalization

### Dropout
**Dropout** was introduced in a [2014 paper](https://jmlr.org/papers/volume15/srivastava14a/srivastava14a.pdf) as a way to prevent overfitting. Dropout can be used in fully connected or convolutional layers and simply randomly disable neurons during training.  Dropout does not have any learnable parameters and has only one hyperparameter, the probability `p` of a neuron being disabled. 

It is important to note that Dropout does not behave similarly during training and testing. Indeed, because we want the behavior of our model to be deterministic in production, dropout is turned off and neurons are not randomly disabled anymore. The main consequence of this is the need to **scale** the neurons output. To be understand this, let us consider a simple fully connected layer containing 10 neurons. We are using a dropout probability of 0.5. Well during training, a neuron in the next fully connected layer will on average receive an input from 5 neurons. However, during testing, the same neurons will receive an input from 10 neurons. To get a similar behavior during training and testing, we need to scale the neuron's output by 0.5 during testing time.

In practice, we use something called **inverted dropout**, where scaling is happening during training. Why? Because we want the model to be as fast as possible when deployed, so we'd rather have even this small operation happen during training instead of at inference time.
### Batch Normalization
**Batch Normalization** or Batchnorm was first introduced in a [2015 paper](https://arxiv.org/pdf/1502.03167.pdf). A batchnorm layers computes batch statistics and scales its inputs using these statistics. By doing so, Batchnorm improves the convergence time of neural networks. 
Similarly to Dropout, Batchnorm behaves differently during training and testing. During training, this layer calculates an **exponential moving average** of batch statistics. During testing, these statistics are used instead of the batch statistics from the test batches.
