# Image Manipulation

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=5AFIMDb3NAc)

## Summary

**Color Spaces and Models**
==========================

This project explores the concept of color spaces and models, specifically the RGB, HSV, and HLS color models. A color space is a mathematical model that describes colors as tuples of numbers.

**Key Concepts**
---------------

* **Color Space**: A mathematical model that describes colors as tuples of numbers.
* **RGB Color Model**: Represents a color as a tuple of three values (red, green, blue) between 0 and 255. Each pixel is described by a 3-tuple of 8-bit integers or floats.
* **Grayscale Images**: Represented as single-channel images with intensity values between 0 and 255.
* **HSV Color Model**: Represents colors using hue (angle), saturation, and value. Hue is a single number between 0 and 360 that specifies the color.
* **HLS Color Model**: Similar to HSV, but uses lightness instead of value.

**Practical Notes**
------------------

* To work with images in Python, use libraries such as OpenCV or Pillow to load and manipulate images using different color models (RGB, HSV, HLS).
* When working with the RGB color model, be aware of its limitations, including non-linearity. This can make it difficult to determine specific colors.
* The HSV and HLS color models are more intuitive for certain tasks, such as color thresholding, due to their use of a single number (hue) to specify color.

This project provides a foundation for understanding the basics of color spaces and models, including the RGB, HSV, and HLS color models. By mastering these concepts, developers can better work with images in various applications.

## Transcript

In this video, we're going to talk about color spaces or color models. What is a color space? A color space is a mathematical model that describes colors as tuples of numbers. We can represent and visualize the same image using different color spaces. For example, the red, green, and blue or RGB color model represents a color as a tuple of three values between zero and 255.

Later in this video, we will also learn about the HSV and HLS color models. But before we really dive into the different color spaces, let's talk about grayscale images. Grayscale images only carry information about intensity, meaning that each pixel value indicates the amount of light for that pixel. Grayscale images usually describe this intensity with a 8-bit integer. This is an example of a grayscale image.

We can see how each object has a different intensity. For example, the white car reflects the light more than a black one and therefore comes up with a higher intensity on the image. Whereas grayscale images may be useful in some cases, a lot of the information is lost because we solely focus on the light intensity. In the next slide, we will learn about the RGB color model. Let's talk about our first color model, the RGB color model.

It is one of the most popular, and you will learn how to master it in this lesson. In this model, each image is described using three channels: red, green, and blue. Let's look at this image, for example, if we were to open this image in Python using the RGB color model, we would obtain a 3-D array, made of a stack of three 2D arrays, one for each channel. We can visualize each channel individually by indexing this array. We obtain three grayscale images, each one containing the pixel intensity for their channel.

Let's focus on some of the object of the scene to better understand the RGB color model. See how this red car comes with different intensity for each channel. It has a very high intensity in the red channel, but much lower ones in the green and blue channels, and now let's look at this yellow advertisement. It has very different intensities in each channel. If you look carefully at other objects in the scene, you will find similar behaviors.

Let's summarize what we have learned about the RGB color model so far. In this color model, each pixel of the image is described as a tuple of three values. Most of the time, these values are 8-bit integer, but you may encounter floats as well. A RGB image can be decomposed in three channels, one for each color. This is very useful when you want to threshold an image based on a specific color.

For example, you want to remove all the red object of an image. Well, you could look at all the high-intensity pixels in the red channel. Despite being very popular, the RGB color model has some limitations. For example, it's not a linear color model. If you were to look at a tuple for bright red pixel in this model and divide all the values by two, you will not get a darker red, but a completely different color.

Because of this, it is hard to determine specific color, and even after years working with the RGB color model, I still need to look at tables to determine the value of the color of interest. Let's see how other color spaces remediate this problem. Even though in this course we will mostly deal with the RGB color model, I want you to be familiar with two more models, the HSV, and HLS color models. They both use the same ID, and we can represent them as cylinder, as you can see on the right here. The HLS model stands for hue lightness and saturation.

Whereas the HSV stands for hue saturation and value. The hue is a single number between zero and 360 that specifies the color. If we look at the cylinder representations of these models, the hue can be considered as an angle. The colors are grouped by values of hue. The models also use the lightness and value, which are a different way to measure the relative lightness of a color.

The higher this value is, the lighter is the color. Finally, the saturation is a measurement of the color fullness. The higher the saturation is, the more intense the color. For example, a bright red has a high saturation value. These color models are easier to use when we would like to do some colors thresholding, because [inaudible] is encoded with a single number.

Let's now learn how to use these different color models in Python.

## Additional Content

## Image Manipulation
**Grayscale** images are single channel images that only contain information about the intensity of the light. 

Color models are mathematical models used to describe digital images.  The **Red, Green, Blue (RGB)** color model describes images using three channels. Each pixel in this model is described by a triplet of values, usually 8-bit integers. This is the most common color model used in ML. **HLS/HSV** are also very popular color models. They take a different approach than the RGB model by encoding the color with a single value, the **hue**. The other two values characterize the darkness / colorfulness of the image.
