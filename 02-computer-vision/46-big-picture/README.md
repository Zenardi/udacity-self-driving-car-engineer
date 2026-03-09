# Big Picture

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Tfuucra9sKE)

## Summary

**Human Vision and Camera Technology**
=====================================

This project explores the basics of human vision and camera technology, including how cameras are used in self-driving cars.

**Key Concepts**
---------------

* **Light Detection**: Human eyes capture light reflected from objects, which is converted into electric signals transmitted to the brain.
* **Camera Functionality**: Cameras use lenses to focus light onto a digital sensor, capturing images in a digital format (e.g., JPEG or PNG).
* **Pixel Intensity**: Digital images are composed of pixels with varying intensity levels, providing high-resolution information.
* **Stereo Vision**: Using two cameras in a stereo system allows for depth estimation and object distance calculation.
* **Sensor Limitations**: Cameras have limitations, including sensitivity to weather conditions and the need for processing and machine learning algorithms.

**Practical Notes**
-------------------

* In self-driving cars, cameras are often combined with other sensors (e.g., LiDAR or RADAR) to overcome individual sensor limitations.
* Camera data requires processing and feeding into a machine learning algorithm to provide usable information.
* Weather conditions can affect camera performance, making it challenging for self-driving cars to operate in adverse weather.

## Transcript

Let's start with some high level concept. How does human vision work? The human eye captures light that is reflected from objects. Receptors inside our eyes convert the light into electric signals that are transmitted to the brain. The brain transforms these signal into the images we see.

A camera works somewhat differently. It captures and focuses the light using lenses, which are pieces of glass that are placed in front of a digital sensor. Depending on their model, cameras can have one or multiple lenses. The light signal is then received by digital sensor that capture it in a digital format. There are many digital format images can be saved as, such as JPEG or PNG.

In the next slide, we will see the usage of cameras in self-driving cars, as well as the limitations of the camera sensor. Why are cameras at the core of the self-driving car technology? First of all, cameras are very high resolution sensor. Let's consider a digital image. Such image is made of pixels, a square of a certain intensity.

Modern cameras generate images made of millions of pixels providing us high quality information. Moreover, because cameras detect visible light, they have access to information that other sensor, such as LiDAR do not. This is extremely useful to detect colors or being able to perform optical character recognition to read traffic signs for example. Even though camera do not detect depths directly, it is possible to estimate the distance of an object on an image using a pair of cameras in a stereo system. Finally, cameras are relatively cheap and fairly small, making them easy to integrate in an existing car.

However, cameras also have a lot of limitation as we will see in the next slide. One of the main challenges that cameras are facing in self-driving cars system is the weather. Indeed, cameras are sensitive to weather condition and may not perform as well in rainy or snowy weather for example. Furthermore, the raw data outputted by cameras does not provide any usable information by itself. It needs to be processed and fed into a machine learning algorithm.

Finally, even though cameras can provide some depth's estimation, they are not the best at this task, which is a limiting factor when trying to estimate the position of an object in 3D. In most self-driving cars systems, cameras are often combined with other types of sensors, such as LiDAR or RADAR. Each sensor has its strengths and weaknesses, but combined together, they can solve most of the challenges a self-driving car's system is facing.

## Additional Content

## Big Picture
Cameras are optical instruments capturing the **light intensity** on a digital image. The most important characteristics of a camera for a ML engineer are the following:
- **Resolution:** Number of pixels the image captured by the camera is made of  (usually described in mega pixels).
- **Aperture:** size of the opening where the light enters the camera. Controls the amount of light received by the sensor. 
- **Shutter speed:** duration that the sensor is exposed to the light. Also controls the amount of light by the sensor. 
- **Focal length / field of view:** this parameter controls the angle of view of the image.
