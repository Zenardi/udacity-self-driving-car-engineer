# Geometric Transformation

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=a1WG6FIr6yY)

## Summary

**Geometric Transformation in Images**
=====================================

This README file summarizes the key concepts of geometric transformation in images, including resizing, translation, and shearing.

### Key Concepts

* **Affine Transformation**: A type of geometric transformation that preserves straight lines and ratios between lengths. In the context of image processing, affine transformations are used to resize, translate, or shear images.
* **Resizing**: A common operation where an image is resized from one dimension to another. This can be achieved using the `Image.resize` function in Pillow.
* **Transformation Matrix**: A mathematical representation of a geometric transformation, which can be used to perform resizing, translation, and shearing operations on an image.
* **Inverse Transformation Matrix**: The inverse of the transformation matrix is required when applying transformations using the `transform` method of the Pillow image class.

### Practical Notes

To resize an image from 1920x1080 to 960x640, you can use the following code:
```python
from PIL import Image

img = Image.open('image.jpg')
img_resized = img.resize((960, 640))
```
Alternatively, you can define a transformation matrix and apply it using the `transform` method:
```python
from PIL import Image

img = Image.open('image.jpg')

# Define transformation matrix for resizing by half
c_x = c_y = 0.5
trans_matrix = [c_x, 0, 0,
                0, c_y, 0,
                0, 0, 1]

img_resized = img.transform(img.size, Image.AFFINE, trans_matrix)
```
Note that the transformation matrix for resizing by half is defined as `c_x` and `c_y` equals 0.5. Be careful to use the inverse of the transformation matrix when applying transformations using the `transform` method.

## Transcript

In the previous videos, we learnt about color spaces and the different types of pixel over transformation we can apply on an image. This video is going to focus on geometric transformation. The first type of geometric transformation we are going to see is resizing. This is a very common operation, especially useful when loading data into a Machine Learning Algorithm. Indeed, we often cannot load full resolution images because of memory limitation.

Pillow makes image resizing extremely easy. Using the Image.resize function, we can resize our image from 1920 by 1080-960 by 640 in one line. The resizing operation is an example of an Affine transformation. We can replicate the results of the resizing operation using the transform method of the Pillow image class. For resizing, we need to define a transformation matrix as such, where c_x and c_y are the re-scaling factors.

If we want to divide by two the dimension of the image, we can use c_x and c_y equals 0.5. Be careful, the transform method takes the inverse of the transformation matrix as an input. After running this transformation, we observe that the image dimensions are indeed divided by two. affine transformations are very powerful. We are going to see two more, translation and shearing.

The transformation matrices are slightly different for this operation, as we can see here. Translation just shift the image by a certain number of pixels. For example, here we shift the image by 200 pixels to the right and 100 pixels down. We can use the transformation matrix to perform shearing as displayed here. In this case, we are going to perform Horizontal Shearing.

Finally, we can also combine different transformation. For example, here we combine translation and shearing. I encourage you to read more about affine transformations. There's a lot more we can do with Pillow.

## Additional Content

## Geometric Transformation
In addition to pixel level transformation, Pillow also provides ways to perform **geometric transformations**, such as rotation, resizing or translation. In particular, we can use Pillow to perform **affine transformation** (a geometric transformation where lines are preserved) using a transformation matrix. 
You can use the workspace below to try out the same code from the video.
