- [Intro to the Camera Sensor](#intro-to-the-camera-sensor)
- [Big Picture](#big-picture)
- [Distortion Correction](#distortion-correction)
- [Pinhole Camera Model](#pinhole-camera-model)
  - [Distortion Coefficients and Correction](#distortion-coefficients-and-correction)
- [Camera Calibration](#camera-calibration)
  - [Examples of Useful Code](#examples-of-useful-code)
  - [A note on image shape](#a-note-on-image-shape)
  - [Note on real chessboard dimension vs. calibration camera chessboard](#note-on-real-chessboard-dimension-vs-calibration-camera-chessboard)
  - [Solution: Camera Calibration](#solution-camera-calibration)
- [Image Manipulation](#image-manipulation)
- [Exercise 2](#exercise-2)
  - [Solution: Image Manipulation](#solution-image-manipulation)


# Intro to the Camera Sensor

Hi, and welcome to this lesson on the camera sensor. Why are we taking the time to understand the sensor?Well, this course is focusing on deepening forcomputer vision and a kind of data we'll be using is digital images. In the previous lesson,I highlighted how important it was forthe machine learning engineer to become one with the data. 

Well, this means that we need a good understanding of the origin of that data,and because we are using digital images as the principal source of data,we need to have a good understanding of the camera sensor. Self-driving cars rely heavily on cameras,and older self-driving cars have multiple of them. 

However, the raw data that we acquire withsuch sensor needs to be processed before we can use it in our machine learning algorithm. This lesson will show you how to process and manipulate digital images. First, we are going to learn about the physics ofthe camera sensor and how to correct the distortion in raw images. Next, we will learn about the camera pinhole model,a very useful simplification of the camera's sensor. Then we will focus on camera calibration. 

Camera calibration is a very critical step in processing digital imagesand every machine learning engineer working withthis kind of data should be familiar with this method. Because digital images are such complex data type,people came up with multiple column models to describe them. In this lesson, we will learn about three of them,the RGB, HSV, and HLS color models. Finally, we're going to learn how to manipulate image data in Python. In this lesson, I will be teaching with Cezanne. 

Cezanne is an expert in computer vision witha masters in electrical engineering from Stanford University. As a former researcher in Genomics and Biomedical Imaging,she has applied computer vision and deep learning to medical diagnostic applications. In this lesson, Cezanne builds some great content on camera calibration. You will be learning with her about distortion correction,the camera pinhole model,and how to use OpenCV,a Python image processing library to calibrate cameras. I am very excited to be working with her on this lesson.  Let's get started. 


This lesson will be organized as follow:

* The camera sensor and its distortion effect
* The camera pinhole model
* Camera calibration
* RGB and other color systems
* Image manipulation in Python


# Big Picture

Let's start with some high level concept. How does human vision work?The human eye captures light that is reflected from objects. Receptors inside our eyes convert the lightinto electric signals that are transmitted to the brain. The brain transforms these signal into the images we see. A camera works somewhat differently. It captures and focuses the light using lenses,which are pieces of glass that are placed in front of a digital sensor. 

Depending on their model,cameras can have one or multiple lenses. The light signal is then received by digital sensor that capture it in a digital format. There are many digital format images can be saved as,such as JPEG or PNG. In the next slide,we will see the usage of cameras in self-driving cars,as well as the limitations of the camera sensor. Why are cameras at the core of the self-driving car technology?First of all, cameras are very high resolution sensor. 

Let's consider a digital image. Such image is made of pixels,a square of a certain intensity. Modern cameras generate images made ofmillions of pixels providing us high quality information. Moreover, because cameras detect visible light,they have access to information that other sensor,such as LiDAR do not. This is extremely useful to detect colors or being able toperform optical character recognition to read traffic signs for example. Even though camera do not detect depths directly,it is possible to estimate the distance of an object onan image using a pair of cameras in a stereo system. 

Finally, cameras are relatively cheap and fairly small,making them easy to integrate in an existing car. However, cameras also have a lot of limitation as we will see in the next slide. One of the main challenges that cameras arefacing in self-driving cars system is the weather. Indeed, cameras are sensitive to weather condition and maynot perform as well in rainy or snowy weather for example. Furthermore, the raw data outputted bycameras does not provide any usable information by itself. 

It needs to be processed and fed into a machine learning algorithm. Finally, even though cameras can provide some depth's estimation,they are not the best at this task,which is a limiting factor when trying to estimate the position of an object in 3D. In most self-driving cars systems,cameras are often combined with other types of sensors,such as LiDAR or RADAR. Each sensor has its strengths and weaknesses,but combined together, they can solve most ofthe challenges a self-driving car's system is facing. 

Cameras are optical instruments capturing the light intensity on a digital image. The most important characteristics of a camera for a ML engineer are the following:

* **Resolution**: Number of pixels the image captured by the camera is made of (usually described in mega pixels).
* **Aperture**: size of the opening where the light enters the camera. Controls the amount of light received by the sensor.
* **Shutter speed**: duration that the sensor is exposed to the light. Also controls the amount of light by the sensor.
* **Focal length / field of view**: this parameter controls the angle of view of the image.

**Summary**

The video titled "Big Picture" provides an overview of the key concepts related to cameras and their role in machine learning, particularly in self-driving cars. Here are the main points covered:

1. **Camera Functionality**: Cameras are optical instruments that capture light intensity to create digital images. Important characteristics include resolution, aperture, shutter speed, and focal length.

2. **Human Vision vs. Camera Operation**: The video compares human vision to camera functionality, explaining how cameras capture and focus light using lenses and digital sensors to create images.

3. **Importance in Self-Driving Cars**: Cameras are crucial for self-driving technology due to their high resolution and ability to detect visible light, which helps in recognizing colors and reading traffic signs.

4. **Limitations**: While cameras provide valuable information, they have limitations, such as sensitivity to weather conditions and challenges in depth perception. They often need to be combined with other sensors like LiDAR or RADAR to address these challenges.

5. **Integration of Sensors**: The video concludes by emphasizing that using a combination of different sensors can help overcome the limitations of individual sensors, leading to more effective self-driving systems.


# Distortion Correction

When we talk about image distortion, we're talking about what happens whena camera looks at 3D objects in the real world andtransforms them into a 2D image. This transformation isn't perfect. For example, here's an image of a road and some images taken through differentcamera lenses that are slightly distorted. 

In these distorted images, you can see that the edges of the lanes are bent andsort of rounded or stretched outward. And distortion is actually changing what the shape andsize of these objects appears to be. This is a problem,because we're trying to accurately place the self-driving car in this world. 

Eventually, we'll want to look at the curve of a lane andsteer the correct direction. But if the lane is distorted, we'll get the wrong measurement forcurvature in the first place and our steering angle will be wrong. So, the frist step in analyzing camera images is to undo this distortion sothat we can get correct and useful information out of them. 

![](./images/lens.png)

**Distortion**

Image distortion occurs when a camera looks at 3D objects in the real world and transforms them into a 2D image; this transformation isn’t perfect. Distortion actually changes what the shape and size of these 3D objects appear to be. So, the first step in analyzing camera images, is to undo this distortion so that you can get correct and useful information out of them.

**Summary**

The video on "Distortion Correction" explains the concept of image distortion that occurs when a camera captures 3D objects and transforms them into a 2D image. Here are the key points discussed:

1. **Understanding Distortion**: Distortion happens due to imperfections in the camera's optics, which can alter the perceived shape and size of objects in the image.

2. **Impact on Self-Driving Cars**: For applications like self-driving cars, accurate image representation is crucial. Distorted images can lead to incorrect measurements of objects, affecting navigation and decision-making.

3. **Importance of Correction**: The first step in analyzing camera images is to correct for distortion. This ensures that the information extracted from the images is accurate and useful for tasks like lane detection and obstacle avoidance.

4. **Techniques for Correction**: While the video does not delve into specific techniques, it implies that various methods exist to rectify distortion in images.

Overall, the video emphasizes the necessity of distortion correction to obtain reliable data from camera images, which is vital for the effective functioning of self-driving technology.

# Pinhole Camera Model

Youtube Video: [Link](https://www.youtube.com/watch?v=FBHyHUN-A8c)

Before we get into the code and start correcting fordistortion, let's get some intuition as to how this distortion occurs. Here's a simple model of a camera called the pinhole camera model. When the camera forms an image,it's looking at the world similar to how our eyes do. By focusing the light that's reflected off of objects in the world. In this case through a small pinhole, the camera focuses the light that'sreflected off of a 3D traffic sign, and forms a 2D imageat the back of the camera or a sensor or some film would be placed. 

In fact the image it forms here will be upside down, andreversed because rays of light that enter from the top of an object will continue on that angled path through the pinhole andend up at the bottom of the formed image. Similarly, light that reflects off the right side of an objectwill travel to the left of the formed image. In math this transformation from 3D object points, P of X, Y, and Z. To 2D image points, P of just X, andY is done by a transformative matrix called the camera matrix. Which I'll call C for camera andwe'll need this to calibrate the camera later on. However, real cameras don't use tiny pinholes like this,they use lenses to focus multiple light rays at a time. 

Which allows them to quickly form images. But lenses can introduce distortion too. Light rays often bend a little too much ortoo little at the edges of a curved lens of a camera, and this creates the effectwe looked at earlier that distorts the edges of images. So that lines or objects appear, more or less, curved than they actually are. This is called radial distortion, and it's the most common type of distortion. Another type, is tangential distortion, if the camera's lens is not alignedperfectly parallel to the imaging plane where the camera film orsensor is, this makes an image look tilted. So that some objects appear further away or closer than they actually are. And this is tangential distortion. There are even example of lenses that purposefully distort images like fisheyeor wide angle lenses which keep radial distortion for stylistic effect. 

But for our purposes we are using this imagesto position ourself driving car and eventually steer it the right direction. So we need undistorted images that accurately reflectour real world surroundings. Luckily, this distortion can generally be captured by five numbers calleddistortion coefficients, whose values reflect the amount of radial andtangential distortion in an image. In severely distorted cases, sometimes even more thanfive coefficients are required to capture the amount of distortion. If we know these coefficients,we can use them to calibrate our camera and undistort our images. And the mathematical details of correcting fordistortion are in the notes below. Next we'll see how to get these coefficients and calibrate a camera. 


**Types of Distortion**

Real cameras use curved lenses to form an image, and light rays often bend a little too much or too little at the edges of these lenses. This creates an effect that distorts the edges of images, so that lines or objects appear more or less curved than they actually are. This is called radial distortion, and it’s the most common type of distortion.

Another type of distortion, is tangential distortion. This occurs when a camera’s lens is not aligned perfectly parallel to the imaging plane, where the camera film or sensor is. This makes an image look tilted so that some objects appear farther away or closer than they actually are.


## Distortion Coefficients and Correction

There are three coefficients needed to correct for **radial distortion**: **k1**, **k2**, and **k3**. To correct the appearance of radially distorted points in an image, one can use a correction formula.

In the following equations, $(x, y)$ is a point in a distorted image. To undistort these points, OpenCV calculates **r**, which is the known distance between a point in an undistorted (corrected) image $(x_{corrected}, y_{corrected})$ and the center of the image distortion, which is often the center of that image $(x_c, y_c)$. This center point $(x_c, y_c)$ is sometimes referred to as the *distortion center*. These points are pictured below.

*Note:* The distortion coefficient **k3** is required to accurately reflect *major* radial distortion (like in wide angle lenses). However, for minor radial distortion, which most regular camera lenses have, k3 has a value close to or equal to zero and is negligible. So, in OpenCV, you can choose to ignore this coefficient; this is why it appears at the end of the distortion values array: [k1, k2, p1, p2, k3]. In this course, we will use it in all calibration calculations so that our calculations apply to a *wider* variety of lenses (wider, like wide angle, haha) and can correct for both minor and major radial distortion.

![](./images/image-correction.png)
Points in a distorted and undistorted (corrected) image. The point (x, y) is a single point in a distorted image and (x_corrected, y_corrected) is where that point will appear in the undistorted (corrected) image.


$$x_{distorted} = x_{ideal}(1 + k_1r^2 + k_2r^4 + k_3r^6)$$

$$y_{distorted} = y_{ideal}(1 + k_1r^2 + k_2r^4 + k_3r^6)$$

**Radial distortion correction.**

There are two more coefficients that account for **tangential distortion: p1** and **p2**, and this distortion can be corrected using a different correction formula.

$$x_{corrected} = x + [2p_1xy + p_2(r^2 + 2x^2)]$$

$$y_{corrected} = y + [p_1(r^2 + 2y^2) + 2p_2xy]$$

**Tangential distortion correction.**


# Camera Calibration

Youtube Video: [Link](https://www.youtube.com/watch?v=lA-I22LtvD4)

I'll be going through the initial camera calibration stepsin this Jupyter notebook. The first step will be to read in calibration images of a chessboard. it's recommended to use at least 20 images to get a reliable calibration. And for this example,we have a lot of images in this calibration images folder. They are all images of a chessboard, taken at different angles and distances. And there's also a test image.  

I'll eventually want to test mycamera calibration and undistortion on. Each chessboard here has eight by six corners to detect. I'll go through the calibration steps forthe first calibration image in detail. First, you can see that I've already done my Numpy OpenCV andplotting imports. Then I'll read in the first image calibration1. jpg, and I'll display it. So here's our calibration image. I'll map the coordinates of the corners in this 2D image,which I'll call it's image points, to the 3D coordinates of the real,undistorted chessboard corners, which I'll call object points. So, I'll set up two empty arrays to hold these points, object points andimage points. The object points will all be the same. 

Just the known object coordinates of the chessboard corners foran eight by six board. These points will be 3D coordinates, x, y and z from the top left corner,0, 0, 0, to the bottom right, 7, 5, 0. The z coordinate will be zero forevery point, since the board is on a flat image plane. And x and y will be all the coordinates of the corners. So I'll prepare these object points,first by creating six by eight points in an array. Each with three columns for the x, y, and z coordinates of each corner. 

I'll initialize these all as zeros using Numpy's zero function. The z coordinate will stay zero so I'll leave that as it is but forour first two columns, x and yI'll use Numpy's mgrid function to generate the coordinates that I want. mgrid returns the coordinate values for a given grid size andI'll shape those coordinates back into two columns, one for x and one for y. Next, to create the image points, I want to lookat the distorted calibration image and detect the corners of the board. OpenCV gives us an easy way to detect chessboard corners with a functioncalled findChessboardCorners that returns the cornersfound in a grayscale image. So I'll convert this image to greyscale andthen I'll pass that into the findChessboardCorners function. This takes in our greyscale image along with the dimensions of the chessboardcorners. 

In this case, eight by six, and the last parameter is for any flags. And there are none in this example. If this function detects corners,I'll append those points to the image points array. I'll also add our prepared object points,objp, to the object points array. And these object points will be the same forall of the calibration images, since they represent a real chessboard. Next, I'll also draw the detected corners,with a call to drawChessboardCorners,that takes in our image, corner dimensions and corner points. A

nd I'll display these corners sothat we can see what was detected in an interactive window. So let's run this code. Here's what our detected corners look like. And if I zoom in, it looks like the corners were detected pretty accurately. The next step will be to do this for all the calibration images. I can read in all the calibration images by importing the glob API,which helps read in images with a consistent file name,like calibration one, two, three, and so on. 

Then, I'll iterate through each image file, detecting corners andappending points to the object and image points arrays. Then later, we'll be able to use the object points andimage points to calibrate this camera. I'll show you the OpenCV functions you'll need to calibrate the camera andfinally, undistort images. To calibrate a camera, OpenCV gives us the calibrateCamera function. This takes in our object points, our image points, andthe shape of the image. And using these inputs, it calculates andreturns the distortion coefficients and the camera matrix that we needto transform 3D object points to 2D image points. 

It also returns the position of the camera in the world, with values forrotation and translation vectors. The next function you'll need is undistort. This takes in a distorted image, our camera matrix, anddistortion coefficients. And it returns an undistorted, often called destination image. In the next quiz, you'll need to apply what you've learned to calibratethe camera and correct for image distortion. Good luck. 


> [!NOTE] 
> Note Regarding Corner Coordinates
> Since the origin corner is (0,0,0) the final corner is (6,4,0) relative to this corner rather than (7,5,0).

## Examples of Useful Code

Converting an image, imported by cv2 or the glob API, to grayscale:

```math
gray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
```

> [!NOTE]
> Note: If you are reading in an image using mpimg.imread() this will read in an RGB image and you should convert to grayscale using cv2.COLOR_RGB2GRAY, but if you are using cv2.imread() or the glob API, as happens in this video example, this will read in a BGR image and you should convert to grayscale using cv2.COLOR_BGR2GRAY. We'll learn more about color conversions later on in this lesson, but please keep this in mind as you write your own code and look at code examples.

**Finding chessboard corners (for an 8x6 board):**

```math
ret, corners = cv2.findChessboardCorners(gray, (8,6), None)
```

**Drawing detected corners on an image:**

```math
img = cv2.drawChessboardCorners(img, (8,6), corners, ret)
```

**Camera calibration, given object points, image points, and the shape of the grayscale image:**

```math
ret, mtx, dist, rvecs, tvecs = cv2.calibrateCamera(objpoints, imgpoints, gray.shape[::-1], None, None)
```

**Undistorting a test image:**

```math
dst = cv2.undistort(img, mtx, dist, None, mtx)
```

## A note on image shape

The shape of the image, which is passed into the `calibrateCamera` function, is just the height and width of the image. One way to retrieve these values is by retrieving them from the grayscale image shape array `gray.shape[::-1]`. This returns the image width and height in pixel values like (1280, 960).

Another way to retrieve the image shape, is to get them directly from the color image by retrieving the first two values in the color image shape array using `img.shape[1::-1]`. This code snippet asks for just the first two values in the shape array, and reverses them. Note that in our case we are working with a greyscale image, so we only have 2 dimensions (color images have three, height, width, and depth), so this is not necessary.

It's important to use an entire grayscale image shape or the first two values of a color image shape. This is because the entire shape of a color image will include a third value -- the number of color channels -- in addition to the height and width of the image. For example the shape array of a color image might be (960, 1280, 3), which are the pixel height and width of an image (960, 1280) and a third value (3) that represents the three color channels in the color image which you'll learn more about later, and if you try to pass these three values into the calibrateCamera function, you'll get an error.

## Note on real chessboard dimension vs. calibration camera chessboard

The video animation depicts a 6x8 chessboard, but a standard chessboard should have 8x8 squares. Camera calibration typically uses a checkerboard pattern, which resembles a chessboard but is specifically designed for calibration purposes. The most common calibration board has a 6x8 or 6x9 grid of internal corners (not squares). Unlike a standard chessboard (8x8 squares), calibration boards often have asymmetric patterns to help the algorithm detect orientation more accurately.

**Why is a 6x8 or 6x9 pattern used?**

The internal corner count (instead of square count) helps OpenCV and other calibration tools easily recognize the grid.

The asymmetric pattern ensures the detection of orientation.

The known dimensions allow precise calculation of camera parameters like focal length and lens distortion.

## Solution: Camera Calibration

Here is one example answer:

```python
def cal_undistort(img, objpoints, imgpoints):
    ret, mtx, dist, rvecs, tvecs = cv2.calibrateCamera(objpoints, imgpoints, img.shape[1::-1], None, None)
    undist = cv2.undistort(img, mtx, dist, None, mtx)
    return undist
```

> [!NOTE] 
> Note that the quiz is loading this image as channels first, so we use `img.shape[1::-1]` to get the height and width. This should be adjusted as necessary, such as is seen on the previous page for a grayscale image.


# Image Manipulation

Youtube Video: [Link](https://www.youtube.com/watch?v=5AFIMDb3NAc)

In this video, we're going to talk about color spaces or color models. What is a color space?A color space is a mathematical model that describes colors as tuples of numbers. We can represent and visualize the same image using different color spaces. For example, the red, green,and blue or RGB color model represents a coloras a tuple of three values between zero and 255. Later in this video,we will also learn about the HSV and HLS color models. But before we really dive into the different color spaces,let's talk about grayscale images. Grayscale images only carry information about intensity,meaning that each pixel value indicates the amount of light for that pixel. Grayscale images usually describe this intensity with a 8-bit integer. This is an example of a grayscale image. 

We can see how each object has a different intensity. For example, the white car reflects the light more thana black one and therefore comes up with a higher intensity on the image. Whereas grayscale images may be useful in some cases,a lot of the information is lost because we solely focus on the light intensity. In the next slide, we will learn about the RGB color model. Let's talk about our first color model,the RGB color model. It is one of the most popular,and you will learn how to master it in this lesson. In this model, each image is described using three channels: red, green, and blue. Let's look at this image, for example,if we were to open this image in Python using the RGB color model,we would obtain a 3-D array,made of a stack of three 2D arrays,one for each channel. We can visualize each channel individually by indexing this array. We obtain three grayscale images,each one containing the pixel intensity for their channel. 

Let's focus on some of the object of the scene to better understand the RGB color model. See how this red car comes with different intensity for each channel. It has a very high intensity in the red channel,but much lower ones in the green and blue channels,and now let's look at this yellow advertisement. It has very different intensities in each channel. If you look carefully at other objects in the scene,you will find similar behaviors. Let's summarize what we have learned about the RGB color model so far. In this color model,each pixel of the image is described as a tuple of three values. Most of the time, these values are 8-bit integer,but you may encounter floats as well. A RGB image can be decomposed in three channels,one for each color. 

![rgb-2](./images/rgb-2.png)

This is very useful when you want to threshold an image based on a specific color. For example, you want to remove all the red object of an image. Well, you could look at all the high-intensity pixels in the red channel. Despite being very popular,the RGB color model has some limitations. For example, it's not a linear color model. If you were to look at a tuple for bright red pixelin this model and divide all the values by two,you will not get a darker red,but a completely different color. Because of this, it is hard to determine specific color,and even after years working with the RGB color model,I still need to look at tables to determine the value of the color of interest. Let's see how other color spaces remediate this problem. 

![](./images/rgb-3.png)

Even though in this course we will mostly deal with the RGB color model,I want you to be familiar with two more models,the HSV, and HLS color models. They both use the same ID,and we can represent them as cylinder,as you can see on the right here. The HLS model stands for hue lightness and saturation. Whereas the HSV stands for hue saturation and value. The hue is a single number between zero and 360 that specifies the color. If we look at the cylinder representations of these models,the hue can be considered as an angle. The colors are grouped by values of hue. 

![](./images/hls.png)

The models also use the lightness and value,which are a different way to measure the relative lightness of a color. The higher this value is,the lighter is the color. Finally, the saturation is a measurement of the color fullness. The higher the saturation is,the more intense the color. For example, a bright red has a high saturation value. These color models are easier to use when we would like to do some colors thresholding,because [inaudible] is encoded with a single number. Let's now learn how to use these different color models in Python. 

---

**Grayscale** images are single channel images that only contain information about the intensity of the light.

Color models are mathematical models used to describe digital images. The **Red, Green, Blue (RGB)** color model describes images using three channels. Each pixel in this model is described by a triplet of values, usually 8-bit integers. This is the most common color model used in ML. **HLS/HSV** are also very popular color models. They take a different approach than the RGB model by encoding the color with a single value, the **hue**. The other two values characterize the darkness / colorfulness of the image.

**Summary**

The video on "Image Manipulation" covers essential concepts related to processing and modifying images in the context of machine learning and computer vision. Here are the key points discussed:

1. **Grayscale Images**: The video explains that grayscale images consist of a single channel that represents light intensity, with each pixel indicating the amount of light.

2. **Color Models**: It introduces the RGB (Red, Green, Blue) color model, which describes images using three channels, where each pixel is represented by a triplet of values. The video also mentions other popular color models, such as HLS (Hue, Lightness, Saturation) and HSV (Hue, Saturation, Value), which encode color differently.

3. **Importance of Color Models**: Understanding different color models is crucial for tasks like image processing and analysis, as they can affect how images are interpreted and manipulated.

4. **Applications**: The video highlights that knowledge of image manipulation and color models is fundamental for various applications in machine learning, including object detection and image classification.

# Exercise 2

**Part 1 - Masking**

**Objective**

The goal of this exercise is to make you familiar with color thresholding. We will be using the RGB color model. In particular, your goal is to isolate all the pixels of a RGB image equal / higher / lower to a given color and a create a binary mask. You will use this mask to create a masked version of the RGB image.

In the example below, we can see (from left to right), the original RGB image, the binary mask and the masked RGB image. In this example, we used a RGB color threshold of `(128, 128, 128)` and isolated all the pixels with a RGB value higher than this threshold.

![](./images/exercise2.png)
```
Left - Original RGB Image, Center - The binary mask, Right - The masked RGB Image
```

**Details**
You need to implement two functions in `masking.py`.

The `create_mask` function outputs a binary mask given an input RGB image. This mask has the same spatial dimensions as the input image. You need to perform an element-wise comparison as shown in the pseudo-code below:

```
mask[x, y] = 0 if image[x, y, :] <= color else mask[x, y] = 1
```

The `mask_and_display` function uses the image array as well as the mask array and displays next to each other the original image, the binary mask and the masked image.

**Running the Code**

> [!NOTE] 
> Any visualized code will only pop up through the workspace desktop - if you complete work in the primary workspace window, you'll need to click the "Desktop" button in the bottom right to view visualizations.

Run `python masking.py` to check your results.

> [!TIP]
> You can use numpy element-wise multiplication to mask the RGB image.

**Part 2 - Statistics**

**Objective**

In this exercise, you first need to calculate the channel wise mean and standard deviations of a list of images in `statistics.py`. Then you need to display the pixel value distributions per channel, as shown in the figure below, for example.

![](./images/exercise2-1.png)

Pixel value distribution per channel
Pixel value distribution per channel

**Details**

The `calculate_mean_std` function outputs the channel wise mean and standard deviation over a list in images. This function outputs two `1x3` numpy array, one for the mean and one for the standard deviation.

The `channel_histogram` function creates the channel wise histograms. You should encode each distribution with the same color channel as shown in the example above.

**Running the Code**

**Note**: Any visualized code will only pop up through the workspace desktop - if you complete work in the primary workspace window, you'll need to click the "Desktop" button in the bottom right to view visualizations. The channel_histogram function, as implemented in the solution, may take a substantial amount of time to display in the workspace (a minute or more).

Run `python statistics.py` to see the results of your code.

> [!TIP]
> You can use the `ImageStat` module of Pillow to calculate image statistics. Feel free to experiment with other Python visualization libraries such as Seaborn(opens in a new tab) (which is installed in the workspace).


## Solution: Image Manipulation

```python
# masking.py

import matplotlib.pyplot as plt
import numpy as np
from PIL import Image


def create_mask(path, color_threshold):
    """
    create a binary mask of an image using a color threshold
    args:
    - path [str]: path to image file
    - color_threshold [array]: 1x3 array of RGB value
    returns:
    - mask [array]: binary array
    """
    img = np.array(Image.open(path).convert('RGB'))
    R, G, B = img[..., 0], img[..., 1], img[..., 2]
    rt, gt, bt = color_threshold
    mask = (R > rt) & (G > gt) & (B > bt) 
    return img, mask


def mask_and_display(img, mask):
    """
    display 3 plots next to each other: image, mask and masked image
    args:
    - img [array]: HxWxC image array
    - mask [array]: HxW mask array
    """
    masked_image = img  *np.stack([mask]*3, axis=2)
    f, ax = plt.subplots(1, 3, figsize=(15, 10))
    ax[0].imshow(img)
    ax[1].imshow(mask)
    ax[2].imshow(masked_image)
    plt.show()


if __name__ == '__main__':
    path = 'data/images/segment-1231623110026745648_480_000_500_000_with_camera_labels_38.png'
    color_threshold = [128, 128, 128]
    img, mask = create_mask(path, color_threshold)
    mask_and_display(img, mask)
```


```python
# statistics.py

import glob

import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
from PIL import Image, ImageStat

from utils import check_results


def calculate_mean_std(image_list):
    """
    calculate mean and std of image list
    args:
    - image_list [list[str]]: list of image paths
    returns:
    - mean [array]: 1x3 array of float, channel wise mean
    - std [array]: 1x3 array of float, channel wise std
    """
    means = []
    stds = []
    for path in image_list:
        img = Image.open(path).convert('RGB')
        stat = ImageStat.Stat(img)
        means.append(np.array(stat.mean))
        stds.append(np.array(stat.var)**0.5)
    
    total_mean = np.mean(means, axis=0)
    total_std = np.mean(stds, axis=0)

    return total_mean, total_std


def channel_histogram(image_list):
    """
    calculate channel wise pixel value
    args:
    - image_list [list[str]]: list of image paths
    """
    red = []
    green = []
    blue = []
    for p in image_list:
        img = np.array(Image.open(p).convert('RGB'))
        R, G, B = img[..., 0], img[..., 1], img[..., 2]
        red.extend(R.flatten().tolist())
        green.extend(G.flatten().tolist())
        blue.extend(B.flatten().tolist())

    sns.kdeplot(red, color='r')
    sns.kdeplot(green, color='g')
    sns.kdeplot(blue, color='b')


if __name__ == "__main__": 
    image_list = glob.glob('data/images/*')
    mean, std = calculate_mean_std(image_list)
    check_results(mean, std)
```