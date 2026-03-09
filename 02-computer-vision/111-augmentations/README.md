# Augmentations

> Part of: **Image Classification with CNNs**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=0-PsNLi2jKc)

## Summary

**Data Augmentation: Enhancing Model Robustness through Data Transformation**
====================================================================================

**Summary**

Data augmentation is a technique used to increase the variability of a dataset by transforming input images at the pixel level. This approach helps improve model robustness by exposing the network to different scenarios and conditions that may not be present in the original training data.

**Key Concepts**

* **Data Augmentation**: A method for introducing more variability in a dataset by applying transformations to input images.
* **Pixel-level Transformation**: Data augmentation involves modifying individual pixels within an image, such as adding blur or rotation.
* **Geometric Operations**: Transformations like rotation, scaling, and flipping can be applied to images to simulate different scenarios.
* **Augmentation Parameters**: Each transformation has parameters that control its application, including `always_apply` (a boolean) and `p` (a float probability).
* **Albumentations Library**: A Python library for image augmentation that provides a range of transformations and allows for combining multiple augmentations.

**Practical Notes**

When applying data augmentation:

* Carefully curate augmentations to reflect real-world scenarios and conditions.
* Use Albumentations library to apply transformations, which can be combined using the `composed` function.
* Consider the format of bounding boxes when applying geometric transformations.
* Experiment with different augmentation parameters to find the optimal settings for your model.

Example code snippets from the lesson demonstrate how to use Albumentations to apply rotation, contrast change, and dropout augmentations to an image. The library also supports applying augmentations to images with bounding boxes, allowing for more realistic simulations of real-world scenarios.

## Transcript

As machinery engineer say, an algorithm is only as good as the data you fit it. To get good performances, you need good data. However, we learned that getting data might be expensive, difficult, or simply not possible. In many cases, you won't be able to get more data. Moreover, your data set might not contain enough variability to train a robust model.

Let's look at this training set for example. We mostly have images with clear weather. A model built using this set would probably perform very well in clear weather condition. However, this is what the real data is sometimes going to look like. Nighttime condition an overcast weather.

If you cannot gather more data to increase the variability of your dataset, data augmentation maybe the solution for you. Our model trained on clear weather data would not perform well in such conditions. If you cannot gather more data to increase the variability of your training dataset, data augmentation maybe the solution for you. Data augmentation is a way to introduce more variability in your dataset by transforming your input image at the pixel level by adding blur for example, or transforming your input image using geometric operation such as rotation. We are going to see some example in the next slide.

Data augmentations should be carefully curated as you want them to reflect what you could potentially see in your dataset but you were not able to capture. For example, a vertical flip augmentation would not be suited for traffic sign classification. As you can hope, then the car will never have to read the traffic sign upside down. Finally, augmentations are often performed dynamically while loading the image and before feeding it into the network. This way, we are not saving the augmented images to disk.

Let's look at some augmentations together in the next slide. Let's consider this image of a crossing sign and let's see what kind of augmentations we can apply to this image. Keep in mind that this augmentations should reflect something that we could see in our test set. First, we could consider blurring as an augmentation. For example, the weather might be foggy.

The car may also be driving fast, in which case we would see some motion blur in the image. We could also apply some small rotation to our image. However, the angle of the rotation should remain small because we would not expect upside down traffic sign in our test set. Increasing and decreasing the brightness is a great way to simulate sunny and overcast weather. Finally, we can mimic potential occlusion on the traffic sign.

Indeed, a tree or another obstacle could occlude the traffic sign and we should make our network robust to occlusion. In the following video, we'll learn how to leverage Albumentations, a Python library that creates augmentation. In this video, we are going to learn how to leverage albumentation, a Python library for image augmentation. Let's open an image and look at a first augmentation. Because albumentation expects a numpy array, we need to convert this image.

We are going to apply a simple rotation augmentation. Each augmentation and albumentations comes with at least two parameters, always_apply and p. Always_apply is a Boolean that you would set to true if you wanted this augmentation to be always used. P is a float that sets the probability of using this augmentation. P equal one, and always_apply equal true, have slightly different behavior.

I encourage you to read the documentation of this library. This is how you would apply rotation to our image. We can look at the augmented image and see that indeed it has been rotated. Often, we want to combine augmentations. To do so, we're going to use the composed function.

The composed function takes a list of augmentation and applies them sequentially to the input image. Here, we use a rotation, contrast change, and dropout augmentations. Let's look at the image created. Finally, we can also apply augmentations to image with bounding boxes. Let's first load the image and the corresponding annotations.

We can also use the composed function, but we need to add an additional argument. This argument will inform albumentation of the format of the boxes, as well as the name of the label field. We can also threshold the minimum area of the outputted bounding boxes. When using geometric transformation, we may have to crop or reshape the bounding boxes, but we want to be sure that the size of the newly created bounding boxes is above a certain threshold. Indeed, a lot of object detection algorithms do not work properly with small objects.

Let's now look at the output of this transformation. Even though deep learning framework like TensorFlow have some pre-implemented augmentation, this library provides additional image augmentation. It is a great tool for any machine learning engineer, and I encourage you to experiment with it.

## Additional Content

## Augmentations
**Data augmentation** is a way to increase the variability in the training dataset without having to capture more images. By applying pixel-level and geometric transformations during training, we can artificially simulate different environments. For example, a blur filter could be used to mimic motion blur. The augmentations should be carefully chosen.
You can follow this [tutorial](https://www.tensorflow.org/tutorials/images/data_augmentation) to use data augmentation in **Tensorflow**. This approach is using the Keras API to create combinations of augmentations. A list of available augmentations can be found [here](https://www.tensorflow.org/api_docs/python/tf/keras/layers/experimental/preprocessing). 

Below we are introducing Albumentations, a framework agnostic data augmentation library.
### Albumentations
Many image augmentations libraries are available but one of the most popular is [albumentations](https://albumentations.ai/docs/). It provides fast and easy ways to apply pixel-level and geometric transformations to images and labels, including bounding boxes.
You can use the workspace below to play around with the code from the video.
