# Camera Calibration

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lA-I22LtvD4)

## Summary

**Camera Calibration with OpenCV**
=====================================

This project demonstrates the initial steps in camera calibration using OpenCV. The goal is to read in calibration images of a chessboard, detect corners, and prepare object points and image points for later use in calibrating the camera.

### Key Concepts

* **Chessboard Corner Detection**: Using OpenCV's `findChessboardCorners` function to detect corners in a grayscale image.
* **Object Points**: 3D coordinates of real chessboard corners, represented as (x, y, z) values.
* **Image Points**: 2D coordinates of detected chessboard corners in the distorted image.
* **Camera Calibration**: Using OpenCV's `calibrateCamera` function to calculate distortion coefficients and camera matrix from object points and image points.

### Practical Notes

To run this code, you'll need to have OpenCV installed. The project uses Jupyter Notebook for interactive coding.

**Step 1: Read in Calibration Images**

* Use the `glob` API to read in calibration images with consistent file names (e.g., `calibration1.jpg`, `calibration2.jpg`, etc.).
* Display each image using OpenCV's `imshow` function.

**Step 2: Detect Chessboard Corners**

* Convert each image to grayscale.
* Use `findChessboardCorners` to detect corners in the grayscale image.
* Append detected points to the `image_points` array.

**Step 3: Prepare Object Points and Image Points**

* Create an array of object points (3D coordinates) for a standard chessboard (8x6).
* Initialize object points with zeros, then use NumPy's `mgrid` function to generate x and y coordinates.
* Append prepared object points to the `objp` array.

**Step 4: Calibrate Camera**

* Use OpenCV's `calibrateCamera` function to calculate distortion coefficients and camera matrix from object points and image points.
* The function returns additional parameters, including rotation and translation vectors.

## Transcript

<v English>I'll be going through the initial camera calibration steps</v> <v English>in this Jupyter notebook.</v> <v English>The first step will be to read in calibration images of a chessboard.</v> <v English>it's recommended to use at least 20 images to get a reliable calibration.</v> <v English>And for this example,</v> <v English>we have a lot of images in this calibration images folder.</v> <v English>They are all images of a chessboard, taken at different angles and distances.</v> <v English>And there's also a test image. I'll eventually want to test my</v> <v English>camera calibration and undistortion on.</v> <v English>Each chessboard here has eight by six corners to detect.</v> <v English>I'll go through the calibration steps for</v> <v English>the first calibration image in detail.</v> <v English>First, you can see that I've already done my Numpy OpenCV and</v> <v English>plotting imports.</v> <v English>Then I'll read in the first image calibration1.jpg, and I'll display it.</v> <v English>So here's our calibration image.</v> <v English>I'll map the coordinates of the corners in this 2D image,</v> <v English>which I'll call it's image points, to the 3D coordinates of the real,</v> <v English>undistorted chessboard corners, which I'll call object points.</v> <v English>So, I'll set up two empty arrays to hold these points, object points and</v> <v English>image points.</v> <v English>The object points will all be the same.</v> <v English>Just the known object coordinates of the chessboard corners for</v> <v English>an eight by six board.</v> <v English>These points will be 3D coordinates, x, y and z from the top left corner,</v> <v English>0, 0, 0, to the bottom right, 7, 5, 0.</v> <v English>The z coordinate will be zero for</v> <v English>every point, since the board is on a flat image plane.</v> <v English>And x and y will be all the coordinates of the corners.</v> <v English>So I'll prepare these object points,</v> <v English>first by creating six by eight points in an array.</v> <v English>Each with three columns for the x, y, and z coordinates of each corner.</v> <v English>I'll initialize these all as zeros using Numpy's zero function.</v> <v English>The z coordinate will stay zero so I'll leave that as it is but for</v> <v English>our first two columns, x and y</v> <v English>I'll use Numpy's mgrid function to generate the coordinates that I want.</v> <v English>mgrid returns the coordinate values for a given grid size and</v> <v English>I'll shape those coordinates back into two columns, one for x and one for y.</v> <v English>Next, to create the image points, I want to look</v> <v English>at the distorted calibration image and detect the corners of the board.</v> <v English>OpenCV gives us an easy way to detect chessboard corners with a function</v> <v English>called findChessboardCorners that returns the corners</v> <v English>found in a grayscale image.</v> <v English>So I'll convert this image to greyscale and</v> <v English>then I'll pass that into the findChessboardCorners function.</v> <v English>This takes in our greyscale image along with the dimensions of the chessboard</v> <v English>corners.</v> <v English>In this case, eight by six, and the last parameter is for any flags.</v> <v English>And there are none in this example.</v> <v English>If this function detects corners,</v> <v English>I'll append those points to the image points array.</v> <v English>I'll also add our prepared object points,</v> <v English>objp, to the object points array.</v> <v English>And these object points will be the same for</v> <v English>all of the calibration images, since they represent a real chessboard.</v> <v English>Next, I'll also draw the detected corners,</v> <v English>with a call to drawChessboardCorners,</v> <v English>that takes in our image, corner dimensions and corner points.</v> <v English>And I'll display these corners so</v> <v English>that we can see what was detected in an interactive window.</v> <v English>So let's run this code.</v> <v English>Here's what our detected corners look like.</v> <v English>And if I zoom in, it looks like the corners were detected pretty accurately.</v> <v English>The next step will be to do this for all the calibration images.</v> <v English>I can read in all the calibration images by importing the glob API,</v> <v English>which helps read in images with a consistent file name,</v> <v English>like calibration one, two, three, and so on.</v> <v English>Then, I'll iterate through each image file, detecting corners and</v> <v English>appending points to the object and image points arrays.</v> <v English>Then later, we'll be able to use the object points and</v> <v English>image points to calibrate this camera.</v> <v English>I'll show you the OpenCV functions you'll need to calibrate the camera and</v> <v English>finally, undistort images.</v> <v English>To calibrate a camera, OpenCV gives us the calibrateCamera function.</v> <v English>This takes in our object points, our image points, and</v> <v English>the shape of the image.</v> <v English>And using these inputs, it calculates and</v> <v English>returns the distortion coefficients and the camera matrix that we need</v> <v English>to transform 3D object points to 2D image points.</v> <v English>It also returns the position of the camera in the world, with values for</v> <v English>rotation and translation vectors.</v> <v English>The next function you'll need is undistort.</v> <v English>This takes in a distorted image, our camera matrix, and</v> <v English>distortion coefficients.</v> <v English>And it returns an undistorted, often called destination image.</v> <v English>In the next quiz, you'll need to apply what you've learned to calibrate</v> <v English>the camera and correct for image distortion.</v> <v English>Good luck.</v>

