# Solution: Image Classification with Feedforward NNs

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=LcHWJl9CZJQ)

## Summary

**Neural Network Implementation with TensorFlow Keras API**
===========================================================

This README file summarizes the key concepts and practical steps involved in implementing a neural network from scratch using the TensorFlow Keras API.

### Key Concepts

* **Flattened layer**: A type of layer that transforms input data into a vector, suitable for use in neural networks.
* **ReLU activation function**: A popular choice for hidden layers, which introduces non-linearity to the model and helps with feature learning.
* **Dense layer**: A type of layer that applies a linear transformation to the input data, often used as output layers or for classification tasks.
* **One-hot encoding**: A technique used to convert categorical labels into numerical representations, suitable for use in neural networks.
* **Categorical cross-entropy loss**: A type of loss function used when dealing with multi-class classification problems, where the classes are mutually exclusive.
* **Adam optimizer**: A popular choice for optimizing neural network weights, which adapts learning rates based on the magnitude of weight updates.

### Practical Notes

When implementing a neural network from scratch using TensorFlow Keras API:

* Use a flattened layer to transform input images into vectors.
* Design a small network with one hidden layer and use ReLU activation.
* Set up output layers with dense layers, specifying the number of neurons based on the number of classes in your dataset.
* Compile the model using Adam optimizer and categorical cross-entropy loss, setting `from_logits` to `True`.
* Monitor training progress by visualizing loss and accuracy curves, looking for signs of over-fitting or under-fitting.

Note: This implementation is a good introduction to model selection and highlights the importance of carefully tuning hyperparameters to achieve optimal performance.

## Transcript

In this exercise, you were asked to implement your first neural network from scratch using the TensorFlow Keras API. I am using the TensorFlow Keras sequential class to create this model. Because our input is an image, I'm using a flattened layer to turn it into a vector. I decided to create a small network with only one hidden layer. This layer has 128 neurons and uses a ReLU activation.

My last layer is a dense layer of 43 neurons because our dataset has 43 classes, and I'm not using any activation for this layer. When compiling the model, I'm using the Adam optimizer with the default parameters. Because our dataset is outputting labels as integer instead of one-hot vector, I am using this pulse categorical cross-entropy loss. Because I did not use a softmax activation for the last layer of my network, I am setting the from logits arguments to true. I'm using the accuracy as the metrics to display for my model.

Finally, I can run model that fit to train my model, and a display function will show the loss and metrics. I'm training my model for tiny parks and I'm visualizing the loss and accuracy. From the decreasing loss, I can detect that my model is training correctly. However, I can see that the loss has not reached a plateau, meaning that I can probably train for more epochs. I'm observing a similar behavior for the accuracy while both training and validation accuracy do not reach a plateau.

Moreover, I can see that the validation accuracy is slightly under the train accuracy after 10 epochs, which may be the sign of over-fitting. This exercise is hopefully a good introduction to model selection. By now, you have realized how many parameters can be tweaked and how complicated it can be to train a model even on a simple dataset such as the traffic sign dataset.

## Additional Content

## Solution: Image Classification with Feedforward NNs
```python
import argparse

import tensorflow as tf
from tensorflow import keras

from utils import get_datasets, get_module_logger, display_metrics


def create_network():
    """ output a keras model """
    model = tf.keras.Sequential([
        tf.keras.layers.Flatten(input_shape=(32, 32, 3)),
        tf.keras.layers.Dense(128, activation='relu'),
        tf.keras.layers.Dense(43)])
    return model


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
- [Basic Image Classification](https://www.tensorflow.org/tutorials/keras/classification)
