# Solution: Intro to ICP

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=xVNL35P9T60)

## Summary

**Summary of Scan Matching using ICP**

This summary covers the key concepts and practical steps involved in implementing Iterative Closest Point (ICP) algorithm for scan matching. The lesson demonstrates how to use ICP to align a source point cloud with a target point cloud, and extract the transformation matrix.

### Key Concepts

* **Transformation Matrix**: A 4x4 matrix that represents the rotation and translation of an object in 3D space.
	+ Initialization: `initTransform` is set as the identity matrix using `transform2D`.
	+ Application: The initial transformation is applied to the source point cloud using `transformSource`.
* **ICP Algorithm**: A point-to-point matching algorithm that aligns two point clouds by iteratively refining the transformation matrix.
	+ Parameters:
		- Number of iterations
		- Source and target point clouds
	+ Output: The aligned point cloud (`newCloud`) and the final transformation matrix.
* **Convergence Check**: ICP converges when the alignment error between the source and target point clouds is minimized.
* **Transformation Multiplication**: To apply the initial offset to the overall solution, the transformation matrix is multiplied by the initial offset.

### Practical Notes

* **Code Pattern**: The code demonstrates how to use PCL (Point Cloud Library) objects to perform ICP alignment. Key functions include:
	+ `transform2D`: Initializes a 4x4 transformation matrix.
	+ `ICP::align()`: Aligns the source point cloud with the target point cloud using ICP.
* **Real-World Application**: The code can be used for scan matching in robotics, where it is essential to accurately align sensor data with the environment.

## Transcript

Let's go ahead and check out the solution for the first exercise on applying scan matching. Here, let's look at how to do ICP. Here, the first thing that we're doing, we initialized transformation matrix as the identity. Well, let's go ahead and get this initTransform, which is this four by four matrix. We'll do that by using this transform2D.

Then that was from the helper function. That's going to be from what is given in startingPose. So we get the startingPose.Theta, startingPose.position.x and startingPose.position.y, and then we can get that four by four matrix. Now we create this transformSource to a PointCloud pointer, and we're going to fill it in. We have this initTransform that we're applying on source, and that it will do the transformation on source.

That'll output it to this transformSource, which is being passed in as a reference. Now, you define this PCL ICP object here, which is doing point-to-point matching, called ICP. Set the number of iterations which is also in the header, give the transformSource that we just created, give the target, which is from the header, and then define this new cloud ICP, which is the PointCloud that has the transform applied to it. We won't actually be using it directly here, but we need it to do this alignment. Then we can call ICP align, and it's aligning the transformSource to the target.

Then we can check if ICP has converged, and if it has, we can grab this final transformation. An important step here is, if we use this initTransform, remember this created this offset for source. We want to make sure to apply it too to the overall solution, the overall movement of source. We're doing this multiplication here, and then we can go ahead and return the transformation matrix. Now, however, if ICP didn't converge, you could output this warning and just return to identity matrix.

That's it for the ICP function. Now, the other parts were saving the estimated location for next time. So a very easy way to do this, if you look at what's being passed in as the starting pose, it's location, which was first being defined up here as the center of the room at Theta zero. We'll just now save location as estimate, and then that'll be used for next time. The view that transforms scan, you can go ahead and do, okay, you can create a new PointCloud transform scan and then apply the transform that you just got from ICP onto the scan to get that transform scan and then do renderPointCloud to visualize it, then right here it's being visualized in green.

That's it for this solution.

## Additional Content