## Additional Content

## Camera Calibration
## Note Regarding Corner Coordinates

Since the origin corner is (0,0,0) the final corner is (6,4,0) relative to this corner rather than (7,5,0).
** Examples of Useful Code**

Converting an image, imported by cv2 or the glob API, to grayscale:

```
gray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
```

*Note*: If you are reading in an image using mpimg.imread() this will read in an **RGB** image and you should convert to grayscale using *cv2.COLOR_RGB2GRAY*, but if you are using cv2.imread() or the glob API, as happens in this video example, this will read in a **BGR** image and you should convert to grayscale using *cv2.COLOR_BGR2GRAY*. We'll learn more about color conversions later on in this lesson, but please keep this in mind as you write your own code and look at code examples.

Finding chessboard corners (for an 8x6 board):

```
ret, corners = cv2.findChessboardCorners(gray, (8,6), None)
```

Drawing detected corners on an image:

```
img = cv2.drawChessboardCorners(img, (8,6), corners, ret)
```

Camera calibration, given object points, image points, and the **shape of the grayscale image**:

```
ret, mtx, dist, rvecs, tvecs = cv2.calibrateCamera(objpoints, imgpoints, gray.shape[::-1], None, None)
```

Undistorting a test image:

```
dst = cv2.undistort(img, mtx, dist, None, mtx)
```
### A note on image shape

The shape of the image, which is passed into the **calibrateCamera** function, is just the height and width of the image. One way to retrieve these values is by retrieving them from the **grayscale image shape** array `gray.shape[::-1]`. This returns the image width and height in pixel values like (1280, 960). 

Another way to retrieve the image shape, is to get them directly from the *color* image by retrieving the first two values in the color image shape array using `img.shape[1::-1]`. This code snippet asks for just the first two values in the shape array, and reverses them.  Note that in our case we are working with a greyscale image, so we only have 2 dimensions (color images have three, height, width, and depth), so this is not necessary.

It's important to use an entire grayscale image shape *or* the first two values of a color image shape. This is because the entire *shape* of a color image will include a third value -- the number of color channels -- in addition to the height and width of the image. For example the shape array of a color image might be (960, 1280, 3), which are the pixel height and width of an image (960, 1280) and a third value (3) that represents the three color channels in the color image which you'll learn more about later, and if you try to pass these three values into the calibrateCamera function, you'll get an error.
### Note on real chessboard dimension vs. calibration camera chessboard

---

The video animation depicts a 6x8 chessboard, but a standard chessboard should have 8x8 squares. Camera calibration typically uses a checkerboard pattern, which resembles a chessboard but is specifically designed for calibration purposes. The most common calibration board has a 6x8 or 6x9 grid of internal corners (not squares). Unlike a standard chessboard (8x8 squares), calibration boards often have asymmetric patterns to help the algorithm detect orientation more accurately.

**Why is a 6x8 or 6x9 pattern used?**

The internal corner count (instead of square count) helps OpenCV and other calibration tools easily recognize the grid.

The asymmetric pattern ensures the detection of orientation.

The known dimensions allow precise calculation of camera parameters like focal length and lens distortion.
