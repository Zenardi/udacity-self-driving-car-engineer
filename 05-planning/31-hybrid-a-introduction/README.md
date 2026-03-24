# Hybrid A* Introduction

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=NuurQejBk0o)

## Summary

**Hybrid A* Algorithm for Robot Path Planning**

This README file provides an overview of the Hybrid A* algorithm, a variant of the A* algorithm designed to handle continuous motion planning in robot path planning. The main topic is the key differences between discrete and continuous motion planning, and how Hybrid A* addresses these differences.

**Key Concepts**

* **Discrete vs. Continuous Motion Planning**: A* is a discrete algorithm that assumes the world can be divided into discrete cells, whereas real-world robotic motion involves continuous movements.
* **State Transition Function**: In Hybrid A*, the state transition function allows for continuous movement by memorizing exact X', Y', and θ' values associated with each grid cell.
* **Hybrid A* Algorithm**: This algorithm combines the benefits of A* (correctness) with the ability to handle continuous motion planning, providing smooth and curved paths.
* **Lack of Completeness**: Hybrid A* may not capture all possible solutions to the navigation problem due to its approximation nature.

**Practical Notes**

To implement Hybrid A*, you will need to:

* Define a state transition function that allows for continuous movement
* Memorize exact X', Y', and θ' values associated with each grid cell
* Use these memorized values to determine the next cell in the path

Note: The implementation of Hybrid A* requires careful consideration of motion equations and their correctness, as this affects the accuracy of the resulting paths.

## Transcript

The next algorithm I would like to show you is called Hybrid A*. To introduce you to Hybrid A*, I would like to share your video that Sebastian recorded for another class. Afterwards, I'm going to ask you the same question about Hybrid A* that you just answered about A*. So let's talk about robot path planning or robot motion planning. Where just a rich field in itself and I can't give you a complete survey of all the items involved. But one of the key differences to the planning as we talked about before is that now the word is continuous. So for example, we've read about A* in which we discretize the world. You might have a goal location, you might have obstacles and then A*, a valid action sequence might look like this. And even though this is a valid solution to the planning problem, a car can't really follow these discrete choices. There's a number of very sharp turns over here that are just irreconcilable with the motion of a car. So the fundamental problem here is A* is discrete whereas the robotic world is continuous. So the question arises, is there version of A* that can deal with the continuous nature and give us probably executable paths? This is a big big question in robot motion planning. And let me just discuss it for this one example and show you what we've done to solve this problem with a duff probing challenge. So the key to solving this with A* has to do with a state transition function. Suppose we are in a cell like this and you play a sequence of very small steps simulations using our continuous math from before, then a state over here might find itself right here in the corner of the next discrete state. Instead of assigning this just to the grid cell, an algorithm called Hybrid A* memorizes the exact X prime Y prime and theta prime and associate it with the grid cell over here the first time the grid cell is expanded. Then when expanding from the cell, it uses a specific starting point over here to figure out what the next cell might be. Now, it might happen that the same cell we used to get in A* maybe from over here going into a different continuous polymerization of X, Y and theta, but because in A* we tend to expand cells along the shortest path before we look the longer paths, we not just cut this off and never consider to stay over here again. Now, this leads to a lack of completeness which means there might be solutions to the navigation problem that this algorithm doesn't capture. But it does give us correctness. So as long as our motion equations are correct, the resulting paths can be executed. Now, here's a caveat. This is an approximation and it's only correct to the point that these motions equations are correct or not correct. But nevertheless, all paths that come out are nice, smooth, and curved paths. And every time we expand the grid cell, we memorize explicitly the continuous values of X prime, Y prime and theta with this grid cell.

## Additional Content

## Hybrid A\* Introduction

The video below is an old one from a different course but does a great job of explaining Hybrid A\*.
