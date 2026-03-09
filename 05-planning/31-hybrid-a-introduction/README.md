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

<v English>The next algorithm I would like to show you is called Hybrid A*.</v> <v English>To introduce you to Hybrid A*,</v> <v English>I would like to share your video that Sebastian recorded for another class.</v> <v English>Afterwards, I&#39;m going to ask you the same question</v> <v English>about Hybrid A* that you just answered about A*.</v> <v English>So let&#39;s talk about robot path planning or robot motion planning.</v> <v English>Where just a rich field in itself and I</v> <v English>can&#39;t give you a complete survey of all the items involved.</v> <v English>But one of the key differences to the planning as</v> <v English>we talked about before is that now the word is continuous.</v> <v English>So for example, we&#39;ve read about A* in which we discretize the world.</v> <v English>You might have a goal location,</v> <v English>you might have obstacles and then A*,</v> <v English>a valid action sequence might look like this.</v> <v English>And even though this is a valid solution to the planning problem,</v> <v English>a car can&#39;t really follow these discrete choices.</v> <v English>There&#39;s a number of very sharp turns over here</v> <v English>that are just irreconcilable with the motion of a car.</v> <v English>So the fundamental problem here is A* is</v> <v English>discrete whereas the robotic world is continuous.</v> <v English>So the question arises,</v> <v English>is there version of A* that can deal with the continuous nature</v> <v English>and give us probably executable paths?</v> <v English>This is a big big question in robot motion planning.</v> <v English>And let me just discuss it for this one example and show you</v> <v English>what we&#39;ve done to solve this problem with a duff probing challenge.</v> <v English>So the key to solving this with A* has to do with a state transition function.</v> <v English>Suppose we are in a cell like this and you play a sequence</v> <v English>of very small steps simulations using our continuous math from before,</v> <v English>then a state over here might find</v> <v English>itself right here in the corner of the next discrete state.</v> <v English>Instead of assigning this just to the grid cell,</v> <v English>an algorithm called Hybrid A* memorizes the exact X prime Y prime and theta</v> <v English>prime and associate it with</v> <v English>the grid cell over here the first time the grid cell is expanded.</v> <v English>Then when expanding from the cell,</v> <v English>it uses a specific starting point over here to figure out what the next cell might be.</v> <v English>Now, it might happen that the same cell we used to get in A* maybe from over</v> <v English>here going into a different continuous polymerization of X, Y and theta,</v> <v English>but because in A* we tend to expand</v> <v English>cells along the shortest path before we look the longer paths,</v> <v English>we not just cut this off and never consider to stay over here again.</v> <v English>Now, this leads to a lack of completeness which</v> <v English>means there might be solutions to</v> <v English>the navigation problem that this algorithm doesn&#39;t capture.</v> <v English>But it does give us correctness.</v> <v English>So as long as our motion equations are correct,</v> <v English>the resulting paths can be executed.</v> <v English>Now, here&#39;s a caveat.</v> <v English>This is an approximation and it&#39;s only correct</v> <v English>to the point that these motions equations are correct or not correct.</v> <v English>But nevertheless, all paths that come out are nice,</v> <v English>smooth, and curved paths.</v> <v English>And every time we expand the grid cell,</v> <v English>we memorize explicitly the continuous values of X prime,</v> <v English>Y prime and theta with this grid cell.</v>

## Additional Content

## Hybrid A\* Introduction

The video below is an old one from a different course but does a great job of explaining Hybrid A\*.
