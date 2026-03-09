# Introduction to Deep Learning and Computer Vision

> Part of: **Introduction to Deep Learning for Computer Vision**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=D-1k64F_jps)

## Summary

**Machine Learning and Artificial Intelligence**
=====================================================

This summary provides a high-level overview of the key concepts introduced in this lesson on machine learning and artificial intelligence.

### Key Concepts

* **Artificial Intelligence (AI)**: A system is considered intelligent when it can learn from external data and use that knowledge to achieve specific tasks.
* **Machine Learning**: Unlike traditional AI, machine learning algorithms do not require explicit programming; instead, they learn from data through a process of training.
* **Deep Learning**: A subset of machine learning that uses neural networks with multiple layers to analyze raw data. Deep learning is particularly useful for working with unstructured data such as images and speech.
* **Supervised Learning**: A type of machine learning where the algorithm is trained on labeled data, meaning each example has a corresponding output or class label.
* **Unsupervised Learning**: A type of machine learning where the algorithm is trained on unlabeled data, requiring it to find patterns or structure in the data.

### Practical Notes

* To train a supervised learning algorithm, you need to gather and label a large dataset. This can be time-consuming and costly, especially for tasks that require detailed annotations.
* Deep learning algorithms often require large amounts of labeled data to achieve good performance.
* In this course, we will focus on supervised learning and use labeled datasets to train our machine learning models.

Note: The instructor provides examples of labeling tasks in the context of image classification (e.g., classifying images as containing a dog or not) and object detection. These examples illustrate the importance of accurate labeling for successful supervised learning.

## Transcript

Let's now talk about machine learning. But before we can understand what machine learning is, we need to take a step back and look at a broader concept, Artificial Intelligence. A system is defined as intelligent when it's able to learn from external data and use this knowledge to achieve specific task. You've been interacting with AI for a long time. For example, video games non playable characters, are a type of AI.

What differentiate machine learning from such a type of artificial intelligence is the necessity of being explicitly programmed. Let's consider a game of Tic-Tac-Toe example. Well, you could build an AI using a hard-coded set of rule, such as if my open-end text one corner, text the opposite corner. However, machine learning algorithm do not need such hard-coded rules and learn from data instead. To do so, we will have to gather data from previously played game and train an algorithm to learn from that data.

Let's now talk about deep learning, a subset of machine learning algorithm. While deep learning finds it foundation on neural network, a type of machine learning algorithm. The term deep learning illustrates the number of layers in such network. How is deep learning exactly different from machine learning? Well, one great thing about deep learning is the ability to work with raw data.

Whereas for machine learning, we sometimes need to handcraft features. Let's consider an example. We are trying to classify an image as containing a dog or not. Well, a machine learning approach will consist in building dog features such as the nose, or ears detectors and find these features in the image. Deep learning, however, we directly take the image and compute the most meaningful features to classify a dog.

It does come at a cost though, which is the amount of data required to train good deep learning algorithms. In this course, we are going to study a couple of machine learning algorithms, such as linear regression and logistic regression. But we will quickly shift to neural network and deep learning because they are the core of the self-driving car technology. In this course, we're going to focus on a specific class of machine learning problems, which is supervised learning. To use supervised learning, we need labeled data.

But what do I mean by that? Well, to train a machine learning algorithm, we need to give the algorithm example of data. But in the case of supervised learning, we also need to annotate or label that data. For example, let's say that you're trying to build a machine learning algorithm that classifies cats and dogs from images. To do so, you gather hundreds of images of both animals.

However, before you can use this data in your supervised learning approach, you need to associate a cat or dog label to each image in your data-set. In unsupervised learning, however, we can feed the algorithm directly the raw, unlabeled data. An example of such an algorithm would be a clustering algorithm. Where we try to group data in clusters by using shared features. What are the downsides of supervised learning?

Well, the labeling task can come at a great cost. Actually, with the deep learning revolution, some companies solely focus on labeling data for deep learning teams. Where some tasks like classification, where we attribute a single label to an image, do not require lengthy labeling process. Other task, such as object detection, may take much longer because we need to annotate every single object in the image. These schools will be entirely focusing on supervised learning.

But fear not, you will have access to labeled data-sets. Before we learn more about machine learning, I wanted to introduce some naming convention of supervised learning. Let's consider the task of classifying traffic signs. We're building a supervised learning algorithm to classify a traffic sign image. This image will be the input or input variable to our model.

We can also use the letter x to describe it, as well as the term observation. Our algorithm will predict a class using this image. In this case, the class is traffic lights ahead sign depending on whether this class has been predicted or annotated, we'll use different terms. We will use Ŷ or output variable in the case of prediction, for an annotation, we will use the term ground truth, label, or just the letter y. Keep in mind these definitions as those terms are going to frequently come back in later lessons.

## Additional Content

## Introduction to Deep Learning and Computer Vision
* **Artificial Intelligence (AI):**  a system that leverages information from its environment to make decisions. For example, a video game bot.
* **Machine Learning (ML):** an AI that does not need to be explicitly programmed, and instead learns from data. For example, a spam classification algorithm.
* **Deep Learning (DL):** a subset of ML algorithms that do not require handcrafted features and can work with raw data. For example, an object detection algorithm with a convolutional neural network.
### Supervised Learning
In this course, we will focus on **supervised learning**, where we use **annotated** data to train an algorithm. In supervised learning, we will define the following:
* Input variable /

$X$

/ Observation: the input data to the algorithm. For example, in spam classification, it would be an email.
* Ground truth /

$Y$

/ label: the known associated label with the input data. For example, a human created label describing the email as a spam or not.
* Output variable /

$\hat{Y}$

/ prediction: the model prediction given the input data. For example, the model predicts the input as being spam.
