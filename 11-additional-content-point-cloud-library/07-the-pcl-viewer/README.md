# The PCL Viewer

> Part of: **[Optional] Intro to PCL**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=KrfNvS0mKuE)

## Summary

**Scene Rendering with PCL Viewer**
=====================================

This project uses the Point Cloud Library (PCL) viewer to create and render 3D scenes in a simulated environment.

### Key Concepts

* **PCL Viewer**: A library used for rendering 3D graphics and visualizing point clouds.
* **Point Cloud Library (PCL)**: An open-source library for processing and visualizing 3D point cloud data.
* **Reference Passing**: A technique where objects are passed to functions by reference, allowing changes made within the function to persist outside of it.
* **Viewer Initialization**: The process of setting up the PCL viewer with initial settings such as background color, camera parameters, and position.

### Practical Notes

The code uses the `PCLVisualizer` class to create a viewer that renders 3D scenes. The viewer is initialized in the `environment.cpp` file, where it is passed as a reference to various functions such as `emitCamera()` and `initHighway()`. These functions use the viewer to render cars and highways to the scene.

Example code snippets:

```cpp
// Initialize camera parameters and background color
viewer->setCameraParameters(...);
viewer->setBackgroundColor(...);

// Set initial camera position
viewer->setCameraPosition(...);

// Render cars and highways to the scene
for (auto car : cars) {
    viewer->renderCar(car);
}
```

Note that this summary focuses on the key concepts and practical notes, while omitting any implementation details not directly related to the PCL viewer.

## Transcript

All right. So now we're actually able to launch this executable and see what the simulated environment looks like, let's talk a little bit more about how it's creating the scene. For doing this, there's something called the PCL viewer. So this is the point Cloud library viewer. This is what's handling graphics and rendering.

So it's rendering the different boxes for the cars, for the road, it's creating those lines and we're also using those functions in environment.cpp for initializing the camera and initializing this highway environment. So let's go ahead and look at what this looks like in environment.cpp. Inside main here, we actually have this viewer that we are creating over here. So this viewer is a PCL visualization, PCL Visualizer and basically, it's going to run at certain frame rate and we can add things to this viewer. So if we look at emit camera in simple highway, we're actually passing in the viewer to these functions.

Let's see how they're being passed in. So for example, in a camera, we see that this PCL visualization viewer is actually being passed in as a reference. So what that means is any changes done to it will persist outside this function. So here we set things like the background color, we can initialize the camera parameters, and we can actually tell the viewer set this camera position so that initial position will be set when we launch that window. So similarly, the init highway function is also using that viewer, and it's being passed in as reference again right here.

What that is doing basically is we're going through and recreating these different cars, and we're specifying where they're located in the simulation environment. We're creating a vector of those cars and for that viewer, we basically call so car render in that viewer is being passed in again as a reference, and that tells the viewer, hey, I'm going to render this car to the scene. I'm going to render this highway to the viewer. So that is a little bit how that PCL viewer is working. It's handling all the graphics for us.

## Additional Content

## The PCL Viewer
### PCL Viewer Overview

In `environment.cpp` a pcl viewer is created. The viewer is used to handle all your visualization of objects on the screen. Some functions that use the pcl viewer inside `environment.cpp` are `initCamera` and `initHighway`. The `initCamera` function helps you set up different viewing angles in your window. There are five different options: XY, TopDown, Side, and FPS. XY gives a 45 degree angle view, while FPS is First Person Sense and gives the sensation of being in the car’s driver seat.

Also, the functions from `render` heavily use the `viewer` as well. You might notice that `viewer` is usually passed in as a reference. That way the process is more streamlined because something doesn't need to get returned. 

### Walkthrough of PCL Viewer Code