## Solution: Intro to ICP
```
using namespace std;

#include

#include 
#include "helper.h"

#include 
#include    // TicToc

Eigen::Matrix4d ICP(PointCloudT::Ptr target, PointCloudT::Ptr source, Pose startingPose, int iterations){

    Eigen::Matrix4d transformation_matrix = Eigen::Matrix4d::Identity ();

    // align source with starting pose
      Eigen::Matrix4d initTransform = transform2D(startingPose.theta, startingPose.position.x, startingPose.position.y);
      PointCloudT::Ptr transformSource (new PointCloudT); 
      pcl::transformPointCloud (*source, *transformSource, initTransform);

    pcl::console::TicToc time;
      time.tic ();
      pcl::IterativeClosestPoint icp;
      icp.setMaximumIterations (iterations);
      icp.setInputSource (transformSource);
      icp.setInputTarget (target);
      PointCloudT::Ptr cloud_icp (new PointCloudT);  // ICP output point cloud
      icp.align (*cloud_icp);

      if (icp.hasConverged ())
      {
          std::cout << "\nICP has converged, score is " << icp.getFitnessScore () << std::endl;
          transformation_matrix = icp.getFinalTransformation ().cast();
          transformation_matrix =  transformation_matrix * initTransform;
          return transformation_matrix;
      }
      cout << "WARNING: ICP did not converge" << endl;

    return transformation_matrix;

}

int main(){

    pcl::visualization::PCLVisualizer::Ptr viewer (new pcl::visualization::PCLVisualizer ("2D Viewer"));
    viewer->setBackgroundColor (0, 0, 0);
    viewer->addCoordinateSystem (1.0);

    // create a room
    double lowerX = -5;
    double upperX = 5;
    double lowerY = -5;
    double upperY = 5;
    vector room;
    LineSegment top(0, 1, upperY, lowerX, upperX);
    room.push_back(top);
    LineSegment bottom(0, 1, lowerY, lowerX, upperX);
    room.push_back(bottom);
    LineSegment right(1, 0, upperX, lowerY, upperY);
    room.push_back(right);
    LineSegment left(1, 0, lowerX, lowerY, upperY);
    room.push_back(left);

    // create lidar
    Lidar lidar(0, 0, 0, 100, 128);

    PointCloudT::Ptr poses (new PointCloudT);     // ground truth
    PointCloudT::Ptr locator (new PointCloudT); // estimated locations

    // starting location
    poses->points.push_back(PointT(lidar.x, lidar.y, 0));
    locator->points.push_back(PointT(lidar.x, lidar.y, 0));

    // get map of room
    PointCloudT::Ptr map = lidar.scan(room);
    cout << "map captured " << map->points.size() << " points" << endl;

    // move around the room

    // Part 1. TODO: localize from single step
    vector movement = {Vect2(0.5,pi/12)};

    // Part 2. TODO: localize after several steps
    if(true){ // Change to true
        movement.push_back(Vect2(0.8, pi/10));
        movement.push_back(Vect2(1.0, pi/6));
    }
    // Part 3. TODO: localize after randomly moving around the whole room
    if(true){ // Change to true
        srand(time(0));
        for(int i = 0; i < 10; i++){
            double mag = 0.5 * ((double) rand() / (RAND_MAX)) + 0.5;
            double angle = pi/8 * ((double) rand() / (RAND_MAX)) + pi/8;
            movement.push_back(Vect2(mag, angle));
        }
    }

    renderPointCloud(viewer, map, "map", Color(0,0,1)); // render map
    Pose location(Point(0,0), 0);
    PointCloudT::Ptr scan;
    int count = 0;
    for( Vect2 move : movement ){

        // exectue move
        lidar.Move(move.mag, move.theta);
        poses->points.push_back(PointT(lidar.x, lidar.y, 0));

        // scan the room
        scan = lidar.scan(room);
        cout << "scan captured " << scan->points.size() << " points" << endl;
        renderPointCloud(viewer, scan, "scan_"+to_string(count), Color(1,0,0)); // render scan

        // perform localization
        Eigen::Matrix4d transform = ICP(map, scan, location, 50); //TODO: make the iteration count greater than zero
        Pose estimate = getPose(transform);
        // TODO: save estimate location and use it as starting pose for ICP next time
        location = estimate;
        locator->points.push_back(PointT(estimate.position.x, estimate.position.y, 0));

        // view transformed scan
          PointCloudT::Ptr transformed_scan (new PointCloudT);
          pcl::transformPointCloud (*scan, *transformed_scan, transform);
          renderPointCloud(viewer, transformed_scan, "icp_scan_"+to_string(count), Color(0,1,0)); // render corrected scan

        count++;
    }

    // display ground truth poses vs estimated pose
    renderPointCloud(viewer, poses, "poses", Color(0,1,0), 8);
    renderPath(viewer, poses, "posePath", Color(0,1,0) );
    renderPointCloud(viewer, locator, "locator", Color(0,0,1), 6);
    renderPath(viewer, locator, "locPath", Color(0,0,1) );

    while (!viewer->wasStopped ())
    {
        viewer->spinOnce ();
    }

    return 0;
}
```
