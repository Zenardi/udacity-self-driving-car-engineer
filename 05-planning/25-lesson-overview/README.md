# Lesson Overview

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=BU4oChjLv7A)

## Summary

**Continuous Trajectory Planning**
=====================================

This project focuses on continuous trajectory planning, specifically generating draggable trajectories. We'll cover key concepts and algorithms used in motion planning.

### Key Concepts

* **Motion Planning Problem**: The process of finding a valid path for an object to move from its current position to a desired goal position while avoiding obstacles.
* **Priorities in Motion Planning**:
	+ Efficiency: Finding the shortest or fastest path
	+ Safety: Avoiding collisions with obstacles
	+ Smoothness: Minimizing jerky movements
* **A\***: A popular motion planning algorithm that uses a graph-based approach to find the shortest path between two points.
* **Hybrid A\***: An extension of A\* that combines discrete and continuous planning methods.
* **Polynomial Trajectory Generation**: A sampling-based method for generating smooth trajectories, particularly useful for highway driving.

### Practical Notes

This project involves implementing algorithms for motion planning, including Hybrid A* and polynomial trajectory generation. These techniques can be applied to various real-world applications, such as autonomous vehicles or robotics.

## Transcript

<v English>Hi, I'm Emmanuel. And in this lesson,</v> <v English>I'm going to teach you about continuous trajectory planning.</v> <v English>And more specifically, how to generate draggable trajectories.</v> <v English>Before we begin, let me give you a quick overview of the lesson.</v> <v English>First, we will define what the motion planning problem is</v> <v English>and discuss a few important concepts and priorities regarding motion planning algorithms.</v> <v English>Then we'll do a quick review of A*</v> <v English>to get you ready for the first new algorithm we will cover which is called Hybrid A*.</v> <v English>As name suggests, Hybrid A* isn't purely discrete or continues.</v> <v English>Next, we explore sampling based method called polynomial trajectory generation,</v> <v English>which is really useful for highway driving.</v> <v English>Before we dive into how to actually make the car drive,</v> <v English>let's take a minute to formally define the motion planning problem.</v>
