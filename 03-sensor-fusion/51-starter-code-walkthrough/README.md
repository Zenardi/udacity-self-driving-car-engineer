# Starter Code Walkthrough

> Part of: **Mid-Term Project: 3D Object Detection**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=JLKDm3J4Ojs)

## Summary

**Introduction**
This README file provides an overview of the `loop_over_dataset` codebase, which is a key component of the midterm and final projects. The codebase is designed to process the Waymo open dataset, perform 3D object detection, and track objects over time.

**Key Concepts**

* **Waymo Open Dataset**: A large dataset of lidar and camera data collected from self-driving cars.
* **3D Object Detection**: The process of detecting objects in 3D space using lidar and camera data.
* **Tracking**: The process of tracking objects over time, including removing false positives and phantoms.
* **Bird's Eye View (BEV) Map**: A 2D representation of the scene from a bird's eye view perspective.
* **Performance Evaluation**: Metrics used to evaluate the performance of object detection and tracking algorithms.

**Practical Notes**

* The codebase is structured into several folders, including `dataset`, `image`, `miscellaneous`, `results`, `solution`, and `student`.
* The `student` folder contains exercises that need to be implemented by the student, including visualization routines for showing point clouds and identifying objects.
* The `tools` folder contains packages used from third parties, such as OpenCV and Waymo simpler reader.
* The `loop_over_dataset` function is a key component of the codebase, responsible for processing the Waymo open dataset and performing 3D object detection and tracking.

**Code Structure**

The code structure is as follows:

```
project/
dataset/
image/
miscellaneous/
results/
solution/
student/
objdet_pcl.py
tools/
...
loop_over_dataset.py
```

Note that this is a simplified representation of the code structure, and there may be additional files and folders not shown here.

**Key Functions**

* `loop_over_dataset`: The main function responsible for processing the Waymo open dataset and performing 3D object detection and tracking.
* `objdet_pcl.py`: A file containing exercises that need to be implemented by the student, including visualization routines for showing point clouds and identifying objects.
* `show_pcl`: A function used to visualize point clouds.

**Tips and Advice**

* Make sure to read through the code carefully and understand the structure and organization of the project.
* Pay attention to the comments and docstrings in the code, which provide additional information about the functions and variables used.
* Start by implementing the exercises in the `student` folder, such as visualization routines for showing point clouds and identifying objects.

## Transcript

This walkthrough, I'm going to familiarize you with a codebase. You need to not only conduct the midterm project, but also the final project. I'm not going to talk about the content of the final project, which is about multi-target tracking and common filtering. This is [inaudible] job to do this. But nonetheless, I will introduce you to the basic structure of the overall main program, which also contains the functionality of the final project.

Let's start with this file here. I'm sure you have already looked at the video walking you through the basic loop.py file which you have been using for the exercises and also for the examples. The structure, the basic structure is the same here. You can find the same imports at the top, which I've talked about before, the OpenCV, system import, and so on and so forth. The Waymo open data set reader which we are using in order to process the Waymo open data set frames.

Then we have some new imports here, which are the imports for the 3D object detection, which is my responsibility. You will of course note that the solution here is different from what you have. You have student dot objdet underscore PCL imports, which means that you actually have to fill in the solution code in order for the program to run correctly. But as I want to execute this to show you how it should look like, I am going to use the solution import here. Okay.

There's also some imports used for tracking, which is [inaudible] part again, but in the same manner as I am changing this to student once we have gone through a code, [inaudible] is going to change this one here to student as well. Then you have the loading functionality for selecting a certain Waymo file, which is the same as before, sequence one, sequence two and sequence three. Also, you can select the frames which should be processed here. Now, we come to the first difference between basic loop and loop over data set. We're going to initialize the object detection here.

This is actually a place where you can select the model which should be used. The pre-set model is going to be darknet. Another model which your job will be to implement or to integrate into this code here is the FPM resonant. This is also the model which you should be using when you are conducting the final project. But for now, it's darknet.

Darknet is the same as complex yellow. This is simply the model name. But if you select darknet, you are running the complex yellow detection network here. In order to check if everything is running smoothly and correctly, you can decide to use the Waymo ground truth labels as actual objects. This would be a perfect world with perfect objects, perfect detections.

This is of course set to false, but if you want to test something, for example, when you are conducting the performance evaluation, if you set this one here to true, the performance evaluation obviously should return a 100 percent score in all measures you are implementing. This is for debugging purposes for your convenience only. Also, the safe results flag here. If you set this to True, the system actually pre-computes binaries and puts them in a folder. Which one is something I will show you in a few minutes.

But if you set this one here to True, all the steps which you have implemented until this point, are pre-computed and saved to file, which is, I think a convenient thing which you can do in order to, let's say you have solved the first three exercises and are working on the fourth, and because processing exercises one, two and three takes time, you pre-compute these intermediate steps and then simply load the results and use them as input for step four, exercise number four. This also simply saves you time. This is the switch which you need to change in order to do that. Initializing tracking is something which [inaudible] is going to talk about. This one here is very important.

