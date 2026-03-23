# Solution: ICP Alignment

> Part of: **Utilizing Scan Matching**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=FmWCNpvKkS0)

## Summary

**ICP (Iterative Closest Point) Algorithm and VoxelGrid Filter**

This README file provides a summary of key concepts and practical steps for implementing the ICP algorithm and using the VoxelGrid filter in 3D point cloud processing.

### Key Concepts

* **ICP Algorithm**: An iterative method for aligning two point clouds by finding the closest points between them.
	+ Transformation: A matrix that represents the rotation, translation, and scaling of a point cloud.
	+ Correspondence distance: The maximum allowed distance between corresponding points in the two input point clouds.
* **VoxelGrid Filter**: A technique for reducing the number of points in a point cloud by grouping nearby points into voxels (3D pixels).
	+ Filter resolution (filterRes): The size of each voxel, which determines the level of detail in the filtered point cloud.

### Practical Notes

To implement the ICP algorithm and VoxelGrid filter:

1. **Define a matrix** from the starting pose and perform the transformation to get the transformed source.
2. Create an ICP PCL function with input parameters:
	* Number of iterations
	* Transform source
	* Target point cloud
3. Set the maximum correspondence distance (e.g., 2) to control convergence.
4. Use the VoxelGrid filter by creating a `VG PCL VoxelGrid` object and setting its input as the scan Cloud with a filterRes of 0.5 (or experiment with different values).
5. Apply the VoxelGrid filter to the point cloud, outputting the filtered Cloud.
6. Repeat steps 2-5 for multiple iterations, adjusting parameters as needed.

Note: This is just one possible implementation of the ICP algorithm and VoxelGrid filter. Experimentation with different parameters and techniques may be necessary to achieve optimal results.

## Transcript

Here's a solution for going over Exercise 1 in Lesson 2. Here's how we can fill an ICP, very much the same as in the first exercise of Lesson 1. Grab that starting pose, define a matrix out of it. Do the transformation, and get transformed source, create that ICP PCL function. Input the number of iterations, give it the transform source as its input, give it the target as the target.

Here setting a max correspondence distance of two. This is something to play with if it's too small, then you'll see that ICP will fail to converge. Then going ahead and creating that new output point cloud, doing the alignment, seeing if it has converged, grabbing that final transformation, and then multiplying it by initTransform to get that full transformation. So going from start, starting pose, to the final transformation, and then otherwise returning that identity matrix. Then the other part was creating that VoxelGrid Filter.

If we scroll down here, that's done by creating this VG PCL VoxelGrid, setting the scan Cloud as the input, here a filterRes of 0.5 is being used. You can definitely experiment with this. Then that's being used in all three, so it's a cube. Then that will output to Cloud filtered. Then here we're just setting number of iterations to three, so we want this to be small.

Yeah, go ahead and play with this, but yeah, there's the solution.

## Additional Content

## Solution: ICP Alignment
### `ICP Function`

```cpp
Eigen::Matrix4d ICP(PointCloudT::Ptr target, PointCloudT::Ptr source, Pose startingPose, int iterations){

	// Defining a rotation matrix and translation vector
  	Eigen::Matrix4d transformation_matrix = Eigen::Matrix4d::Identity ();

  	// align source with starting pose
  	Eigen::Matrix4d initTransform = transform3D(startingPose.rotation.yaw, startingPose.rotation.pitch, startingPose.rotation.roll, startingPose.position.x, startingPose.position.y, startingPose.position.z);
  	PointCloudT::Ptr transformSource (new PointCloudT); 
  	pcl::transformPointCloud (*source, *transformSource, initTransform);

  	/*
  	if( count == 0)
  		renderPointCloud(viewer, transformSource, "transform_scan_"+to_string(count), Color(1,0,1)); // render corrected scan
  	*/
	
	pcl::console::TicToc time;
  	time.tic ();
  	pcl::IterativeClosestPoint

icp;
  	icp.setMaximumIterations (iterations);
  	icp.setInputSource (transformSource);
  	icp.setInputTarget (target);
	icp.setMaxCorrespondenceDistance (2);
	//icp.setTransformationEpsilon(0.001);
	//icp.setEuclideanFitnessEpsilon(.05);
	//icp.setRANSACOutlierRejectionThreshold (10);

  	PointCloudT::Ptr cloud_icp (new PointCloudT);  // ICP output point cloud
  	icp.align (*cloud_icp);
  	//std::cout << "Applied " << iterations << " ICP iteration(s) in " << time.toc () << " ms" << std::endl;

  	if (icp.hasConverged ())
  	{
  		//std::cout << "\nICP has converged, score is " << icp.getFitnessScore () << std::endl;
  		transformation_matrix = icp.getFinalTransformation ().cast();
  		transformation_matrix =  transformation_matrix * initTransform;
  		//print4x4Matrix(transformation_matrix);


  		/*
  		PointCloudT::Ptr corrected_scan (new PointCloudT);
  		pcl::transformPointCloud (*source, *corrected_scan, transformation_matrix);
  		if( count == 1)
  			renderPointCloud(viewer, corrected_scan, "corrected_scan_"+to_string(count), Color(0,1,1)); // render corrected scan
		*/
  		return transformation_matrix;
  	}
	else
  		cout << "WARNING: ICP did not converge" << endl;
  	return transformation_matrix;

}
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
if(matching == Icp)
    // Change 0 to 3 (or other positive number)
    transform = ICP(mapCloud, cloudFiltered, pose, 3);
```
