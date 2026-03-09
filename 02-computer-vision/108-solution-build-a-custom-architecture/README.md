# Solution: Build a Custom Architecture

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=NPJcnXqLUaE)

## Summary

**CurveNet Implementation using TensorFlow Keras API**
=====================================================

This README file summarizes the key concepts and practical steps involved in implementing a CurveNet using the TensorFlow Keras API.

### Key Concepts

* **Convolutional Layers**: Used to extract features from images, with three by three filters and strides of one.
* **MaxPooling Layers**: Used to aggregate information without losing too much, with two-by-two filters and a stride of two.
* **Fully-Connected Layers**: Used as the classifier, with ReLU activation apart from the last layer which does not have an activation.
* **Adam Optimizer**: Used with default parameters for training the model.
* **Logits vs. Probability Vector**: The loss function used expects logits, not probability vectors, so no activation is applied to the last layer.

### Practical Notes

* To implement a CurveNet using TensorFlow Keras API:
	+ Use two blocks of convolution and pooling layers.
	+ Specify the input shape for the first convolutional layer.
	+ Use three fully-connected layers with ReLU activation apart from the last one.
	+ Train the model for 10 epochs and visualize the loss and accuracy curves.
* Key takeaways from this exercise:
	+ CurveNets require more experimentation than feedforward neural networks due to their complex architecture design choices.
	+ Overfitting can occur if the model is not trained long enough or with sufficient data.

## Transcript

In this exercise, you were asked to implement your first CurveNet using the TensorFlow Keras API. For this exercise, I implemented a network inspired from [inaudible]. This network was originally developed to classify handwritten digits on small resolution images. Let's look at some of the design decision made here. We have two blocks of convolution and pooling layers.

I am using MaxPooling layers with two-by-two filters and a stride of two such that we aggregate information without losing too much. For the convolutional layers, I'm using three by three filters and the strides of one. For the first convolutional layer, I had to specify the input shape. The other input shapes in the network are automatically inferred. For the classifier, I use three fully-connected layer with relu activation apart from the last one that does not have an activation.

I'm not using an activation for the last layer because the loss function that I'm using expects the logits and not the probability vector. I'm using the Adam optimizer with the default parameters. After training my model for 10 epochs, I can visualize the loss and accuracy for both the training set and a validation set. So what can I infer from these curves? Well, by looking at the loss curves, I can tell that my model is not done converging as the training loss has not reached a plateau.

Looking at the accuracy curve, I can see that my model is doing a very good job at this task as the training accuracy is above 0.9. However, I can see that after 10 epochs, the validation accuracy is slightly under the training accuracy, meaning that my model is probably starting to over fit. With this exercise, you have now implemented your first CurveNet. Whereas for feedforward neural network the architecture design choices were limited to the number of layers and the number of neurons per layer, you can see now that CurveNets require a lot more experimentation.

## Additional Content

## Solution: Build a Custom Architecture
```python
import argparse
import logging

import tensorflow as tf
from tensorflow.keras.layers import Dense, Flatten, Conv2D, MaxPooling2D

from utils import get_datasets, get_module_logger, display_metrics


def create_network():
    net = tf.keras.models.Sequential()
    input_shape = [32, 32, 3]
    net.add(Conv2D(6, kernel_size=(3, 3), strides=(1, 1), activation='relu', 
                   input_shape=input_shape))
    net.add(MaxPooling2D(pool_size=(2, 2), strides=(2, 2)))
    net.add(Conv2D(16, kernel_size=(3, 3), strides=(1, 1), activation='relu'))   
    net.add(MaxPooling2D(pool_size=(2, 2), strides=(2, 2)))
    net.add(Flatten())
    net.add(Dense(120, activation='relu'))
    net.add(Dense(84, activation='relu'))
    net.add(Dense(43))
    return net


if __name__  == '__main__':
    logger = get_module_logger(__name__)
    parser = argparse.ArgumentParser(description='Download and process tf files')
    parser.add_argument('-d', '--imdir', required=True, type=str,
                        help='data directory')
    parser.add_argument('-e', '--epochs', default=10, type=int,
                        help='Number of epochs')
    args = parser.parse_args()    

    logger.info(f'Training for {args.epochs} epochs using {args.imdir} data')
    # get the datasets
    train_dataset, val_dataset = get_datasets(args.imdir)

    model = create_network()

    model.compile(optimizer='adam',
              loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
              metrics=['accuracy'])
    history = model.fit(x=train_dataset, 
                        epochs=args.epochs, 
                        validation_data=val_dataset)
    display_metrics(history)
```
## Extra Resources
- [Convolutional Neural Network](https://www.tensorflow.org/tutorials/images/cnn)
- [Image Classification](https://www.tensorflow.org/tutorials/images/classification)