It's the selective, execution, and visualization. These lists here, exit detection and tracking and visualization, are for you to select which part will be actually computed based on your code or which will be pre-loaded from file. Let's remove all of these strings here for now and have an empty list. The options are available here for your convenience. For example, if you want to compute the bird's eye view from the point cloud, which is the significance behind this string here.

If you want to run this function, actually, you can simply copy this one here, put it here, and then this function will be executed. For now, of course, the system is going to use the solution code. But once I changed this package import to Student, the system is going to call the function which is related to this string here and expects you to have done the actual implementation. If you are working on this exercise here, related to the string, put it here, and if you remove it, the system is going to use a pre-saved binary, which we have provided you with, so you can take a look at how the result should look like. If everything is empty here, the system is going to use pre-computed binaries, assuming of course, that the pre-computed binaries are in the correct place and that you have selected the correct sequence here for those binaries.

Now once we have done this, you can again select the number of milliseconds or the system waits between processing two frames. Zero means we are waiting for you to press a key on the keyboard, Space or Enter, it doesn't matter. We're going to leave it at this to better show you what's going on. Okay, then we have the main loop again, the infinite loop which is only broken once the last frame has been reached and the system has tried to go one step further then this stop iteration is called the same as in basicloop.pi. Then we process the different waymo frames, also same code as before.

Frame contains all the data for the current frame count, frame number q, frame number 2 and so on, so forth. This is where all the information is. Then we come to the actual 3D object detection. The first step is to extract the calibration data of the lidar and also of the front camera from the current frame. Therefore, we need to lidar name and the camera name.

In case you're wondering why we have these error squills under dataset_p2, this is something related to the input path of the intellisense plug-in of Visual Code and the content is actually there. I don't know why it shows this error, it might show the same error for you on your system. Don't bother with this error here, Class 'LaserName' has no 'TOP' member it says. Actually, it does have a top member so simply ignore it. We're loading the lidar name for the top lidar sensor, which is the one on top of the waymo vehicle roof.

Then we load the front camera, this one here. Then we load the lidar calibration also using a waymo utility from the simpler waymo reader and by passing it the actual calibration information from the frame. Also, we tell the system which lidar sensor to load. The same for the camera calibration. If the load image string has been put into the execution list, here we can tell the system to also load the camera image.

Let's progress through the first step which is about loading the actual Lidar Point Cloud from arrange image. So if you put this string here into the execution list, then the system tries to call the pcl_from_range_image function and then simply loads the point cloud from the range image. If you do not do this, the system will load a pre-computed point cloud from file and it will use this function to do so, which is one of the helper functions which we provided you with for convenience. These strings here are the ones which you put in to for example, execution list for tracking, for object detection or also for visualizing. Then we come to the second step which is about computing the bird's eye view map, the BV map.

Actually, this is one of the first exercises which you need to work on. bev_from_pcl is the function name and if you want to go into these functions, I will show you in a few minutes where you can actually find this but first, let's continue the walkthrough. Again, if you do not put this string here into the execution list, the system will assume that you want to load it from file. Then comes the 3D object detection as the next step. Again, we have a function here which you need to work on, actually this one is not something which you need to work on.

It's a convenience function which comes pre-shipped so to speak, we wrote it for you. What you need to actually do is, yeah, this is the one which is used when you decide to use the object labels as objects as I told you before. But in case you decide not to do this, this is the string you must be looking for. If you decide to detect the actual objects by yourselves, then you need to work on this function here, det.detect_objects. This is in the student code section and you need to implement the steps which are outlined there in this function here.

Then we come to the part where the object labels are validated. I'm going to talk a little bit about label validation in one of the lectures so I'm not going to repeat myself here other than saying that invalid label flags we have for each preloaded ground truth label from the waymo datasets, and information about whether it is relevant to us in terms of should we use it for assessing the detection performance or not? Then we come to the performance evaluation part. This is the place where we collect some initial performance measurements in terms of true positives, true negatives, and so on and so forth for each and every frame. We are accumulating this information here in this structure, we are simply appending for every frame, we are appending the performance measures to this structure here.

Then at the end of the loop when all frames have been processed, this accumulative structure here is used to make the overall performance assessment. Then we get to the visualization part for the object detection in this case, and this is something where you can simply take a look at the output of the various steps you have been implementing to see how they look. Let's now execute the code for the very first time, and I would like to show you the objects and labels in the bird's eye view. If I want to visualize the actual objects which have been detected by the deep learning framework and also the ground truth labels which have been shipped with a way more dataset, I simply need to copy this code here, scroll up to the execution list in the visualization part and simply put this string here. Show_objects_and_labels_in_bev.

