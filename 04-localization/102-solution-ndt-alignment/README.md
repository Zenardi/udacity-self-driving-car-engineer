# Solution: NDT Alignment

> Part of: **Utilizing Scan Matching**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=9-KesOlpELU)

## Summary

**README: NDT for Scan Matching**

This repository provides a detailed explanation of how to implement Normal Distributions Transform (NDT) for scan matching, including code examples and practical steps.

### Key Concepts

* **Init Guess**: The initial guess for the transformation between two point clouds is obtained from the starting pose.
* **Transformation Matrix**: The init_guess is converted into a 3D transformation matrix using the `transform` function.
* **NDT Object**: The NDT object is created and initialized with the source point cloud, number of iterations, and other hyperparameters.
* **VoxelGrid Filter**: A VoxelGrid filter is applied to the point clouds to reduce noise and improve performance.
* **Hyperparameters**: Various hyperparameters can be set for the NDT algorithm, including map resolution, step size, and minimum transformation difference.

### Practical Notes

To implement NDT for scan matching:

1. Create an `NDT` object with the source point cloud and other required parameters.
2. Apply a VoxelGrid filter to the point clouds using a suitable resolution value.
3. Set hyperparameters such as map resolution, step size, and minimum transformation difference.
4. Use the `alignClouds` function to perform alignment between two point clouds.

To benchmark ICP and NDT side by side:

1. Create a loop that iterates over both algorithms with different parameters (e.g., number of iterations).
2. Use keyboard input to switch between ICP and NDT matching.
3. Record the time taken for each algorithm to perform alignment and compare results.

Note: This implementation uses Point Cloud Library (PCL) functions and assumes familiarity with C++ programming language.

## Transcript

Now we're going ahead and looking over the solution for exercise 2 in lesson 2, filling in the NDT for utilizing scan matching. Also, note, I went ahead and copied over the ICP function so we can benchmark both of these side by side, which is really useful and beneficial for the final project, where you get to decide between using ICP or NDT to do your alignment and localization. Filling in NDT, first thing to do is to get that init_guess. We have this init_guess coming from the starting pose. Using that transform 3D, we can get that as a matrix, then going ahead and setting the number of iterations in our NDT object, giving it the source.

This is a bit different than ICP where we're giving it the transform source. Here, note that we're actually passing in this init_guess that we calculated as this matrix here, that's where it's doing the transformation within this alignment, a little bit different than ICP. Just take note of that. Just giving it directly to the source and then giving it this output Cloud calling the alignment, and then getting that final transformation very similar to ICP in returning that. That was the NDT.

Now, if we scroll down, the other thing is we're creating that VoxelGrid filter. This is very much the same as with the ICP actually, just identical there, and play with this resolution value. Then, creating that. So the NDT was created here, and then this setting some hyperparameters. So there's links to all the different hyperparameters you can set with this PCL NDT function.

Here are the main ones. Setting that map Cloud as a target. Here, a resolution of just a one meter cubes is being used to find that grid space resolution in the NDT. Then, some other things here I just put in is that here's a step size. This is saying this is the maximum step size for doing this line search method.

Also, the link to the PCL code for doing that step size is included. It's interesting to take a look at. You can see here's setting minimum transformation difference for termination condition. So just another hyperparameter that can be looked at. This was just trying to be set small.

Then, here, this is how you can benchmark the two side by side, we have the cnum for matching. If matching enum is NDT, then you can call NDT, otherwise if it's ICP, you call ICP. Here, we're just both doing iterations of three, but this is cool because then you can actually hit a key on the keyboard. If we go up here into that keyboard [inaudible] , if you hit I, it's going to do ICP matching, or if you hit N, it's going to be NDT, so then you can move the scan around. You can even save the position X, and then benchmark the two side by side, which one's faster?

Which one gives the smallest pose there? This will be really helpful when you want to decide between the two in the final project. There's the solution there.

## Additional Content

## Solution: NDT Alignment
### `NDT Function`

```cpp
Eigen::Matrix4d NDT(pcl::NormalDistributionsTransform

ndt, PointCloudT::Ptr source, Pose startingPose, int iterations){

	
	pcl::console::TicToc time;
	time.tic ();

	Eigen::Matrix4f init_guess = transform3D(startingPose.rotation.yaw, startingPose.rotation.pitch, startingPose.rotation.roll, startingPose.position.x, startingPose.position.y, startingPose.position.z).cast();

  	// Setting max number of registration iterations.
  	ndt.setMaximumIterations (iterations);
	ndt.setInputSource (source);
  	
	pcl::PointCloud::Ptr cloud_ndt (new pcl::PointCloud);
  	ndt.align (*cloud_ndt, init_guess);

	//cout << "Normal Distributions Transform has converged:" << ndt.hasConverged () << " score: " << ndt.getFitnessScore () <<  " time: " << time.toc() <<  " ms" << endl;

	Eigen::Matrix4d transformation_matrix = ndt.getFinalTransformation ().cast();

	return transformation_matrix;

}
```
### Set Resolution and Point Cloud Target (Map) for NDT

```cpp
pcl::NormalDistributionsTransform ndt;
// Setting minimum transformation difference for termination condition.
ndt.setTransformationEpsilon (.0001);
// Setting maximum step size for More-Thuente line search.
ndt.setStepSize (1);
//Setting Resolution of NDT grid structure (VoxelGridCovariance).
ndt.setResolution (1);
ndt.setInputTarget (mapCloud);
```

### Create the Voxel Filter

```cpp
// cloudFiltered = scanCloud; // Make sure you removed this line

pcl::VoxelGrid vg;
vg.setInputCloud(scans[0]);
double filterRes = 0.5;
vg.setLeafSize(filterRes, filterRes, filterRes);
typename pcl::PointCloud::Ptr cloudFiltered (new pcl::PointCloud);
vg.filter(*cloudFiltered);
```

### Change the Number of Iterations

```cpp
if(matching == Ndt)
    // Change 0 to 3 (or other positive number)
    transform = NDT(ndt, cloudFiltered, pose, 3);
```
