# Deep Learning Engineer

> Part of: **Autonomous Systems Interview Practice**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=EcIwpFM-UYQ)

## Summary

**Semantic Segmentation: A Deep Learning Approach**
=====================================================

This README file provides a summary of the key concepts, formulas, and techniques introduced in the Udacity lesson on semantic segmentation.

### Key Concepts

* **Semantic Segmentation**: The process of assigning a category or label to each pixel in an image.
* **Fully Convolutional Neural Networks (FCNNs)**: A type of neural network architecture used for image classification tasks. In this context, FCNNs are composed of an encoder and a decoder.
* **Encoder-Decoder Architecture**: The encoder takes the input image and reduces its spatial dimensions, while the decoder upsamples the output to match the original image size.
* **Transfer Learning**: Using pre-trained models (e.g., VGG16) as a starting point for training a new model on a specific task.
* **D-Convolutional Layers**: A type of convolutional layer used for upsampling and downsampling operations in FCNNs.
* **Softmax Function**: A mathematical function that converts raw output values into probabilities, ensuring they sum up to 1.
* **Cross Entropy Loss Function**: A log loss function used to calculate the difference between predicted probabilities and actual labels.

### Practical Notes

To implement semantic segmentation using a fully convolutional neural network:

1. Use a pre-trained model (e.g., VGG16) as an encoder.
2. Add D-convolutional layers for upsampling and downsampling operations.
3. Use softmax to convert raw output values into probabilities.
4. Apply cross entropy loss function to calculate the difference between predicted probabilities and actual labels.
5. Train the network using gradient descent and backpropagation.

Note: This summary provides a high-level overview of the key concepts and techniques introduced in the lesson. For more detailed information, please refer to the original transcript or additional resources provided by Udacity.

## Transcript

<v English>Well, I&#39;m glad to have you in here today Aaron for our deep learning engineer position.</v> <v English>To get started, I&#39;d like to ask you a question</v> <v English>actually in deep learning, are you ready to go?</v> <v English>Yeah, sure let&#39;s do it.</v> <v English>All right. So, the first thing I&#39;d like to ask you</v> <v English>is just to explain the concept of semantic segmentation.</v> <v English>Oh sure. I&#39;ve done some work on semantic segmentation.</v> <v English>Awesome.</v> <v English>I&#39;ve generated some really cool results.</v> <v English>Nice.</v> <v English>So, I can tell you what I&#39;ve done before is I&#39;ve used a fully convolution neural network,</v> <v English>and it&#39;s made up of an encoder and a decoder.</v> <v English>Your encoder, you can actually use transfer learning.</v> <v English>So, it&#39;s just a convolution neural network.</v> <v English>You can use a pre-trained one like VGG</v> <v English>16 and then you can do some pretty interesting techniques.</v> <v English>So, you could use one by</v> <v English>one convolution to bring it to a decoder and this is where things get really</v> <v English>interesting because now you&#39;re using something called D</v> <v English>convolutional layers to actually upsample the results.</v> <v English>So, the result that you end up getting is the same dimensions as your input.</v> <v English>So, if we&#39;re looking at trying to figure</v> <v English>out which pixels in an image belong to the road and which ones don&#39;t,</v> <v English>this is where a fully convolution neural network will do great,</v> <v English>because it&#39;ll actually provide us</v> <v English>which of those pixels are actually the road and which ones aren&#39;t.</v> <v English>So, it&#39;s looking at the category of them.</v> <v English>In order to do this,</v> <v English>it&#39;s actually going to start out quite random when you feed in your image.</v> <v English>It&#39;s just going to look like a lot of noise.</v> <v English>A lot of pixels are going to be various values.</v> <v English>So, we can actually have a label.</v> <v English>So we want to do some training here.</v> <v English>So this is our input data and then this is our label.</v> <v English>So this is hand annotated.</v> <v English>Okay.</v> <v English>So here, pixels that are one,</v> <v English>belong to the road and ones that are zeros are non-road.</v> <v English>So, this is what we want it to end up looking like.</v> <v English>If we want to get from here to here,</v> <v English>we&#39;re actually going to want to do some training.</v> <v English>So, we want to have a good loss function in order to do this.</v> <v English>Great. What kind of loss function do you think you&#39;ll use?</v> <v English>So, you can actually use a loss function that&#39;s quite similar to when you&#39;re</v> <v English>just doing categories for different images.</v> <v English>You can use softmax and then do cross entropy and what that looks like is at first,</v> <v English>this is going to be quite random.</v> <v English>So, if we just grab a pixel on here,</v> <v English>so there&#39;s different categories that we&#39;re dealing with.</v> <v English>So, let&#39;s say that we grabbed this one that&#39;s actually a part of the road.</v> <v English>So, we can have non-road and we can have road</v> <v English>and it is a probability that&#39;s going to sum up to one.</v> <v English>First, our network is going to produce something that doesn&#39;t sum up to one,</v> <v English>it&#39;s going to be quite random.</v> <v English>So, maybe we have negative 0.23 and we have 105.</v> <v English>Well, softmax is going to be able to take this and make it into a probability.</v> <v English>It ends up looking something like this function where we can use</v> <v English>e and then we can just sum over those different values.</v> <v English>So here we have two different values and we can use that.</v> <v English>Make sure that it sums up to one.</v> <v English>Okay.</v> <v English>Once it actually sums up to one,</v> <v English>we can use cross entropy and that&#39;s a log loss function and it</v> <v English>looks something like this where we have this negative summation and then we have,</v> <v English>let&#39;s say, is L log S where L is</v> <v English>part of the label and S are the values that we&#39;re getting from the softmax.</v> <v English>Essentially, what that&#39;s doing is if it&#39;s actually matching up really well,</v> <v English>it&#39;s going to be zero for the loss.</v> <v English>If they&#39;re wildly off,</v> <v English>it&#39;s going to be very large and [inaudible] , large loss.</v> <v English>So, once we actually have our loss function and this is using gradient descent and</v> <v English>following that derivative to minimize</v> <v English>the loss and then slowly over time with that training,</v> <v English>we can actually get our results that are quite noisy in random.</v> <v English>They actually look like our labels.</v> <v English>Okay. That covers everything I had on this topic anyway.</v> <v English>Let&#39;s go ahead and move on to the next one.</v> <v English>Sure.</v>
