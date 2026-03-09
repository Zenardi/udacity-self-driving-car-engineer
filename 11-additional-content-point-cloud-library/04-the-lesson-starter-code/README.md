# The Lesson Starter Code

> Part of: **[Optional] Intro to PCL**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=yVdyzmStvFI)

## Summary

**Simulated Highway Environment and Point Cloud Processing**

This project involves working with a simulated highway environment where lidar scanning is used to detect other cars around us. The goal is to process the point cloud data using various techniques such as filtering, segmentation, and clustering.

**Key Concepts:**

* **Point Cloud**: A set of 3D points in space that represent objects or surfaces.
* **Lidar Scanning**: Using light detection and ranging technology to capture 3D data from the environment.
* **Simulated Highway Environment**: A virtual representation of a highway with virtual cars, street, and other objects.
* **Point Cloud Processing Techniques**:
	+ Filtering: Removing noise and outliers from point cloud data.
	+ Segmentation: Identifying and separating different objects or surfaces within the point cloud.
	+ Clustering: Grouping points that are close together in space.
* **Templates**: A way to define a class with specific properties and behavior, used in the `processPointClouds` file.

**Practical Notes:**

* The starter code includes four main files:
	+ `environment.cpp`: Contains the main function for launching the visual window and rendering the simulated environment.
	+ `processPointClouds.cpp`: Defines functions for filtering, segmentation, and clustering point cloud data.
	+ `lidar.h`: A header file for working with lidar objects and ray casting.
* The project uses a virtual desktop environment provided by Visual Studio Code to work on the code.

## Transcript

So let's go ahead now and dive into this starter code that we're going to be working with. Basically, what we have set up for this first couple of lessons, is working with this simulated highway environment where we're going to be doing lidar scanning and see the other cars around us. Then, look at the point cloud processing techniques to figure out where these other cars are at. So the main files that we'll be working with, there's four of them; its environment.cpp, its processPointClouds, and there's a.cpp and a header file for that as well. Then, there's this render directory.

You won't be working with that too closely, but it's nice to know that it's there, and it has this render.cpp and render.h files. Also, is this sensors lidar.h, and we'll be using that later to do some scanning. Let's go ahead now and in the classroom, we have this, our workspace environment. What's nice is, we can go ahead and we have this desktop button here. We can go ahead and launch right into this virtual desktop environment, and here we have a Visual Studio code.

So this is an id that's provided. We can open it up. Let's go ahead and check out what the workspace looks like here. So there is this directory called source, and inside source, we're going to have the environment.cpp file that we're just talking about. Let's go ahead and just look at this file from high overview and see what it's doing.

Well, this file is going to be your main file that it's going to have your main function here, and basically what that's going to be doing is launching this visual window that you can use to view your point clouds and other objects in your scene. So what other objects are those? Well, here we're creating this simple highway environment. So there is this highway, and that's going to be generating these virtual cars, this virtual street, and it's going to be rendering this all to the viewer. Then there's also this function for doing initCamera, and this initCamera is going to be setting up.

So when you first launch the window, you would have these different camera views that you can look at. So this kind of main function that you'll be launching in this environment.cpp. Here's another big file. This is the processPointClouds.cpp, and this one is where it has all these function decoration setup for doing filtering, for doing segmentation. So if we look at this, if we go up to the top here, we can see that it's being defined as this class, and it's using some different templates that we'll be talking about a little bit later.

So we can actually create a point cloud processor, and then we have these functions here for doing filtering the Cloud. I'm looking at doing the segmentation. So we kind of scroll down here. We have a clustering function. Then we're talking a little bit about render, and that's what's actually going to allow us to render our simulated environment.

Then the last thing, we'll be working with this file pretty soon. Is a lidar object which will actually be doing ray casting, and we'll use it to create some point cloud data.

## Additional Content

## The Lesson Starter Code
### Starter Repo Structure
*Note: Aaron's mention of the other lessons ~0:10 is what happens in the Sensor Fusion ND this lesson originally came from - you'll still be working with localization techniques in the upcoming lessons here!*
All the code for our brief dive into PCL (as well as more content from Sensor Fusion ND on obstacle detection) is contained in a GitHub repository. The classroom has workspace environments that already include all the dependencies for getting started right way. You can also clone the repo, and use the README to get started on your own machine as well. Here is the [link](https://github.com/udacity/SFND_Lidar_Obstacle_Detection).

You will mostly be working out of two main files, which are `environment.cpp` and `processPointClouds.cpp`. The `environment.cpp` file contains the `main` function and will generate the runnable executable. The `processPointClouds.cpp` file will contain all your function placeholders to process the pcd. 

There are some other files worth mentioning, like `sensors/lidar.h`, which simulates lidar sensing and creates point cloud data. Also `render.cpp` and `render.h` which have functions for rendering objects onto the screen.

### Code Structure 

- Top-level `CMakeLists.txt`
- `Readme`
- `src/`
  - `render/`
    - `box.h` - this file has the struct definitions for box objects
    - `render.h`
    - `render.cpp` - this file, along with the header, define the classes and methods for rendering objects. 
  - `sensors/`
    - `data/` - this directory contains pcd data used in the course.
    - `lidar.h` - has functions using ray casting for creating pcd.
  - `environment.cpp` - the main file for using pcl viewer and processing and visualizing pcd.
  - `processPointClouds.h`
  - `processPointClouds.cpp` - Functions for filtering, segmenting, clustering, boxing, loading, and saving pcd.

### Starter Repo Walkthrough
