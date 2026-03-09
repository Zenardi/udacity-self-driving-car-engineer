# Compiling the Lidar Simulator

> Part of: **[Optional] Intro to PCL**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=kj3PLhCVuPg)

## Summary

**Lidar Simulator Compilation Guide**
=====================================

This guide provides a step-by-step walkthrough of compiling the Lidar Simulator using CMake.

### Key Concepts

* **CMake**: A build system generator that creates instructions for building, testing, and packaging software.
* **CMakeLists.txt**: A configuration file that contains instructions for CMake to generate build files.
* **Build directory**: A new directory created to hold the compiled executable.
* **`cd` command**: Changes the current working directory in the terminal.
* **`mkdir` command**: Creates a new directory.
* **`cmake` command**: Generates build files based on the instructions in CMakeLists.txt.

### Practical Notes

To compile the Lidar Simulator, follow these steps:

1. Create a new directory called `Build` using the `mkdir` command: `MK directory Build`
2. Navigate into the `Build` directory and run `cmake ..` to generate build files.
3. Run `make` to create the executable.

Note: Make sure you are in the correct directory (e.g., `cd home/workspace/sensor_fusion`) before running these commands.

## Transcript

Let's go ahead now and see about compiling this Lidar Simulator. Back in my virtual workspace environment, I have something called the terminator, which is a terminal but it's called the terminator. We're going to go into home. We're going to check out workspace, and from here, we'll go into this sensor fusion, and I just clone this from the GitHub repository. Here, what you want to do is you want to make a new directory called Build, and so you do MK directory Build.

Then, I already did this actually, you can go into Build. Basically, we can see right here we have the CMakeList.text. So when I'm inside Build and I run c-make.., this.. is saying look in the directory just one level above, and that it'll see that CMakeLists.txt when I call that, it'll create all the instructions needed, so when I next to the final command build, it'll create this executable for me. So if I go ahead and do make, I build this target now and have this environment executable and that I will later be using.

So now you can go ahead and try this for yourself. From the classroom workspace environment, go into the desktop mode and then you can actually go into the terminator cd home workspace, and from that root directory, go ahead and run these commands and see if you can compile the environment.

## Additional Content

## Compiling the Lidar Simulator
### Compilation Instructions
- In the terminal workspace below, click on `Desktop` button on lower right. A new virtual Desktop will open up in a separate browser tab. 
- Click on `Terminator` to load up work space desktop terminal.
- From the terminal, go to the project root directory, `cd /home/workspace/SFND-Lidar-Obstacle-Detection`.
- Create a new directory from the project root named `build` with the following command: `mkdir build`.
- Then go into the build directory: `cd build`.
- Run cmake pointing to the `CMakeLists.txt` in the root: `cmake ..`.
If everything went well you should see something like
```bash
-- Configuring done
-- Generating done
-- Build files have been written to: /your directory/simple_highway/build
```
- If cmake was successful, then from inside build run make: `make`
- If make built target environment 100%, it will have generated an executable called `environment`. This build process is defined from the `CMakeLists.txt` file.

### Compilation Walkthrough
