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

Well, I'm glad to have you in here today Aaron for our deep learning engineer position. To get started, I'd like to ask you a question actually in deep learning, are you ready to go? Yeah, sure let's do it. All right. So, the first thing I'd like to ask you is just to explain the concept of semantic segmentation. Oh sure. I've done some work on semantic segmentation. Awesome. I've generated some really cool results. Nice. So, I can tell you what I've done before is I've used a fully convolution neural network, and it's made up of an encoder and a decoder. Your encoder, you can actually use transfer learning. So, it's just a convolution neural network. You can use a pre-trained one like VGG 16 and then you can do some pretty interesting techniques. So, you could use one by one convolution to bring it to a decoder and this is where things get really interesting because now you're using something called D convolutional layers to actually upsample the results. So, the result that you end up getting is the same dimensions as your input. So, if we're looking at trying to figure out which pixels in an image belong to the road and which ones don't, this is where a fully convolution neural network will do great, because it'll actually provide us which of those pixels are actually the road and which ones aren't. So, it's looking at the category of them. In order to do this, it's actually going to start out quite random when you feed in your image. It's just going to look like a lot of noise. A lot of pixels are going to be various values. So, we can actually have a label. So we want to do some training here. So this is our input data and then this is our label. So this is hand annotated. Okay. So here, pixels that are one, belong to the road and ones that are zeros are non-road. So, this is what we want it to end up looking like. If we want to get from here to here, we're actually going to want to do some training. So, we want to have a good loss function in order to do this. Great. What kind of loss function do you think you'll use? So, you can actually use a loss function that's quite similar to when you're just doing categories for different images. You can use softmax and then do cross entropy and what that looks like is at first, this is going to be quite random. So, if we just grab a pixel on here, so there's different categories that we're dealing with. So, let's say that we grabbed this one that's actually a part of the road. So, we can have non-road and we can have road and it is a probability that's going to sum up to one. First, our network is going to produce something that doesn't sum up to one, it's going to be quite random. So, maybe we have negative 0.23 and we have 105. Well, softmax is going to be able to take this and make it into a probability. It ends up looking something like this function where we can use e and then we can just sum over those different values. So here we have two different values and we can use that. Make sure that it sums up to one. Okay. Once it actually sums up to one, we can use cross entropy and that's a log loss function and it looks something like this where we have this negative summation and then we have, let's say, is L log S where L is part of the label and S are the values that we're getting from the softmax. Essentially, what that's doing is if it's actually matching up really well, it's going to be zero for the loss. If they're wildly off, it's going to be very large and [inaudible] , large loss. So, once we actually have our loss function and this is using gradient descent and following that derivative to minimize the loss and then slowly over time with that training, we can actually get our results that are quite noisy in random. They actually look like our labels. Okay. That covers everything I had on this topic anyway. Let's go ahead and move on to the next one. Sure.
