# Solution: Training Tips #2

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=W8hqoZcme1I)

## Summary

**Learning Rate Annealing Strategies**
=====================================

This project focuses on experimenting with different annealing strategies to improve model performance. Two specific techniques are explored: exponential decay annealing and step annealing.

**Key Concepts**
---------------

* **Exponential Decay Annealing**: a strategy where the learning rate decreases exponentially over time, using a pre-implemented scheduler in TensorFlow.
	+ Key formula: `learning_rate = initial_learning_rate * (decay_rate ^ epoch)`
	+ Example parameters: decay rate of 0.95 and decay steps set to 100
* **Step Decay Annealing**: a strategy where the learning rate is divided by two at regular intervals, such as every 10 epochs.
	+ Key concept: using modular arithmetic to check if the epoch is a multiple of 10
	+ Example parameters: dividing the learning rate by two every 10 epochs

**Practical Notes**
-----------------

* To implement exponential decay annealing, use TensorFlow's pre-implemented scheduler with an aggressive decay strategy (e.g., decay rate of 0.95 and decay steps set to 100).
* For step decay annealing, create a custom learning rate scheduler callback that takes your function as input.
* When implementing annealing strategies, start by experimenting with constant learning rates before trying different annealing techniques.
* Visualize the learning rate decay function after training to monitor its effectiveness.

## Transcript

In this exercise, you are asked to experiment with different annealing strategies. In particular, you were asked to implement exponential decay annealing and step annealing. For exponential decay, we can use the pre implemented scheduler of TensorFlow. I'm going to use a pretty aggressive decay strategy, using a decay rate of 0.95 and setting decay steps to 100. I am setting the scheduler as the input learning rate to my optimizer.

Finally, I can compile my model and run the training. After 50 epoch, we can visualize the learning rate. We see the exponential shape of the learning rate function. Our model is over fitting a lot, so it is worth experimenting with different values of the hyperparameters. Next, I implemented the step decay.

We were asked to implement a decay such that the learning rate was divided by two, every 10 epochs of training. I'm using the modular function to check if the epoch is a multiple of 10. We have to work slightly differently here and use the learning rate scheduler callback that takes our custom function as input. We compile the model using an optimizer initialized with the chosen learning rates. We can also train our model for 50 epoch and visualize the learning rate decay function.

Our model is also over fitting a lot. On the right, we can see the step shape of the learning rate function. Learning rate annealing is a very useful strategy to improve your model performances. However, you should first experiment with constant learning rates before trying different annealing strategies. I'm personally a big fan of the step decay strategy and I hope you will find it useful as well.

## Additional Content

## Solution: Training Tips #2
```python
import argparse
import logging

import tensorflow as tf
from tensorflow.keras.optimizers import schedules
from utils import get_datasets, get_module_logger, display_metrics, \
    create_network, LrLogger


def exponential_decay(model, callbacks, lr=0.001):
    """ use exponential decay """
    # add decay
    scheduler = schedules.ExponentialDecay(lr, decay_steps=100, decay_rate=0.95)
    optimizer = tf.keras.optimizers.Adam(learning_rate=scheduler)

    # compile model
    model.compile(optimizer=optimizer,
                loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
                metrics=['accuracy'])
    
    return model, callbacks


def step_decay(model, callbacks, lr=0.001):
    """ create custom decay using learning rate scheduler """
    def scheduler(epoch, lr):
        if epoch % 10 == 0 and epoch > 0:
            lr /= 2
        return lr 
    callbacks.append(tf.keras.callbacks.LearningRateScheduler(scheduler))

    # create optimizer
    optimizer = tf.keras.optimizers.Adam(learning_rate=lr)

    # compile model
    model.compile(optimizer=optimizer,
                loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
                metrics=['accuracy'])
    
    return model, callbacks


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
    logger = LrLogger()
    callbacks = [logger]

    model = create_network()

    # model, callbacks = exponential_decay(model, callbacks)
    model, callbacks = step_decay(model, callbacks)

    history = model.fit(x=train_dataset, 
                        epochs=args.epochs, 
                        validation_data=val_dataset,
                        callbacks=callbacks)
    display_metrics(history)
```
