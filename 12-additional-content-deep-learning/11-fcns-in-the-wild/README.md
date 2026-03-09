# FCNs In The Wild

> Part of: **Fully Convolutional Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=q9wTd53-hsw)

## Summary

**Using FCNs in Practice**
==========================

This project focuses on applying **Fully Convolutional Networks (FCNs)** in real-world scenarios. An FCN is a type of neural network composed of two main components: the **encoder** and the **decoder**.

### Key Concepts
* **Encoder**: extracts features from an input image that will be used by the decoder.
* **Decoder**: uses transposed convolutional layers to upsample the image and produce the output.
* **Transfer Learning**: a technique borrowed from FCNs, where pre-trained models (e.g. VGG and ResNet) are used as encoders.
* **One-by-One Convolutional Layer Conversion**: a special technique applied to complete the encoder portion of the FCN.
* **Transposed Convolutional Layers**: used by the decoder to upsample the image.
* **Skip Connections**: added via a third special technique, which can help improve model performance but must be used carefully to avoid increasing the model size.

### Practical Notes
When building an FCN, consider using pre-trained models (e.g. VGG-16) as encoders and apply one-by-one convolutional layer conversion to complete the encoder portion. The decoder uses transposed convolutional layers to upsample the image, and skip connections can be added via a third special technique. Be cautious not to add too many skip connections, as this can lead to an explosion in model size.

**Example Code**
```python
# Import necessary libraries
import torch
import torchvision

# Load pre-trained VGG-16 model as encoder
encoder = torchvision.models.vgg16(pretrained=True)

# Apply one-by-one convolutional layer conversion to complete the encoder portion
encoder = one_by_one_convolutional_layer_conversion(encoder)
```
Note: The example code is a simplified representation and may not be directly executable.

## Transcript

<v English>Let's take a few moments to talk about using FCNs in practice.</v> <v English>An FCN has two components,</v> <v English>the encoder and the decoder.</v> <v English>We mentioned that encoder extracts features that will later be used by the decoder.</v> <v English>This may sound familiar to transfer learning, and it is.</v> <v English>In fact, we can borrow techniques from transfer</v> <v English>learning to accelerate the training of our FCNs.</v> <v English>It's common for the encoder to be pre-trained on ImageNet.</v> <v English>VGG and ResNet are popular choices, as examples.</v> <v English>By applying the first special technique of one by one convolutional layer conversion,</v> <v English>we can complete the encoder portion of the FCN.</v> <v English>The encoder is followed by the decoder,</v> <v English>which uses a second special technique of</v> <v English>transposed convolutional layers to upsample the image.</v> <v English>Then the skip connection via the third special technique is added.</v> <v English>Be careful not to add too many skip connections, though.</v> <v English>It can lead to the explosion in the size of your model.</v> <v English>For example, when using VGG-16 as the encoder,</v> <v English>only the third and the fourth pooling layers are typically used for skip connections.</v> <v English>After all that, we can now train the model end to end.</v>
