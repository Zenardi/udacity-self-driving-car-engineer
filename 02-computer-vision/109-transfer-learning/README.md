# Transfer Learning

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Od9EU9QeWKI)

## Summary

**Transfer Learning: Leverage Pre-Trained Models for Smaller Data Sets**
====================================================================

Transfer learning is a technique that allows us to use pre-trained models on smaller data sets, reducing the need for large amounts of labeled data. This approach leverages the properties of convolutional neural networks (CNNs) as feature extractors.

**Key Concepts**
---------------

* **Convolutional Neural Networks (CNNs)**: CNNs act as feature extractors, where shallower layers learn general features like lines or edges, and deeper layers learn more specialized features.
* **Transfer Learning**: Transfer learning uses the weights of a network trained on another data set to initialize our own network, reducing the need for large amounts of labeled data.
* **Fine Tuning**: Fine tuning involves retraining the pre-trained model on our specific data set, either by retraining all layers or just the classifier.
* **Data Agnostic Features**: The features learned in the shallow layer are useful across different data sets and can be leveraged through transfer learning.

**Practical Notes**
-------------------

When implementing transfer learning, you'll typically use pre-trained models like ImageNet weights as a starting point. You can then fine tune these models by retraining all layers or just the classifier, depending on your specific needs. This approach is particularly useful when working with smaller data sets, allowing you to leverage the power of deep neural networks without requiring large amounts of labeled data.

## Transcript

I previously said that deep learning requires a lot of data. Well, this is not entirely true. Thanks to transfer learning, we can use deep learning models on smaller data set. What is transfer learning? Transfer learning leverages a very cool properties of convolutional neural network.

As we mentioned earlier, covenants act as feature extractors. The shallower layer of a convolutional neural network learn general features such as lines or edges. Whereas deeper layers learn more specialized features. These features learned in the shallow layer are data agnostic and should be useful for an entire different data set than the one that network was trained on. This is exactly what transfer learning is.

Instead of using randomly initialized weight, we're going to use the weights of a network trained on another data set. In practice, it means that we are almost never training a network from scratch, but instead initializing our network with ImageNet weights, for example. In my many years training deep neural networks, I have trained very few neural networks from scratch. Instead, we'll do something called fine tuning. There are many different ways to perform fine tuning.

For example, we can decide to retrain every single layer of the network. We can also decide to just retrain the classifier and not the feature extractor. You will have a chance to experiment with transfer learning and fine tuning for the final project. Transfer learning is a very powerful ID as it overcomes some of the challenges of training deep neural networks.

## Images

![Four Cases When Using Transfer Learning](images/02-guide-how-transfer-learning-v3-01.png)
*Four Cases When Using Transfer Learning*

![General Overview of a Neural Network](images/02-guide-how-transfer-learning-v3-02.png)
*General Overview of a Neural Network*

![Case 1: Small Data Set with Similar Data](images/02-guide-how-transfer-learning-v3-03.png)
*Case 1: Small Data Set with Similar Data*

![Neural Network with Small Data Set, Similar Data](images/02-guide-how-transfer-learning-v3-04.png)
*Neural Network with Small Data Set, Similar Data*

![Case 2: Small Data Set, Different Data](images/02-guide-how-transfer-learning-v3-05.png)
*Case 2: Small Data Set, Different Data*

![Neural Network with Small Data Set, Different Data](images/02-guide-how-transfer-learning-v3-06.png)
*Neural Network with Small Data Set, Different Data*

![Case 3: Large Data Set, Similar Data](images/02-guide-how-transfer-learning-v3-07.png)
*Case 3: Large Data Set, Similar Data*

![Neural Network with Large Data Set, Similar Data](images/02-guide-how-transfer-learning-v3-08.png)
*Neural Network with Large Data Set, Similar Data*

![Case 4: Large Data Set, Different Data](images/02-guide-how-transfer-learning-v3-09.png)
*Case 4: Large Data Set, Different Data*