As those lists are empty, the system is simply loading the information about all the intermediate steps from the pre-computed files, and what we're going to see here are the pre-computed results we provided you with when we shipped you this report here. In order to run it, I'm always using the Debug option, and as you can see, we have a visualization window. In this window you can see the bird's eye view of the latter point cloud, and the various colors you can see here are explained in detail in the respective lessons. What you can also see here barely are several rectangles, green one underneath a red one. The green rectangles are actually the ground truth labels loaded from the way more data-set, it also states this year in the caption of the window labeled green and also detected objects in red, and this is another detected object.

The blue line here indicates the front of a vehicle, and here where my mouse currently moves, you can see the actual back of the vehicle in front of us driving into this direction here, and so it makes sense for the blue line to be at the other end. If I stepped through the sequence once more, you can see on the right side in the terminal that we are stepping through the frames now. Here's actually a false positive, it's a detection where there's no actual vehicle, but the system thought it found something in the bushes on the right-hand side. Still we do have the actual vehicles, these are both true positives, but this detection here is a phantom, so to speak. It's the job of the tracking framework to remove such detections here from the actual track list so that the system does not involuntarily break on, for example, a phantom bush which actually does not exist on the real world.

Let's step through this, and as you can see now, the bush has disappeared. We have another vehicle coming in at the top which is not yet detected another phantom, and so we can simply step through all the various sequences here and the various frames here and process it one by one. Once you are finished with processing, you will arrive at the end of the loop, which is about performance computation. If you put this string here into the execution list, show_detection_performance, you get into the file compute underscore performance starts, and this is where you put in all the accumulated frame wise performance measures which you collected through the execution of the main loop. That's basically all there is to say currently about this file here, loop_over_dataset, let's now take a look at the structure.

One word about this structure which you can see here, yours will look a little bit different because this is my instructor working directory here. You will not have all these folders up here, the only thing interesting to you now is the project folder. This one here, and inside the project folder, there are several sub-folders. For example, dataset, which is where you put the various way more open dataset training files which are downloaded. Then there is the image folder which at this point contains some visualization graphic arts for the GitHub repo.

This is nothing which you need to be concerned about. We have the miscellaneous folder which contains the helper functions which I have been talking about. These are functions which you will not be implementing yourself. You will also not be looking at the implementation details if you do not want to. This is something which you simply use.

Inside the results folder, this is the folder which we actually already took a look at when the main loop crashed because a certain file was not in this folder here, and here are all the various binaries which you need to download and put there in order to be able to for example, use a visualization and look at how it's supposed to look when you are in the process of implementing a certain exercise. Then we have the solution folder, and inside the solution folder, this is the instructor code with all the implemented exercises which you will not be having. So you might have this folder, but it's going to be empty, or you might not even see this folder here. What you will be working on is the student folder. Inside the student folder for example, let's take a look at maybe this one here objdect_pcl.py.

Let's miniaturize this one here, and inside this folder, for example, you will need to work on the visualization routines for showing an actual point cloud and the identification number, the ID for this exercise here is something you can look for in the actual lessons, inside the Udacity framework. ID_S1_EX2 means this is the exercise which you need to perform now. It has a starting position, it also has an end position, and in-between, those are the various steps you need to implement. Step 1 would be to initialize the framework, open3d with key callback and then create a window and so on and so forth, and at the end, visualize the point cloud and keep the window open until the right-arrow key is pressed. This is a small exercise which teaches you how to visualize a point cloud, rotate it, zoom into it for close inspection, and get yourself familiarized with working with lidar data.

If we scroll down, we find another exercise, this one here. It's exercise number 1 in lesson number 2, and this means that you need to compute the bev-map, the bird's eye view map, by performing a number of steps, four in total. Once you have completed this task here, you will be able to visualize a point-cloud using the function show_pcl, which we just looked at. Then you will compute the intensity layer of the bev-map by implementing these steps here, and so on and so forth. There's also some code here which has been pre-filled by us.

So you do not have to write every line by yourself, but instead, we only have selected a certain number of steps which you need to implement in order to limit the scope and the workload on you when implementing these exercises here. That's about all you need to know about how to look for exercises. Let's go back to the file structure. Let's close the student folder and move forward to the tools folder. This is the folder where we included packages which we have used from third parties freely available under for example, MIT license and other licenses which make the code free for working with object detection models, for actually performing object detection using a deep running framework.

This is codebase we took from GitHub and also the Waymo simpler reader, which I already talked about several times, which facilitates the use of the Waymo open dataset. Basically, that's it. That's all you need to know in order to work on the midterm project, and also maybe let's go back into loop_over_dataset once more and close this view here also on the final project, because once this function here has been executed, it's where all the performance measurements for each frame are accumulated, and once all the visualization functions which you want to call have been called, then we get to the actual tracking part. This is the part where the midterm project ends and the final project starts, but this function, or this code here is something Anthea it is going to share with you in her introduction of the final project.

## Additional Content

## Starter Code Walkthrough
### Configurations
### The Main Loop: 3D Object Detection
### Visualization
### Project Structure
