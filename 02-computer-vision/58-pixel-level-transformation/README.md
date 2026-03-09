# Pixel Level Transformation

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ASFah7kFRB4)

## Summary

**Image Manipulation with OpenCV and Pillow**
=====================================================

This project demonstrates how to manipulate images using the OpenCV library and the Pillow library in Python.

### Key Concepts

* **Pillow Image Attributes**: A Pillow image has several attributes, including size and mode (color model used).
* **Color Models**: RGB, RGBA, HSV, and grayscale color models are discussed.
	+ RGB: Red, Green, Blue color model
	+ RGBA: Red, Green, Blue, Alpha (transparency) color model
	+ HSV: Hue, Saturation, Value color model
	+ Grayscale: 2D array of pixel values representing shades of gray
* **Image Conversion**: Converting images between different color models using `image.convert()`.
* **Pixel Values**: Accessing and manipulating pixel values in an image using NumPy arrays.
* **Binary Mask**: Creating a binary mask to isolate specific pixels based on their hue value.
* **Image Filtering**: Applying filters to an image, including blurring, contour detection, smoothing, and sharpening.

### Practical Notes

To manipulate images with Pillow:

1. Import the `image` module from Pillow.
2. Load an image using `image.open()`.
3. Access image attributes, such as size and mode.
4. Convert images between different color models using `image.convert()`.
5. Display images in Jupyter Notebooks by typing the variable name.

To apply filters to an image:

1. Import pre-implemented filters from Pillow.
2. Apply filters to an image using methods like `blur()` or `contour()`.
3. Experiment with custom filter implementation using Pillow's API.

This project provides a foundation for further exploration of image manipulation techniques, including geometric transformations and pixel-level transformations.

## Transcript

With [inaudible] , you learn how to manipulate images with the OpenCV library. In this video, we will use another very popular Python image library, Pillow. We're going to see how we can leverage this library to open images, convert them in different color models, and perform colors thresholding. Let's start by importing some packages. In this video, we will only use the image module.

We can use the image.open to load an image. A Pillow image has several attributes, such as the size or the mode, which is the color model used. Our image is in the PNG format, which supports among other RGB and RGBA color models. The mode of an image depends on the way it was saved. Even though our image is already in the RGB format, we can run image.convert to transform it into RGB image.

In Jupyter Notebooks, Pillow images are very easily displayed by just typing the variable name. Now that we have loaded an RGB image, what if we want to look at the grayscale versions? Well to do, so we just have to run Image.convert L to convert it into a grayscale format. Finally, let's convert our image to the HSV color model. We cannot display such image in a notebook, however, we can still manipulate it.

Let's try to see if we can isolate the red car in this image. We can get the pixel values of these HSV image by loading it into a NumPy array, then we can isolate hue channel. We are trying to select only the dark red pixels, which are pixels with a hue between 340 and 360. However, because pixels in HSV images in Pillow are stored as eight bits integer, we need to scale this value. We can create a binary mask to keep only the pixel, whether hue is above our threshold.

We can use this mask to mask the RGB image. We multiply the RGB pixel values by two to emphasize the colors. Finally, we can visualize the masked RGB image. If we were to use the RGB model to create this mask, it will be much more challenging as we would have to create the mask based on triplets of value. Hopefully, this shows you the pros and cons of the different color models.

In this second video about pixel level transformations, we are going to learn about a few more ways you can leverage the Pillow Library to transform images. Let's start by loading the different function, as well as the small helper function to plot image histograms. In the first part of this video, we're going to focus on image contrast. The contrast of an image is defined by the difference in colors between the different object in this image. Let's look at this first image and take a look at the RGB value histograms.

As we can see on this histogram, the channel distributions are much more spread out. This is an example of what you can do with image enhance. I encourage you to spend time playing around with this module. I also want you to be familiar with image filtering. It's an extremely useful Pillow feature.

Pillow comes with pre-implemented filters, but you can also implement your own and I encourage you to look into that. Filters are pixel level transformation, such as blurring. We can blur this image using the pre-implemented filter. As you can see, the output image is slightly blurred. This is extremely useful if we were to mimic foggy images, for example.

Other pre-implemented filter exist in Pillow, such as contour, smooth, or sharpen. Well, with this notebook, we're done with pixel-level transformation with the Pillow Library. In the next video, we are going to focus on geometric transformation.

## Additional Content

## Pixel Level Transformation
**Pillow** is a python imaging library. Using Pillow, we can easily load images, convert them from one color model to another and perform diverse pixel level transformation, such as color thresholding. **Color thresholding** consists of isolating a range of color from a digital image. It can be done using different color models, but the HSV/HLS color models are particularly well suited for this task.
You can use the workspace below to try out the same code from the video as well as the second video further down the page.
### Image Enhancement and Filtering
Images in ML dataset reflect real life conditions and therefore may need to be improved upon or modified. Pillow provides a very useful module, **ImageEnhance**, to perform pixel level transformations on images, such as contrast changes. Moreover, ML engineers often want to add some noise to the images in the dataset to reduce overfitting. ImageEnhance provides simple ways of doing so.
