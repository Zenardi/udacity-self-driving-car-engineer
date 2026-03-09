# Lesson Conclusion

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=sU7jdtpNZ9I)

## Summary

**Camera Sensor Fundamentals**
=====================================

This project covers the basics of camera sensors used in self-driving cars. We'll explore how cameras work, image calibration, color models, and image manipulation techniques.

**Key Concepts**
---------------

* **Camera Pinhole Model**: A mathematical model that simulates how a camera captures images by projecting 3D points onto a 2D plane.
* **Image Calibration**: The process of correcting distortion in raw images using checkerboards to estimate the intrinsic parameters of the camera.
* **Color Models**:
	+ **RGB (Red, Green, Blue)**: A widely used color model that represents colors as combinations of red, green, and blue intensities.
	+ **HSV (Hue, Saturation, Value)**: A color model that separates color into hue, saturation, and value components for better image processing.
* **Geometric Transformations**: Techniques to manipulate images by transforming pixels at the pixel level or using geometric transformations.

**Practical Notes**
-------------------

This project provides a foundation in manipulating image data in Python. You should now be able to:

* Use the camera pinhole model to calibrate images
* Understand the strengths and weaknesses of different color models (RGB, HSV)
* Apply geometric transformations to manipulate images

In the next lesson, you'll learn how to use these skills to train machine learning algorithms using image data.

## Transcript

In this lesson, we'll learn about one of the primary components of self-driving cars, the camera sensor. First, we learn how a camera works and why processing raw images is needed to correct the distortion. We use the camera pinhole model to calibrate images using checkerboards. We then learn about the different color models, such as RGB or HSV, and the strengths and weaknesses of each one. In the last part of this lesson, we'll learn how to manipulate images.

First, by transforming them at the pixel level, and then by using geometric transformations. These transformations are used in image processing libraries for machine learning and are very useful to know. You should now be familiar with manipulating image data in Python. In the next lesson, we are going to start using these images to train machine learning algorithm. You have reached the end of this lesson.

Congrats, you should now be familiar with the camera sensor and comfortable with manipulating image data in Python. In the next lesson, we are going to start using these images to train machine learning algorithm.

## Additional Content

## Lesson Conclusion
In this lesson, we learned about:
- **The camera sensor and its distortion effect.** A camera captures light to a digital sensor but the raw images are distorted. 
- **The camera pinhole model:** a simplified physical model of cameras.
- **Camera calibration** and how to use the Python library OpenCV to calibrate a camera using checkerboard images.
- **RGB and other color systems.** We discovered the RGB, HLS and HSV color systems and learned about the strength and weaknesses of each one.
- **Image manipulation in Python** and how to leverage Pillow to perform pixel-level and geometric transformations of digital images.
