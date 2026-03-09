# Solution: Creating ICP

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=-gXHKcujssw)

## Summary

**ICP Algorithm Summary**
==========================

This README file provides a summary of the Iterative Closest Point (ICP) algorithm, including key concepts, practical notes, and code patterns.

**Key Concepts**
---------------

* **KdTree**: A data structure used for efficient nearest neighbor search in high-dimensional spaces.
* **Nearest Neighbor Search**: The process of finding the closest point to a given point in a set of points.
* **Associations**: A vector of pairs of indices, where each pair represents a source point and its corresponding target point.
* **Centroids**: The mean position of all points in a set.
* **SVD (Singular Value Decomposition)**: A matrix factorization technique used to decompose a matrix into three matrices (U, Σ, V).
* **Rotation Matrix (R)**: A 3x3 matrix that represents a rotation transformation.
* **Translation Vector (T)**: A 3-element vector that represents a translation transformation.

**Practical Notes**
------------------

* To implement the ICP algorithm, you need to:
	+ Create a KdTree from the target point cloud.
	+ Iterate through all source points and find their nearest neighbors using the KdTree.
	+ Calculate associations between source and target points.
	+ Calculate centroids of source and target points.
	+ Use SVD to calculate rotation and translation matrices (R, T).
	+ Create a final transformation matrix by combining R and T.

**Code Patterns**
----------------

* Using Eigen library for matrix operations:
```cpp
Eigen::Matrix3f X;
Eigen::Matrix3f Y;

// Calculate centroids
for (int i = 0; i < pairs.size(); ++i) {
    X.col(i) = pairs[i].p1 - centroidX;
    Y.col(i) = pairs[i].p2 - centroidY;
}

// Calculate SVD
Eigen::JacobiSVD<Eigen::Matrix3f> svd(X * Y.transpose());
```
* Using KdTree for nearest neighbor search:
```cpp
pcl::KdTree<pcl::PointXYZ> kdtree;
kdtree.setInputCloud(targetPointCloud);
int index = kdtree.nearestNeighbor(sourcePoint, distance);
```

## Transcript

Now, let's go and check out the solution for Exercise 2 on creating ICP. Here's how you can complete the nearest neighbor function. What's first being done is we have that initTransform that we're transforming source by, so creating that new PointCloudT transformSource. Create a pcl KdTree and set its input to that target PointCloudT. Then we have our vector of associations and we want to fill that in.

One way of doing that could be to iterate through all the transformSource points. Then we have this index that's being incremented each time. Starting at zero, so that's the source points and we feed that into the KdTree. We have this point that we're iterating through. Then we have that distance parameter.

If it's not negative 1, if it's not exceeding this distance, if it's within the search radius, then we can push back that association of the point index that radius search finds, zero right here is very closest one. Otherwise, if it's negative 1, you can just push that back. That will fill in associations for all the corresponding source indices to target indices using that KdTree search. Then for doing pair points, we want to fill in these pairs. Yeah, that's the same idea here.

We have index starting at zero and increment that each time we're going to go through all the source points. But now what we're doing is, so we want to grab the points that those indices are representing. We're doing that directly right here in this for-loop, grabbing the source point. Yeah, we have this index and we can get this association. The i is going to be the association of that index.

At zero would association does that point have, that'll be i. Then we can just grab it from target, go ahead and directly access it with i. Then when we have that, so that's going to directly give us that PointT. Target was our PointCloudT. We can go ahead and render that.

Using this renderRay function, we can render those two points. Then we get this nice line segment showing in green here to connect those source and target points and seeing that association. Then in pairs, which is the thing we're after, pushing back that pair of points. We have the point x, y, 0 because we're just doing this in 2D. Then the association that came from here for x and y.

Then that'd allow us to complete pairs. Now we have a vector of pairs of the source point along with its target point. Now we have everything we need to start filling in ICP, which is the most involved function here. Let's go through that. The first thing we need to do is transform source by our starting pose, which is done with this in this transform 3D coming from helper.

This being in those parameters there to get our matrix. Then we go ahead and create this transform source by doing that transform point cloud function there that in the transform that we grabbed. Now we have transformSource. Then we go ahead and get those pairs just using our pair of points function where we have associations, we have the target, we have transformSource, and we can go ahead and start creating these matrices. Here's one way of doing this.

