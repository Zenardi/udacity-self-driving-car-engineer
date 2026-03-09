# Templates and Different Point Cloud Data

> Part of: **[Optional] Intro to PCL**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=3Hws520ZZGw)

## Summary

**README: Understanding Point Cloud Templates**

This README provides an overview of the key concepts and practical notes related to point cloud templates in 3D computer vision.

### Key Concepts

* **Templates**: A template is a way to define reusable code that can work with different types of data. In the context of point clouds, a template specifies the type of point cloud being used.
* **PointT**: `PointT` is a variable that can hold the place of any type of point cloud (e.g., `PointXYZ`, `PointXYZI`, etc.). It's defined as a template parameter in the `pcl::PointCloud` class.
* **PCL PointCloud PointT pointer**: A `PCL PointCloud PointT pointer` is a typedef for a `boost::shared_ptr`. This type of pointer is used to manage memory and ensure that point clouds are properly deallocated when no longer needed.

### Practical Notes

When working with templates in point cloud processing, it's essential to understand the difference between values and types. The compiler may assume a template parameter is a value unless explicitly declared as a type using a `typedef` or a type name (e.g., `PointT`). This can lead to compilation errors if not handled correctly.

To avoid these issues, use the following pattern:

* Define a `typedef` for the point cloud type (e.g., `typedef pcl::PointCloud<pcl::PointXYZ> PointCloudXYZ;`)
* Use this `typedef` as the template parameter in your code (e.g., `pcl::PointCloud<PointT> cloud;`)
* When using pointers, use the `PointT` type name to specify that it's a type (e.g., `pcl::PointCloud<PointT>* cloud_ptr;`)

## Transcript

<v English>Now, let's go ahead and talk about templates.</v> <v English>This was coming in effect when we're creating that PointCloud from "Scan."</v> <v English>So basically, we're saying that earlier there's many different kinds of PointClouds.</v> <v English>In our case, we are using the PCL PointXYZ.</v> <v English>So in this template,</v> <v English>it's being held in these arrow brackets right here.</v> <v English>It's like an argument saying.</v> <v English>"Okay, we're working with a PCL PointCloud,</v> <v English>and it's of type PCL PointXYZ."</v> <v English>In the future, you could have one that is PointXYZI or PointXYZ RGB.</v> <v English>But that's what the template is</v> <v English>and it's great because it's going to allow us to do reusable code.</v> <v English>So in our case,</v> <v English>we're using this PointXYZ.</v> <v English>Later, we'll be looking at PointXYZI.</v> <v English>One thing that take notice of,</v> <v English>is let's look at how those templates being defined back in this point process Clouds.cpp.</v> <v English>So if we look at this this file,</v> <v English>we can see a lot of places where we have template.</v> <v English>So template is being set up with this type name PointT.</v> <v English>Basically, what that is saying is that PointT is variable</v> <v English>and it can hold the place of any of these different kinds of PointClouds.</v> <v English>So let's look at an example function like,</v> <v English>let's look at FilterCloud for instance.</v> <v English>If we check that out and we have that template being setup right above it.</v> <v English>Let's see where that PointT is being used.</v> <v English>So here's that PointT being used right here in places as PCL PointCloud.</v> <v English>So now, you can work with different types of PointClouds.</v> <v English>But we'll notice that we have this type name here.</v> <v English>This quiz will motivate or help us understand why we're using this type name.</v> <v English>We're actually using this pointer type here for this cloud.</v> <v English>What does that exactly mean.</v> <v English>Well, let's look up the definition for this.</v> <v English>So if we go back to the classroom and we will look at</v> <v English>templates in different PointCloud data.</v> <v English>We have some definitions here for template.</v> <v English>Also, we have this documentation now help with this quiz below.</v> <v English>What is a PCL PointCloud PointT pointer?</v> <v English>Well, it's a typedef boost shared pointer.</v> <v English>So this quiz then is asking.</v> <v English>What do you think a PCL PointCloud PointT pointer is?</v> <v English>Is it a value or a type and that documentation will help you answer this.</v> <v English>It's a typedef boost shared pointer.</v> <v English>So what do you think it is?</v> <v English>It's a little bit of a tricky question but then we'll</v> <v English>talk about it and why it's important in our case,</v> <v English>and how does it relate back to type name in process PointCloud.</v>

All right. So this typedef boost shared pointer is actually going to be a type, and why that is important here is, when the compiler is looking at templates, so would reference back here when we are in processPointClouds.cpp, when it sees as value that's going to be using a template inside, it doesn't actually have enough information to figure out if it's going to be a value or a type, and so it'll actually assume that it's a value. Unless you use this type name which is specifically saying no, this is actually going to be a type. So what does that mean exactly? Well, it means that if it looks at this and the compiler thinks it's a value, it's actually going to have a compilation error.

So you could try this out, if you take this type name away, because the compiler is thinking it's a value when it's really a type. So by having this type name, you're actually telling the compiler, no, wait. This actually really is a type, and then it'll be able to compile successfully. What this just means then is in the processPointClouds.cpp file, any place that you have this extension of pointer on this PCL pointCloud template, you'll want to use a type name. So kind of looking at this file, you'll see this pattern of where you're using these different type names whenever you have this pointer extension.

So it will be-

## Additional Content

## Templates and Different Point Cloud Data
### Why Use Templates?

The lidar scan function used previously produced a pcl PointCloud object with pcl::PointXYZ points. The object uses a [template](http://www.cplusplus.com/doc/oldtutorial/templates/) because there are many different types of point clouds: some that are 3D, some that are 2D, some that include color and intensity. Here you are working with plain 3D point clouds so PointXYZ is used. However, there are also points with an intensity component as well.

Instead of defining two separate functions one with an argument for PointXYZ and the other for PointXYZI, templates can automate this process. With templates, you only have to write the function once and use the template like an argument to specify the point type. 

### Templates and Pointers

If you haven’t used templates with pointers before, you may have noticed in the code that `typename` is used whenever a pointer is used that depends on a template. For example in the function signature here: 

```cpp
typename pcl::PointCloud

::Ptr ProcessPointClouds::FilterCloud(typename pcl::PointCloud::Ptr cloud, float filterRes, Eigen::Vector4f minPoint, Eigen::Vector4f maxPoint)
``` 

The reason for this is the following: Given a piece of code with a type name parameter, like `pcl::PointCloud::Ptr`, the compiler is unable to determine if the code is a value or a type without knowing the value for the type name parameter. The compiler will assume that the code represents a value. If the code actually represents a typename, you will need to specify that.

Test your own intuition with the quiz below. You can use this [documentation](https://pointclouds.org/documentation/classpcl_1_1_point_cloud.html) for help.
### Explanation
