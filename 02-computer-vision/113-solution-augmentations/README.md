# Solution: Augmentations

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=vQSNjzhKOxE)

## Summary

**Traffic Sign Classification with Albumentation Augmentation**
===========================================================

This project demonstrates how to add albumentation augmentation to the TensorFlow data loading process for traffic sign classification. The goal is to enhance the dataset by applying relevant transformations, such as rotation and blurring.

### Key Concepts

* **Albumentation**: A library used for image augmentation in deep learning models.
* **Image Augmentation**: Techniques applied to images to increase diversity and robustness of the model, including:
	+ Rotation: rotating images to simulate different angles
	+ Blurring: applying a blur effect to images to simulate varying levels of focus
* **TensorFlow's `image_dataset_from_directory` class**: used to load image datasets from directories.
* **Batching**: grouping data into batches for efficient processing.

### Practical Notes

To implement albumentation augmentation in TensorFlow, follow these steps:

1. Import the necessary libraries: `albumentations`, `tensorflow`.
2. Define two functions:
	+ One function applies rotation and blurring augmentations to an image.
	+ The other function is a wrapper for TensorFlow's `numpy` function, taking the augmentation function and image as inputs.
3. Use `image_dataset_from_directory` with a batch size of one to load the dataset.
4. Apply the augmentation using the `map` method and batch the data using the `batch` method.
5. Visualize the output of the dataset to ensure the augmentations are effective.

Remember to adjust the parameters of the augmentations (e.g., rotation angle, blur value) to optimize their impact on the model's performance.

## Transcript

In this exercise, you are asked to add albumentation augmentation to TensorFlow data loading process. You had the freedom to select any augmentation as long as they were relevant to the traffic sign classification problem. I chose the rotation and blurring augmentation. Then I implemented two functions. The first one takes an image as a NumPy array and apply the augmentation.

Because the input array has four dimensions, I squeeze the first one. I then apply normalization and cast the Numpy array back to tensor. The second function is a simple wrapper of the TensorFlow NumPy function. This function is going to take out augmentation function as well as the image as inputs. Let's look at the main code now.

We are using the image_dataset_from_directory TensorFlow class that we have used in the past. However, this time we're using a batch_size of one. It means that when we are iterating through this dataset, the elements will have a first dimension equal to one hence the squeezing that I used previously. I'm using the map method of the data set as well as the batch method to apply the augmentation and batch the data. Finally, I wrote a small loop to display the output of my datasets.

Let's look at this figure together. On this figure, we can see a sample of ten images from our dataset. A lot of the input, actually very blurry, which mean that the blur value that I used for my augmentation is probably a little too high. We can see that some of these traffic sign are rotated. The rotation angle is very relevant to the traffic sign classification problem.

To this augmentation probably has the right parameter. It is critical that you visualize your data before it is being fed to the neural network. At this can be the source of many bugs.

## Additional Content

## Solution: Augmentations
`augmentations.py`

```python
import argparse
from functools import partial

import albumentations as A
import matplotlib.pyplot as plt
import numpy as np
import tensorflow as tf
from tensorflow.keras.preprocessing import image_dataset_from_directory

from utils import plot_batch


transforms = A.Compose([A.Rotate(limit=30, p=0.5),
                        A.Blur(blur_limit=5, p=0.5)])


def aug_fn(image):
    """ augment an image """
    aug_data = transforms(image=image.squeeze())
    aug_img = aug_data["image"]
    aug_img = tf.cast(aug_img/255.0, tf.float32)
    return aug_img


def process_data(image, label):
    """ wrapper function to apply augmentation """
    aug_img = tf.numpy_function(func=aug_fn, inp=[image], Tout=tf.float32)
    return aug_img, label


if __name__ == '__main__':
    parser = argparse.ArgumentParser(description='Augment dataset')
    parser.add_argument('-d', '--imdir', required=True, type=str,
                        help='data directory')
    args = parser.parse_args()    

    dataset = image_dataset_from_directory(args.imdir, 
                                           image_size=(32, 32),
                                           validation_split=0.1,
                                           subset='training',
                                           seed=123,
                                           batch_size=1)
    dataset = dataset.map(process_data).batch(256)
    for X,Y in dataset:
        batch_np = X.numpy()
        plot_batch(batch_np)
        break
```
## Extra Resources
- [Data Augmentation](https://www.tensorflow.org/tutorials/images/data_augmentation)
