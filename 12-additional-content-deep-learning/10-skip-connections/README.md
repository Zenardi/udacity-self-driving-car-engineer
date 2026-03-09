# Skip Connections

> Part of: **Fully Convolutional Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=JUYLA5PWzo0)

## Summary

**Summary of Skip Connections in Convolutional Networks**

Skip connections are a technique used to retain information in convolutional neural networks (CNNs) while using encoding layers. By connecting the output of one layer to a non-adjacent layer, skip connections allow the network to use information from multiple resolutions, resulting in more precise segmentation decisions.

**Key Concepts**

* **Convolutional Encoding**: Convolutions can narrow down the scope by focusing on specific details and losing the bigger picture.
* **Skip Connections**: Connecting the output of one layer to a non-adjacent layer to retain information.
* **Element-wise Addition**: Combining the output of two layers using element-wise addition operation.
* **Resolution**: The level of detail or scale at which an image is processed.

**Practical Notes**

To implement skip connections, you can combine the output of a pooling layer with the current layer's output using element-wise addition. This allows the network to use information from multiple resolutions and make more precise segmentation decisions. For example, comparing the FCN-8 architecture (with two skip connections) to the FCN-32 architecture (with zero skip connections) demonstrates the effectiveness of skip connections in improving segmentation performance.

## Transcript

<v English>The third special technique that fully</v> <v English>convolution on networks use is the skip connection.</v> <v English>One effect of convolutions or encoding in general is you narrow down</v> <v English>the scope by looking closely at some picture and lose the bigger picture as a result.</v> <v English>So even if we were to decode the output of the encoder back to the original image size,</v> <v English>some information has been lost.</v> <v English>Skip connections are a way of retaining the information easily.</v> <v English>The way skip connection work is by connecting</v> <v English>the output of one layer to a non-adjacent layer.</v> <v English>Here, the output of the pooling layer from the encoders combine with</v> <v English>the current layers output using the element-wise addition operation.</v> <v English>The result is bent into the next layer.</v> <v English>These skip connections allow the network to use information from multiple resolutions.</v> <v English>As a result, the network is able to make more precise segmentation decisions.</v> <v English>This is empirically shown in the following comparison</v> <v English>between the FCN-8 architecture which has</v> <v English>two skip connections and the FCN-32 architecture which has zero skip connections.</v>