This is just using that Eigen matrix library. We know X and Y are those beginning matrices that when we calculate know that there are two by the number of points. We can just say, okay, pairs-size is the number of points. Now we've filled in X and Y, we also have the centroids, so we're just filling those in. We know there are two by one, initializing them with zero.

Then we can go ahead and calculate those by going through those pairs. We can tackle both of these at the same time. Summing up all those points from the source p1 and the target p2. So just sum all those up in their respective rows within that column, and then go ahead and divide it by the total number of pairs to get our overall centroids. Then I'm going to do something very similar to finish off X and Y.

Just grab those points directly in here from the pairs p1. x and go ahead and subtract the centroid. We have the X values, centroid X that p1. x. Then the bottom here we have the Y minus the centroid Y.

That is for the source, and then we have the target. Then we're just working with p2 and the target centroid. So we've created X and Y. Now it's just down to doing these equations, calculating S, X times Y transpose, calling svd to get our V and U. Then also this diagonal matrix.

We're looking at it in the classroom. We see that this two-by-two diagonal where the last element is something specific. To do that and just set the identity, and it's right here, it's just the size of V columns and the columns here. Well, those are both 2 by 2. Both U and V are 2 by 2.

So this is going to be 2 by 2. That'll work out. Then the set, the last element, you can just index into it, so.cols minus 1. We can index into that last diagonal part. Then it's equal to this V times U dot transpose, and then the determinant of all of that.

Now you can just directly calculate the rotation and translation by using that V times D times the U dot transpose for rotation. Then T is those centroids that we calculated earlier, then a Q minus R times P. Now we have the R and T. We can just create our final transformation matrix by putting those R and T in the correct corresponding parts of our 4 by 4 transformation matrix. Last but not least, to get that overall transformation movement.

Remember we moved source, we transform source by intTransform so we get the overall movement. We also include that by multiplying that and then transform by our transformation matrix. Then we have the full coverage of that transform. That's it.

## Additional Content

