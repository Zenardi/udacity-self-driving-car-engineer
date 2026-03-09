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

<v English>Hey, I'm Tobi.</v> <v English>And I'm Ben.</v> <v English>And we are software engineers at Mercedes-Benz,</v> <v English>who work in the behavior planning team.</v> <v English>The behavior planning team is responsible for providing guidance to</v> <v English>the trajectory planner about what sorts of maneuvers they should plan trajectories for.</v> <v English>If you think about the over all flow of data in</v> <v English>a self-driving car operating on the fastest time scales you have control.</v> <v English>And with a slightly lower frequency than that you have Sensor Fusion.</v> <v English>Just lower than that you have localization and</v> <v English>trajectory planning which you learn more about in a next lesson.</v> <v English>Next is Prediction which you just learned about.</v> <v English>And then at the top of this diagram is behavior planning with the lowest update rate.</v> <v English>The inputs to behavior planning come from</v> <v English>the prediction module and the localization module.</v> <v English>Both of which get their inputs from the sensor fusion.</v> <v English>And the output from the behavior module goes directly to the trajectory planner.</v> <v English>Which also takes input from prediction and</v> <v English>localization so that it can send trajectories to the motion controller.</v> <v English>Everything inside of this box is the focus of</v> <v English>this course and is commonly referred to as Path Planning.</v> <v English>In this lesson, you will learn what exactly has to</v> <v English>happen in this comparatively long time span.</v> <v English>But intuitively this longtime span comes from</v> <v English>the fact that the behavior plan has to incorporate a lot of</v> <v English>data to make decisions about</v> <v English>fairly long time horizons in the order of 10 seconds or even more.</v> <v English>We will start by doing a brief introduction where</v> <v English>you'll learn more about the details of the inputs and</v> <v English>outputs to behavior planner and understand</v> <v English>what problems a behavior planning module is expected to solve.</v> <v English>Next, we will talk about</v> <v English>Finite State Machines as one technique for implementing a behavior plan.</v> <v English>Followed by a more in-depth look at</v> <v English>the Cost Functions we will use to actually make behavioral level decisions.</v> <v English>But first let's spend some time looking at the inputs</v> <v English>we would be working with and the outputs we will be generating.</v>
