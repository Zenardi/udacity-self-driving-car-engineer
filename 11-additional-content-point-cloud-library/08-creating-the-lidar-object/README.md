# Creating the Lidar Object

> Part of: **[Optional] Intro to PCL**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=mU1kp4FXdVg)

## Summary

**Lidar Sensor Implementation for Simulation Environment**
===========================================================

This README file provides a summary of the key concepts and practical steps introduced in the Udacity lesson on creating a Lidar sensor for a simulation environment.

### Key Concepts

* **Lidar Object**: A struct that holds parameters for holding a PointCloud and has a constructor to set it up.
* **Ray Casting**: The process of simulating laser beams emitted by the Lidar unit, which can bounce off physical objects in the environment.
* **PointCloud**: A data structure used to represent 3D points in space, generated from the ray casting process.
* **Heap vs Stack Memory Allocation**: The importance of using the heap for memory allocation when dealing with large data structures like PointCloud.

### Practical Notes

* To create a Lidar object, instantiate it on the heap using the `new` keyword and provide parameters such as cars and ground plane slope value.
* Use the `lidar.h` file to define the Lidar struct and its constructor.
* In the `environment.cpp` file, use the `Lidar` pointer type to create a new instance of the Lidar object in the `simpleHighway` function.

**Example Code**

```cpp
// Create a Lidar object on the heap
Lidar* lidar = new Lidar(initHighway(), 0);
```

This code snippet demonstrates how to create a Lidar object using the `new` keyword and provide parameters for cars and ground plane slope value.

## Transcript

Next, we're actually going to look at creating a Lidar for our simulation environment. So we were talking a little bit before about this lidar.h file. It's in sensors. This is actually what we'll be using to create this virtual Lidar, and then use it to scan the environment and create some PointCloud data with it. The first thing we're going to do though is actually visualize what these Lidar rays look like as they're being cast from this virtual Lidar unit.

So what I want you to do then is back in the workspace environment. We will be looking at the simple highway function. Basically, there's a to-do there and it's to create a Lidar object. So what I'd like you to do basically in right at to-do, where it says create Lidar sensor, is to create this Lidar object. In order to do that, go ahead and checkout in "Sensors" lidar.h and see how that's defined.

So basically, what the Lidar object is, it's a struct. It has some parameters for holding a PointCloud, and it has a constructor that you'll be using to set it up. So right here in line 85 in lidar.h, check this out. This is how you actually instantiate the Lidar and look at what it's using. So these parameters that's taking in are used to actually do the ray casting.

It's basically telling the Lidar what physical objects rays can bounce off of. The objects here in our simulation environment are cars, and this ground slope value. So here we're just talking about this very horizontal ground, so we'll actually just be using zero for that. The cars that we get, that'll actually be from this init highway. It'll be generating these cars for us and returning that.

So you can actually instantiate this Lidar object back in the environment.cpp. Let's instantiate it on the heap. So in order to instantiate on the heap, you want to be using the new keyword. The reason we're doing it on the heap instead of the stack is well this Lidar is actually going to be holding this PointCloud and maybe it could potentially be very large. On the stack, we only have about two megabytes to work from.

On the heap, they can be much larger. So let's go ahead and instantiate that Lidar object on the heap using the new keyword. So it'll be this Lidar pointer and then new Lidar. I'll use this declaration here for setting up the arguments which are the cars that are returned from init highway, and then zero for the ground plane. So check out this lidar.h file and then go back into environment.cpp, and see if you can create this Lidar object in the simple highway function in the to-do.

All right. Let's check out the solution now for creating this lighter object. So back in environment.cpp. In this simple highway function, we can go ahead and create our Lidar as so. So here we're instantiating on the heap.

So we have this lidar pointer type, and we're using the new keyword, and then the arguments were cars, and so cars is actually just coming from the initHighway function. That's just the list of cars in our simulation environment, and then we're using zero just saying that our ground plane is at zero slope. So it's just the horizontal plane. Now, if we go ahead and say that, we could compile and then we have this lighter object.

## Additional Content

## Creating the Lidar Object
The first thing you are going to do is create a lidar object. The lidar object is defined by the `src/sensors/lidar.h` header file which is included at the top of environment.cpp. Also in `environment.cpp` is the `simpleHighway` function, which takes a reference argument for the PCL visualizer `viewer` that was discussed previously.

### Exercise Instructions

You will instantiate a pointer to a `Lidar` object in the `simpleHighway` function.
You should create the `Lidar` pointer object on the heap, using the `new` keyword.
The `Lidar` constructor takes two arguments: cars and the slope of the ground - these arguments are necessary for modeling ray collisions. The `Lidar` object should be created with a slope of 0.

#### Note

The lidar  arguments are necessary for modeling ray collisions.
The Lidar object is going to be holding point cloud data which could be very large. By instantiating on the heap, we have more memory to work with than the 2MB on the stack. However, it takes longer to look up objects on the heap, while stack lookup is very fast.

### Solution
In `environment.cpp`, within the `simpleHighway` function:

```cpp
// TODO: Create lidar sensor
Lidar* lidar = new Lidar(cars, 0);
```
