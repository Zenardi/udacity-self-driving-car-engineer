# Distortion Correction

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Bv3o0INBQIU)

## Summary

**Image Distortion: Understanding and Undoing Camera Transformations**

When a camera captures 3D objects in the real world, it transforms them into a 2D image. However, this transformation is not perfect and can result in distorted images. This distortion affects the shape and size of objects, making it challenging to accurately place self-driving cars in their environment.

**Key Concepts:**

* **Image Distortion**: The process by which a camera's lens transforms 3D objects into a 2D image, introducing errors in shape and size.
* **Camera Transformations**: The mathematical processes that convert 3D coordinates to 2D pixel coordinates on an image sensor.
* **Distorted Images**: Images with bent or stretched edges, where the lane markings appear rounded or stretched outward.

**Practical Notes:**

To accurately analyze camera images, it's essential to undo this distortion. This involves understanding how camera transformations affect the shape and size of objects in the scene. In practice, this means applying algorithms that correct for lens distortions, ensuring accurate measurements of curvature and other features. By removing distortion from images, self-driving cars can obtain reliable information about their surroundings, enabling them to navigate safely and efficiently.

## Transcript

<v English>When we talk about image distortion,</v>
<v English>we're talking about what happens when</v> <v English>a camera looks at 3D objects</v>
<v English>in the real world and</v> <v English>transforms them into a 2D image.</v> <v English>This transformation isn't perfect.</v> <v English>For example, here's an image of a road</v>
<v English>and some images taken through different</v> <v English>camera lenses that</v>
<v English>are slightly distorted.</v> <v English>In these distorted images, you can see</v>
<v English>that the edges of the lanes are bent and</v> <v English>sort of rounded or stretched outward.</v> <v English>And distortion is actually</v>
<v English>changing what the shape and</v> <v English>size of these objects appears to be.</v> <v English>This is a problem,</v> <v English>because we're trying to accurately place</v>
<v English>the self-driving car in this world.</v> <v English>Eventually, we'll want to look</v>
<v English>at the curve of a lane and</v> <v English>steer the correct direction.</v> <v English>But if the lane is distorted,</v>
<v English>we'll get the wrong measurement for</v> <v English>curvature in the first place and</v>
<v English>our steering angle will be wrong.</v> <v English>So, the frist step in analyzing camera</v>
<v English>images is to undo this distortion so</v> <v English>that we can get correct and</v>
<v English>useful information out of them.</v>

## Additional Content

## Distortion Correction
**Distortion** 

Image distortion occurs when a camera looks at 3D objects in the real world and transforms them into a 2D image; this transformation isn’t perfect. Distortion actually changes what the shape and size of these 3D objects appear to be. So, the first step in analyzing camera images, is to undo this distortion so that you can get correct and useful information out of them.