## Solution: Creating ICP
```
using namespace std;

#include

#include 
#include "helper.h"

#include 
#include 
using namespace Eigen;
#include 
#include    // TicToc

Pose pose(Point(0,0,0), Rotate(0,0,0));
Pose upose = pose;
vector associations;
vector bestAssociations = {5,6,7,8,9,10,11,12,13,14,15,16,16,17,18,19,20,21,22,23,24,25,26,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,62,63,64,65,66,67,68,69,70,71,72,74,75,76,77,78,79,80,81,82,83,84,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100,101,102,103,104,105,106,107,108,109,110,111,112,113,114,115,116,117,118,119,120,121,122,122,123,124,125,126,127,0,1,2,3,4,4};
bool init = false;
bool matching = false;
bool update = false;
void keyboardEventOccurred(const pcl::visualization::KeyboardEvent &event, void* viewer)
{

      //boost::shared_ptr viewer = *static_cast *>(viewer_void);
    if (event.getKeySym() == "Right" && event.keyDown()){
        update = true;
        upose.position.x += 0.1;
      }
    else if (event.getKeySym() == "Left" && event.keyDown()){
        update = true;
        upose.position.x -= 0.1;
      }
      if (event.getKeySym() == "Up" && event.keyDown()){
        update = true;
        upose.position.y += 0.1;
      }
    else if (event.getKeySym() == "Down" && event.keyDown()){
        update = true;
        upose.position.y -= 0.1;
      }
    else if (event.getKeySym() == "k" && event.keyDown()){
        update = true;
        upose.rotation.yaw += 0.1;
        while( upose.rotation.yaw > 2*pi)
            upose.rotation.yaw -= 2*pi;  
      }
    else if (event.getKeySym() == "l" && event.keyDown()){
        update = true;
        upose.rotation.yaw -= 0.1;
        while( upose.rotation.yaw < 0)
            upose.rotation.yaw += 2*pi; 
      }
    else if (event.getKeySym() == "space" && event.keyDown()){
        matching = true;
        update = false;
      }
    else if (event.getKeySym() == "n" && event.keyDown()){
        pose = upose;
        cout << "Set New Pose" << endl;
      }
    else if (event.getKeySym() == "b" && event.keyDown()){
        cout << "Do ICP With Best Associations" << endl;
        matching = true;
        update = true;
      }
}

double Score(vector pairs, PointCloudT::Ptr target, PointCloudT::Ptr source, Eigen::Matrix4d transform){
    double score = 0;
    int index = 0;
    for(int i : pairs){
        Eigen::MatrixXd p(4, 1);
        p(0,0) = (*source)[index].x;
        p(1,0) = (*source)[index].y;
        p(2,0) = 0.0;
        p(3,0) = 1.0;
        Eigen::MatrixXd p2 = transform * p;
        PointT association = (*target)[i];
        score += sqrt( (p2(0,0) - association.x) * (p2(0,0) - association.x) + (p2(1,0) - association.y) * (p2(1,0) - association.y) );
        index++;
    }
    return score;
}
vector estimations;

vector NN(PointCloudT::Ptr target, PointCloudT::Ptr source, Eigen::Matrix4d initTransform, double dist){

    PointCloudT::Ptr transformSource (new PointCloudT); 
      pcl::transformPointCloud (*source, *transformSource, initTransform);

    pcl::KdTreeFLANN kdtree;
    kdtree.setInputCloud (target);

    vector associations;

    int index = 0;
    for(PointT point : transformSource->points ){

        vector pointIdxRadiusSearch;
          vector pointRadiusSquaredDistance;
        if ( kdtree.radiusSearch (point, dist, pointIdxRadiusSearch, pointRadiusSquaredDistance) > 0 )
         {
            associations.push_back(pointIdxRadiusSearch[0]);
        }
        else{
            associations.push_back(-1);
        }
        index++;
    }

    return associations;
}

vector PairPoints(vector associations, PointCloudT::Ptr target, PointCloudT::Ptr source, bool render, pcl::visualization::PCLVisualizer::Ptr& viewer){

    vector pairs;

    int index = 0;
    for(PointT point : source->points ){
        int i = associations[index];
        if( i >= 0)
        {
            PointT association = (*target)[i];
            if( render){
                viewer->removeShape(to_string(index));
                renderRay(viewer, Point(point.x, point.y,0), Point(association.x, association.y,0), to_string(index), Color(0,1,0));
            }
            pairs.push_back(Pair(Point(point.x, point.y,0), Point(association.x, association.y,0)) );
        }
        index++;
    }
    return pairs;
}
```
### `ICP` function
```
Eigen::Matrix4d ICP(vector associations, PointCloudT::Ptr target, PointCloudT::Ptr source, Pose startingPose, int iterations, pcl::visualization::PCLVisualizer::Ptr& viewer){

      // align source with starting pose
      Eigen::Matrix4d initTransform = transform3D(startingPose.rotation.yaw, startingPose.rotation.pitch, startingPose.rotation.roll, startingPose.position.x, startingPose.position.y, startingPose.position.z);
      PointCloudT::Ptr transformSource (new PointCloudT); 
      pcl::transformPointCloud (*source, *transformSource, initTransform);

    vector pairs = PairPoints(associations, target, transformSource, true, viewer);

    //cout << "score is " << Score(pairs, Eigen::MatrixXd::Identity(4,4) ) << endl;

    Eigen::MatrixXd X(2,pairs.size());
    Eigen::MatrixXd Y(2,pairs.size());
    Eigen::MatrixXd P(2,1);
    P << Eigen::MatrixXd::Zero(2,1);
    Eigen::MatrixXd Q(2,1);
    Q << Eigen::MatrixXd::Zero(2,1);

    for(Pair pair : pairs){
        P(0,0) += pair.p1.x;
        P(1,0) += pair.p1.y;

        Q(0,0) += pair.p2.x;
        Q(1,0) += pair.p2.y;
    }
    P(0,0) = P(0,0)/pairs.size();
    P(1,0) = P(1,0)/pairs.size();

    Q(0,0) = Q(0,0)/pairs.size();
    Q(1,0) = Q(1,0)/pairs.size();
    int index = 0;
    for(Pair pair : pairs){
        X(0,index) = pair.p1.x - P(0,0);
        X(1,index) = pair.p1.y - P(1,0);

        Y(0,index) = pair.p2.x - Q(0,0);
        Y(1,index) = pair.p2.y - Q(1,0);
        index++;
    }

    // compute best R and t from using SVD
    Eigen::MatrixXd S  = X * Y.transpose();
    JacobiSVD svd(S, ComputeFullV | ComputeFullU);
    Eigen::MatrixXd D;
    D.setIdentity(svd.matrixV().cols(), svd.matrixV().cols());
    D(svd.matrixV().cols()-1,svd.matrixV().cols()-1) = (svd.matrixV() * svd.matrixU().transpose() ).determinant();

    Eigen::MatrixXd R  = svd.matrixV() * D * svd.matrixU().transpose();
    Eigen::MatrixXd t  = Q - R * P;

    Eigen::Matrix4d transformation_matrix;
    transformation_matrix << Eigen::MatrixXd::Identity(4,4);

    transformation_matrix(0,0) = R(0,0);
    transformation_matrix(0,1) = R(0,1);
    transformation_matrix(1,0) = R(1,0);
    transformation_matrix(1,1) = R(1,1);
    transformation_matrix(0,3) = t(0,0);
    transformation_matrix(1,3) = t(1,0);

    //cout << "score is " << Score(pairs, transformation_matrix ) << endl;

    //cout << transformation_matrix << endl;

    estimations = pairs;
    transformation_matrix =  transformation_matrix * initTransform;
      return transformation_matrix;

}

int main(){

    pcl::visualization::PCLVisualizer::Ptr viewer (new pcl::visualization::PCLVisualizer ("ICP Creation"));
      viewer->setBackgroundColor (0, 0, 0);
      viewer->addCoordinateSystem (1.0);
    viewer->registerKeyboardCallback(keyboardEventOccurred, (void*)&viewer);

    // Load target
    PointCloudT::Ptr target(new PointCloudT);
      pcl::io::loadPCDFile("target.pcd", *target);

    // Load source
    PointCloudT::Ptr source(new PointCloudT);
      pcl::io::loadPCDFile("source.pcd", *source);

    renderPointCloud(viewer, target, "target", Color(0,0,1));
    renderPointCloud(viewer, source, "source", Color(1,0,0));
    viewer->addText("Score", 200, 200, 32, 1.0, 1.0, 1.0, "score",0);

      while (!viewer->wasStopped ())
      {
        if(matching){

            init = true;

            viewer->removePointCloud("usource");

            Eigen::Matrix4d transformInit = transform3D(pose.rotation.yaw, pose.rotation.pitch, pose.rotation.roll, pose.position.x, pose.position.y, pose.position.z);
            PointCloudT::Ptr transformed_scan (new PointCloudT);
              pcl::transformPointCloud (*source, *transformed_scan, transformInit);
            viewer->removePointCloud("source");
              renderPointCloud(viewer, transformed_scan, "source", Color(1,0,0));

            if(!update)
                associations = NN(target, source, transformInit, 5);
            else
                associations = bestAssociations;

            Eigen::Matrix4d transform = ICP(associations, target, source, pose, 1, viewer);

            pose = getPose(transform);
              pcl::transformPointCloud (*source, *transformed_scan, transform);
            viewer->removePointCloud("icp_scan");
              renderPointCloud(viewer, transformed_scan, "icp_scan", Color(0,1,0));

            double score = Score(associations,  target, source, transformInit);
            viewer->removeShape("score");
            viewer->addText("Score: "+to_string(score), 200, 200, 32, 1.0, 1.0, 1.0, "score",0);
            double icpScore = Score(associations,  target, source, transform);
            viewer->removeShape("iscore");
            viewer->addText("ICP Score: "+to_string(icpScore), 200, 150, 32, 1.0, 1.0, 1.0, "iscore",0);

            matching = false;
            update = false;
            upose = pose;

        }
        else if(update && init){

            Eigen::Matrix4d userTransform = transform3D(upose.rotation.yaw, upose.rotation.pitch, upose.rotation.roll, upose.position.x, upose.position.y, upose.position.z);

            PointCloudT::Ptr transformed_scan (new PointCloudT);
              pcl::transformPointCloud (*source, *transformed_scan, userTransform);
            viewer->removePointCloud("usource");
            renderPointCloud(viewer, transformed_scan, "usource", Color(0,1,1));

            vector pairs = PairPoints(associations, target, transformed_scan, true, viewer);

            double score = Score(associations,  target, source, userTransform);
            viewer->removeShape("score");
            viewer->addText("Score: "+to_string(score), 200, 200, 32, 1.0, 1.0, 1.0, "score",0);

            update = false;

        }

          viewer->spinOnce ();
      }

    return 0;
}
```
