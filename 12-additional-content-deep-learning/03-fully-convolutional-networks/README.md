# Fully Convolutional Networks

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=_Lh2ozg5yTs)

## Summary

**Fully Convolutional Networks (FCNs) for Semantic Segmentation**
===========================================================

This project focuses on implementing Fully Convolutional Networks (FCNs), a type of neural network architecture that has achieved state-of-the-art results in computer vision tasks, particularly semantic segmentation. FCNs utilize three key techniques: replacing fully connected layers with convolutional layers, up-sampling through transposed convolutional layers, and skip connections.

### Key Concepts

* **Fully Convolutional Networks (FCNs)**: A type of neural network architecture that replaces fully connected layers with convolutional layers.
* **Transposed Convolutional Layers**: Used for up-sampling the output of the encoder to match the original image size.
* **Skip Connections**: Allow the network to use information from multiple resolution scales, enabling more precise segmentation decisions.
* **Encoder-Decoder Structure**: FCNs typically consist of two parts: an encoder that extracts features and a decoder that up-scales the output.

### Practical Notes

To implement FCNs for semantic segmentation, you will need to:

* Replace fully connected layers with convolutional layers in your network architecture
* Use transposed convolutional layers to up-sample the output of the encoder
* Implement skip connections to leverage information from multiple resolution scales
* Train and test your model on a dataset suitable for semantic segmentation tasks

Note: This summary provides an overview of the key concepts and practical steps involved in implementing FCNs. The actual implementation details may vary depending on the specific requirements of your project.

## Transcript

<v English>Fully Convolutional Networks have achieved state</v> <v English>of the art results in computer vision tasks,</v> <v English>such as semantic segmentation.</v> <v English>FCNs take advantage of three special techniques; one,</v> <v English>replace fully connected layers with one by one convolutional layers, two,</v> <v English>up-sampling through the use of transposed convolutional layers, three, skip connections.</v> <v English>These skip connections allow the network to</v> <v English>use information from multiple resolution scales.</v> <v English>As a result the network is able to make more precise segmentation decisions.</v> <v English>We will discuss these techniques in greater detail shortly.</v> <v English>Structurally an FCN is usually comprised of two parts; encoder and decoder.</v> <v English>The encoder is a series of convolutional layers like VGG and ResNet.</v> <v English>The goal of the encoder is to extract features from the image.</v> <v English>The decoder up-scales the output of the encoder</v> <v English>such that it's the same size as the original image.</v> <v English>Thus, it results in segmentation or prediction</v> <v English>of each individual pixel in the original image.</v>
