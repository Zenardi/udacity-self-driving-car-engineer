# Exercise: Lidar Data in the Waymo Dataset

> Part of: **The Lidar Sensor**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=9eZCCmMwPmM)

## Summary

**Summary of Basic Loop.py File**

The `basic_loop.py` file is used for executing exercises and examples throughout the course. It prepares students for the midterm and final projects by demonstrating the basic structure of processing frames from the Waymo Open Dataset.

**Key Concepts:**

* **Waymo Open Dataset**: a dataset used for training and testing object detection and tracking algorithms
* **Simple Waymo Package**: a third-party package that simplifies loading data from the Waymo Open Dataset
* **EasyDict**: a convenient way to parameterize object detection and tracking algorithms
* **Exception Handling**: using try-except blocks to handle exceptions, such as `StopIteration`, when iterating over frames
* **Loop Structure**: a basic loop structure for iterating over frames in the Waymo sequence
* **Visualizations**: displaying camera images, range images, and other visualizations using functions like `display_image` and `print_pitch_resolution`
* **Exercise Directories**: importing exercise directories, such as `L1 examples` and `L1 exercises`, to execute specific exercises

**Practical Notes:**

* To use the `basic_loop.py` file, you need to have the necessary packages installed, including NumPy, math, OpenCV, EasyDict, and the Simple Waymo Package.
* The file uses a loop structure to iterate over frames in the Waymo sequence. You can modify this loop to execute specific exercises or examples by commenting out or uncommenting code blocks.
* To display visualizations, you need to use functions like `display_image` and `print_pitch_resolution`, which are located in the exercise directories.
* The file also includes exception handling using try-except blocks to handle exceptions when iterating over frames.

## Transcript

Welcome to this walk-through through the file basic_loop.py, which is used for executing exercises and examples over the course of the lessons and of the course. The nice thing about this file basic_loop.py is that it prepares you for the actual midterm project as well as for the final project. Because the basic structure of processing way more frames of opening the various elements and then piping them into various functions is actually the same for the midterm project and the same for the final project. By paying close attention to the structure which I'm going to show you now also helps you in preparation for these two projects. Let's start right away with some general inputs which we require for the course.

Those are the operating system package. This is package NumPy, math, the OpenCV, this one here, also EasyDict. This one is required for setting up a very easy and convenient to use conflict structure which we need to parameterize the object detection algorithm and also the tracking algorithm later on, so this one is something which we make use of quite a lot here. Then we set the current working directory and this one here is really interesting because it's the inputs for the Waymo Open Dataset reader, the simple Waymo Open Dataset reader. This is actually a third-party package which is freely available on GitHub and which does away with several huge imports that are required by the official Waymo release.

It's really convenient and very easy and straightforward to use. This is why we chose to use this one here instead of the official Waymo Open Dataset reader. This is the input for the tools which are shipped along with this package here. Then we have some miscellaneous project-related inputs, for example, for the object detection and also some helper tools for loading and saving data. These are tools which you do not need to work on, but which we instead created for you to make some steps a little bit more convenient.

Sometimes it's also third-party applications which we integrated into the project. These are all inside the miscellaneous package here. Then we add some exercise directories, for example, for lesson 1 and lesson 2. If you pay close attention, you will see that I have chosen to import the solution sub-directory here, which is something which you do not have access to. Your code will have starter instead of solution here, but I chose to conduct this first walk-through using the solution import because I want to actually execute some of the exercises to show you how it should look like.

In order for them to work, I need to import the solution code here. You will have starter here and you will have to implement all the exercises and examples step by step. That's everything you need to know about the inputs. Let's talk about setting the parameters and then performing some further initializations here. This first part here is really important because using these lines of code here, you actually select a file name from the Waymo open dataset.

It has this lengthy number here, and you can actually download this by yourself. How to do this is the content of one of the actual lectures of all the chapters. But we assume that you have downloaded these three files locally to your machines if you execute on your personal computer, and we have to rely on you using this actual string here or this actual file here, and use it as a Sequence number 1. Because when we tell you, let's say use Sequence number 1, frames 10-15, this is what you need to do. Uncomment this line here, and then put frames 10-15 in this small list here.

If we instead say, okay, let's execute frames 0-200, this is what you need to do. If we want you to choose, let's say Sequence number 2, comment this out, comment this one in here, and then there you have at Sequence number 2, and we again rely on you to have downloaded this file to your computer. How to get this is very conveniently explained to you in one of the chapters. But let's revert this to using Sequence number 1, and also frames, let's say 0-5 or 0-10 maybe. Here we go.

