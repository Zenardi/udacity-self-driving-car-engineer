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

Hi, I'm Emmanuel. And in this lesson, I'm going to teach you about continuous trajectory planning. And more specifically, how to generate draggable trajectories. Before we begin, let me give you a quick overview of the lesson. First, we will define what the motion planning problem is and discuss a few important concepts and priorities regarding motion planning algorithms. Then we'll do a quick review of A* to get you ready for the first new algorithm we will cover which is called Hybrid A*. As name suggests, Hybrid A* isn't purely discrete or continues. Next, we explore sampling based method called polynomial trajectory generation, which is really useful for highway driving. Before we dive into how to actually make the car drive, let's take a minute to formally define the motion planning problem.