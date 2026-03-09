# Camera Measurement Model

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=RbebqvHQY18)

## Summary

**Camera Measurement Model H**
=====================================

This README file provides an overview of the key concepts and practical steps involved in deriving the camera measurement model H. The lesson covers the basics of image properties, coordinate systems, and intrinsic camera calibration.

**Key Concepts**
---------------

* **Camera Coordinate System XYZ**: The x-axis points forward, y-axis to the left, and z-axis upward.
* **Image Coordinate System**: Origin at the upper left corner of the image, with pixel coordinates denoted by I (horizontal) and J (vertical).
* **Focal Length F**: Replaced by Fi and Fj for horizontal and vertical focal lengths, respectively.
* **Image Center C**: Intersection of optical axis and image plane.
* **Intrinsic Camera Calibration**: Derives image center C and focal length F from the camera's internal parameters.

**Practical Notes**
------------------

To derive the camera measurement model H:

1. Understand the relationship between 3D vehicle coordinates (Px, Py, Pz) and projected image coordinates.
2. Replace Px with focal length F, and scale Py and Pz accordingly.
3. Apply modifications to account for:
	* Opposite direction of i and j coordinate axes: multiply by -1
	* Shift origin from image center C to upper left corner: add Ci and Cj respectively

The resulting camera measurement model H summarizes how to compute image coordinates (I, J) from 3D object coordinates in vehicle coordinates.

## Transcript

Here we are in the lesson map. In this video, we will derive the camera measurement model H. But first, we have to do a quick recap of image properties. In this image, we see the camera coordinate system XYZ. As before, the x-axis points forward, so the gray image plane is orthogonal to the x-axis.

Similarly, we will use a vehicle coordinate system for tracking where X points forward, Y points to the left, and Z points upward. But we will learn more about this later. The x-axis is the camera's optical axis. The intersection of the optical axis and the image plane is called the image center or principle point. The image coordinate system usually has its origin in the upper left corner of the image.

The pixel coordinates are denoted by I for the horizontal dimension, and J for the vertical dimension. Note that a pixel is not necessarily perfectly square. Instead of a single focal length F, we now have two numbers, Fi and Fj that might slightly differ. The image center C and focal length F are derived through intrinsic camera calibration. With these definitions, we now have everything to rewrite the measurement model.

Imagine there's a real-world vehicle with 3D position Px, Py, Pz. The vehicle is projected to the image, and we want to know the corresponding image coordinates which are depicted by the red image point. We know from the previous video that Px is replaced by the focal length F, and Py and Pz are scaled accordingly. The focal length F is the same for all image points, so we can remove the first coordinate. Replacing F with Fi and Fj for the focal length in image coordinates gives this red formula for the projected point.

There are two more changes we have to consider. First, the i and j coordinate axis point in the opposite direction of the Y and Z axis, so we have to multiply everything with minus 1. Second, the origin is not the image center, but the upper left corner. We have to shift the coordinates by Ci and Cj respectively. With these two modifications, we have found our camera measurement model H.

The formula summarizes how we can compute the image coordinates, hence the expected measurement from a 3D object in vehicle coordinates.

## Additional Content

## Camera Measurement Model
-

$\left(c_i, c_j\right)$

is the

$\textbf{image center}$

or

$\textbf{principal point}$

in image coordinates, derived from intrinsic camera calibration.
-

$\left(f_i, f_j\right)$

is the

$\textbf{focal length}$

in image coordinates, derived from intrinsic camera calibration.
- Projecting a 3D point (or a 6D state vector, since we simply ignore the velocity components) to 2D image space gives the following

$\textbf{nonlinear measurement function}$

:

$$h(\mathbf{x}) =
h\left(\begin{pmatrix}
p_x\\
p_y\\
p_z\\
v_x\\
v_y\\
v_z
\end{pmatrix}\right) =
\Large \begin{pmatrix}
c_i-\frac{f_i\cdot p_y}{p_x}\\
c_j-\frac{f_j\cdot p_z}{p_x}
\end{pmatrix}$$

### H versus h(x)

The

$\textbf H$

matrix from the lidar lesson and

$h(\mathbf x)$

function from the camera lesson are actually accomplishing the same thing: they are both needed to calculate the residual

$\gamma=\mathbf z-\mathbf H\mathbf x$

in the update step.

But for camera, there is no

$\textbf H$

matrix that will map the state vector

$\textbf x$

into image coordinates; instead, you need to calculate the mapping manually to convert from cartesian coordinates to image coordinates.
 
Hence for camera,

$\gamma=\mathbf z-\mathbf H\mathbf x$

becomes

$\gamma=\mathbf z-h(\mathbf x)$

.

$h$

is a nonlinear function. In the next quiz, I would like to check your intuition about what that means.