The vis_pause_time actually lets you pause between visualizations, for example, to wait for a key press if you put zero there which is what we will do now, the system pauses the execution and waits for you to press the space-bar or enter. If we put a 10 there, it's going to wait for 10 milliseconds before it shows you the next frame. To show you what's actually happening, let's revert this to zero and stop the system after we have looked sufficiently long enough at a certain visualization for example. Now we come to the actual loop over all the different frames of the Waymo sequence we're currently loading. The loop executes here while this isn't infinite loop, while the system tries to load a certain frame.

This is a convenient iterator which we are using to iterate over the content of the data file which we have been loading up here. This one here, it actually loads the data file using a function called Waymo data file reader which is within the simple Waymo package which I talked about, and this is used to iterate over all the Waymo frames. Each time this line here is executed, you will get another frame. Then we increment the frame count and print the currently used frame which is being processed. That's the major loop.

Let's scroll down to the bottom. Here you find this exception which I was talking about earlier. This is the StopIteration exception. Once the last frame number has been reached, or the one after that actually, when there is no next frame to iterate over, then this exception is thrown and the system terminates the infinite loop and this is the end where all the frames have been processed. There's actually one exercise which relies on you to execute a certain number of frames, which is about performance evaluation.

This one here, and this is called once all the frames have been processed, once all the information on frame, once performance has been gathered, and this function shall be called. Then this is part of a Lesson 2 exercise and we're going to talk about this later on. Let's scroll upwards again, and go back to the point in the code where the current frame is being processed, and this is the place where all the Lesson 1 exercises and examples live between these two statements here. These are all the exercises and examples for Lesson 1. For example, if we want to, let's say display the camera image, what you need to do is, this is an example, not an exercise.

You can simply comment this one herein and if you want to know how this actually works, simply go to definition. No definition found, but luckily I have this one open here. Let's go into L1 examples, let's select the function display image. Here is the actual code that pulls the image from the Waymo frame, converts the actual image into a specified format, and RGB format, then resizes the image and then displays the image. That's how it's working.

Let's run the code. In order to execute code, I always use the debugging option here. Let's open this and simply press on this green arrow here, and on the right-hand side you can see the terminal where the entire program is now executed, and here the statement processing frame zero is output by line number 95 in this case and prints the frame number. What you can see here is the actual visualization. We have been calling L1 examples display image, and this is the image as seen by the Waymo front camera.

If I press space, you can see that the frame number one has now been processed. The image has changed, and when I continue pressing here, you can see that I can step by step, iterate through the sequence until the last frame has been reached, which I have set at this position here, and the loop then terminates and quits the program. This is basically the structure of the basic loop file which helps you iterate over Waymo frames, and as I told you if you actually want to execute a certain example, simply comment in or comment out the code here in the main loop, and this is all you need to know about this. If you want to conduct an actual exercise, what you also need to do, same to the example, simply comment in for example, L1 exercise print pitch resolution. This is the first or the second exercise which you need to conduct here.

The first is print number of vehicles, but let's stick with this one here, for example, open the L1 exercises.py file, then you can also go to the respective function which is called print pitch resolution, and here is a sequence of steps which tells you what to actually do in order to implement this function on top of the description which you will find within each lesson. That's where you put the, for example code to load range image, the code to compute the vertical field of view from a ladder calibration, and so on and so forth. I think that's all you need to know to go through the exercises one by one to make the visualizations, and I wish you all the best with using this code, and please don't forget to leave us comments, give us feedback in case something doesn't work as expected, or maybe you have a suggestion for certain improvements.

## Additional Content

## Exercise: Lidar Data in the Waymo Dataset

First, please have a look at the following screencast to familiarize yourself with the general structure of the code. Then, clone the [Github repository](https://github.com/udacity/nd013-c2-fusion-exercises) to your local computer, or use the classroom workspace further below, and solve a first small exercise.
### Starter Code Imports
### The Basic Loop
Note: The workspace below will also contain the Waymo dataset files needed for the exercise.
### Working with Each Exercise
#### Files to work in: 
- `basic_loop.py` 
- `lesson1-lidar-sensor/exercises/starter/l1_exercises.py`

Now that you are familiar with the starter code, please try to solve the following exercise: 
- In `basic_loop.py`, parameterize the code to load sequence 1 and start the loop with frame 1. 
- Pass the current frame to function `print_no_of_vehicles` in file `l1_exercises.py`. 
- Write code to find out how many objects of type "vehicle" have been provided as ground-truth labels for the LiDAR sensors in this frame and print the result.