![Neural Network with Large Data Set, Different Data](images/02-guide-how-transfer-learning-v3-10.png)
*Neural Network with Large Data Set, Different Data*

## Additional Content

## Transfer Learning
### The Four Main Cases When Using Transfer Learning

Transfer learning involves taking a pre-trained neural network and adapting the neural network to a new, different data set. 

Depending on both:

* the size of the new data set, and
* the similarity of the new data set to the original data set

the approach for using transfer learning will be different. There are four main cases:

1. new data set is small, new data is similar to original training data
1. new data set is small, new data is different from original training data
1. new data set is large, new data is similar to original training data
1. new data set is large, new data is different from original training data
A large data set might have one million images. A small data could have two-thousand images. The dividing line between a large data set and small data set is somewhat subjective. Overfitting is a concern when using transfer learning with a small data set. 

Images of dogs and images of wolves would be considered similar; the images would share common characteristics. A data set of flower images would be different from a data set of dog images. 

Each of the four transfer learning cases has its own approach. In the following sections, we will look at each case one by one.
### Demonstration Network

To explain how each situation works, we will start with a generic pre-trained convolutional neural network and explain how to adjust the network for each case. Our example network contains three convolutional layers and three fully connected layers:
Here is an generalized overview of what the convolutional neural network does: 

* the first layer will detect edges in the image
* the second layer will detect shapes
* the third convolutional layer detects higher level features

Each transfer learning case will use the pre-trained convolutional neural network in a different way.
### Case 1: Small Data Set, Similar Data
If the new data set is small and similar to the original training data:

* slice off the end of the neural network
* add a new fully connected layer that matches the number of classes in the new data set
* randomize the weights of the new fully connected layer; freeze all the weights from the pre-trained network
* train the network to update the weights of the new fully connected layer

To avoid overfitting on the small data set, the weights of the original network will be held constant rather than re-training the weights. 

Since the data sets are similar, images from each data set will have similar higher level features. Therefore most or all of the pre-trained neural network layers already contain relevant information about the new data set and should be kept.

Here's how to visualize this approach:
### Case 2: Small Data Set, Different Data
If the new data set is small and different from the original training data:

* slice off most of the pre-trained layers near the beginning of the network
* add to the remaining pre-trained layers a new fully connected layer that matches the number of classes in the new data set
* randomize the weights of the new fully connected layer; freeze all the weights from the pre-trained network
* train the network to update the weights of the new fully connected layer

Because the data set is small, overfitting is still a concern. To combat overfitting, the weights of the original neural network will be held constant, like in the first case.

But the original training set and the new data set do not share higher level features. In this case, the new network will only use the layers containing lower level features.

Here is how to visualize this approach:
### Case 3: Large Data Set, Similar Data
If the new data set is large and similar to the original training data:

* remove the last fully connected layer and replace with a layer matching the number of classes in the new data set
* randomly initialize the weights in the new fully connected layer
* initialize the rest of the weights using the pre-trained weights 
* re-train the entire neural network

Overfitting is not as much of a concern when training on a large data set; therefore, you can re-train all of the weights.

Because the original training set and the new data set share higher level features, the entire neural network is used as well.

Here is how to visualize this approach:
### Case 4: Large Data Set, Different Data
If the new data set is large and different from the original training data:

* remove the last fully connected layer and replace with a layer matching the number of classes in the new data set
* retrain the network from scratch with randomly initialized weights
* alternatively, you could just use the same strategy as the "large and similar" data case

Even though the data set is different from the training data, initializing the weights from the pre-trained network might make training faster. So this case is exactly the same as the case with a large, similar data set.

If using the pre-trained network as a starting point does not produce a successful model, another option is to randomly initialize the convolutional neural network weights and train the network from scratch.

Here is how to visualize this approach:
## Extra Resources
- [Transfer Learning and Fine Tuning](https://www.tensorflow.org/tutorials/images/transfer_learning)
