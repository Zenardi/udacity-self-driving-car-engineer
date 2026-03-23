# Using NDT to Align

> Part of: **Utilizing Scan Matching**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=y4oEZhp8jJQ)

## Summary

**Summary of Scan Matching with NDT**

This lesson builds upon previous exercises by introducing Normal Distributions Transform (NDT) scan matching. The main topic is utilizing PCL's NDT function to create a grid space from a target PointCloud and then applying voxel grid filtering to improve performance.

**Key Concepts**

* **Scan Matching**: A technique used in robotics for aligning point clouds of a scene.
* **Normal Distributions Transform (NDT)**: A method for registering point clouds by creating a probability distribution over the points.
* **Voxel Grid Filtering**: A technique used to reduce the number of points in a point cloud, improving performance and reducing computational cost.
* **PCL's NDT function**: A pre-built function in PCL that creates an NDT object from a target PointCloud.

**Practical Notes**

To implement scan matching with NDT:

1. Create an NDT object using PCL's `ndt::NormalDistributionsTransform` class, passing in the target PointCloud and setting the resolution of the grid.
2. Apply voxel grid filtering to reduce the number of points in the point cloud.
3. Pass the NDT object into the NDT function, which will calculate the transform between the current pose and the target pose.
4. Use keyboard shortcuts (I for ICP, N for NDT) to test and compare the performance of both methods.

Note: Benchmarking is an important aspect of this lesson, as it allows you to compare the performance of ICP and NDT scan matching in real-time.

## Transcript

So here's the second exercise for lesson 2, utilizing scan matching and now working with NDT. It would be very similar to the previous exercises in ICP, now just with NDT, so the same layout as the previous exercise. Now you'll just be filling in this NDT function and the notes for doing that are all in the classroom. This will be using a PCL object, so in the previous lesson you were creating NDT from scratch, here you'll just be utilizing the code in PCL to call this NDT function. Then from lesson 1, you're familiar at least with how NDT is functioning.

Then along with creating that, defining an NDT function in main, you'll be doing a voxel grid filtering. Again, having a lower number of points in your scan also is beneficial for time for NDT as well. Fewer H and G matrices that you need to look up and calculate for a fewer number of points, so doing this filtering will help giving NDT the run in real-time. Also along with that defining, so here is that NDT object in PCL. There's just a couple of things to do here that are only done once, they're not done like every iteration that would be called in an NDT function.

So only in the very innate state you're doing things such as setting the resolution for the grid, remember NDT is creating a grid space from the target PointCloud. So you'll be setting that resolution and you'll be giving it that target PointCloud, which is the map that's loaded up above here. Then once it has that that's only called once, so it will be setting that. Then NDT object will be passed into the NDT function down below. So let me see if it's matching NDT, you can see it's being passed in right here.

Then that's giving us our transform. Here, just like in the previous exercise, go ahead and play with this value to try to get it to be as fast as possible, but also as accurate. So you increase the accuracy, it should increase but also increasing this comes with a cost, which is it takes more time. See what gives the best results with that, and that's essentially it. Have fun.

Let's take a look at what it looks like once we fill in the code for ICP and NDT and run the program. In-home workspace, NDT matching L2, we're going to be comparing both of those side-by-side. We will run scan matching too. We'll load this up, and then, let's go ahead and hit I on the keyboard, and then we'll do ICP so we can see how it's moving and it's aligning once it stops moving, some amount of threshold the test will stop and it'll record the time so it was taking about 3.3 seconds for doing that alignment on the pose error, there was 0.2 meters is about 36 cycles total of doing that. Then we can go ahead and reset it.

If we hit N instead, so that was testing ICP, we hit N. That was faster, 2.4 seconds, total cycles 22 and 0.075 for the pose error. NDT was better in that case, but is it always better? We can move this around, so we can use the keyboard, and then we can use K, and let's say something like this. Then if we hit X, I believe we save it.

Then if we kind of move and hit space, now we'll always snap back to that position. Let's go ahead and hit I. Those ICP testing still going 3.4 seconds, 39, 0.21, okay, then we say that pose with the X, and then we're going to hit space. Then we're back there and let's hit N. It's looking like it's faster again, and it is doing pretty well here right now.

I have seen that there are some poses of course, for ICP will be better. But yeah, this is really great to checkout for doing benchmarking, that was about half the time, and the pose error was better there too. That's how you can benchmark in run NDT, and ICP side-by-side, and figure out which one you want to use for the final project.

## Additional Content

## Using NDT to Align: The Code
### NDT Alignment Demo
## Using NDT to Align

Now that you have implemented ICP, in this next exercise you will do the same but for NDT. The set up for NDT in PCL is very similar to the steps for ICP but with a few differences.

First lets look at the header function for `NDT` in `sm2-main.cpp` and compare this to the header function for `ICP` from `sm1-main.cpp` that you just used.

```
//NDT
Eigen::Matrix4d NDT(pcl::NormalDistributionsTransform

ndt, PointCloudT::Ptr source, Pose startingPose, int iterations)

//ICP
Eigen::Matrix4d ICP(PointCloudT::Ptr target, PointCloudT::Ptr source, Pose startingPose, int iterations)
```

The difference between the two functions is the **target** paramater from `ICP` is now an **ndt** object in `NDT`. This is because you might recall from the first lesson that you don't want to have have to build the NDT mapping space every time, that would be very inefficient. So instead the **ndt** object with the point cloud map input and set space resolution are only set once at the beginning and then passed to the `NDT` function to use. In `sm2-main.cpp` the **ndt** object is already defined.

```
pcl::NormalDistributionsTransform ndt;
```

Your task will then be to set the input cloud, resolution, and any additional parameter settings that you wish for NDT. Here is how to set some of the main parameters for **ndt**.

#INPUT `pcl::PointCloud::Ptr` input point cloud pointer

#RES `double` size of the cell, ~1m can be a good starting value to test

#STEP `double` max step size, ~1m can be a good starting value to test

```cpp
ndt.setInputTarget (##INPUT);
ndt.setResolution (##RES);
ndt.setStepSize (##STEP);
```

For more details on [setting **ndt** parameters check out this link](https://pointclouds.org/documentation/tutorials/normal_distributions_transform.html).
## Implementing NDT function with PCL

Completing the **NDT** can be done in a few lines of code.

##ITERATIONS int set from the function header value **iterations**

##SOURCE `pcl::PointCloud::Ptr` set from the function header value **source**

##TRANSFORM `Eigen::Matrix4d` intial pose from function header **startingPose**

The function `transfrom3D` from `helper.h` can be used to convert the input `Pose` object to a matrix.

##OUTPUT `pcl::PointCloud` aligned scan

```cpp
ndt.setMaximumIterations (##ITERATIONS);
ndt.setInputSource (##SOURCE);
ndt.align (##OUTPUT, ##TRANSFORM);
```

The final matrix transformation from **ndt** can be retrieved by calling

```cpp
ndt.getFinalTransformation ().cast();
```
## Testing ICP vs NDT

Once NDT has been implemented the same steps from the ICP exercise can be used to test it and benchmark it's time and errors from various starting poses. The code from the ICP exercise can be downloaded and copied into this exercise in order to test ICP and NDT side by side. To download the previous ICP code in **ICP Exercise** section right click on the completed sm1-main.cpp file inside the workspace, then click download. Then in the **NDT Exercise** from the workspace select upload file and select the downloaded sm1-main.cpp file. After that the completed part of the sm1-main.cpp can be copied and pasted into the sm2-main.cpp. The enum matching selector will now have three values. `enum Registration{ Off, Icp, Ndt};`
