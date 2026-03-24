# Lesson Outline

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=qyH-1BMCiUY)

## Summary

**Behavior Planning Overview**
=====================================

This lesson introduces the concept of behavior planning in self-driving cars, specifically its role in providing guidance to the trajectory planner. Behavior planning is responsible for making decisions about maneuvers over a long time horizon (10 seconds or more) based on data from various modules.

**Key Concepts**
-----------------

* **Path Planning**: The overall process of determining a vehicle's path, which involves behavior planning, trajectory planning, localization, and sensor fusion.
* **Behavior Planning Module**: A module that makes decisions about maneuvers over a long time horizon (10 seconds or more) based on data from various modules.
* **Finite State Machines (FSMs)**: A technique for implementing a behavior plan by defining a set of states and transitions between them.
* **Cost Functions**: Mathematical functions used to make behavioral level decisions, such as determining the best course of action.

**Practical Notes**
-------------------

The lesson will cover practical steps in:

* Understanding the inputs and outputs of the behavior planner
* Implementing Finite State Machines for behavior planning
* Defining Cost Functions for making behavioral level decisions

Note: This summary focuses on the key concepts and practical notes, but does not include code or formulas as there are none mentioned in the provided transcript.

## Transcript

Hey, I'm Tobi. And I'm Ben. And we are software engineers at Mercedes-Benz, who work in the behavior planning team. The behavior planning team is responsible for providing guidance to the trajectory planner about what sorts of maneuvers they should plan trajectories for. If you think about the over all flow of data in a self-driving car operating on the fastest time scales you have control. And with a slightly lower frequency than that you have Sensor Fusion. Just lower than that you have localization and trajectory planning which you learn more about in a next lesson. Next is Prediction which you just learned about. And then at the top of this diagram is behavior planning with the lowest update rate. The inputs to behavior planning come from the prediction module and the localization module. Both of which get their inputs from the sensor fusion. And the output from the behavior module goes directly to the trajectory planner. Which also takes input from prediction and localization so that it can send trajectories to the motion controller. Everything inside of this box is the focus of this course and is commonly referred to as Path Planning. In this lesson, you will learn what exactly has to happen in this comparatively long time span. But intuitively this longtime span comes from the fact that the behavior plan has to incorporate a lot of data to make decisions about fairly long time horizons in the order of 10 seconds or even more. We will start by doing a brief introduction where you'll learn more about the details of the inputs and outputs to behavior planner and understand what problems a behavior planning module is expected to solve. Next, we will talk about Finite State Machines as one technique for implementing a behavior plan. Followed by a more in-depth look at the Cost Functions we will use to actually make behavioral level decisions. But first let's spend some time looking at the inputs we would be working with and the outputs we will be generating.