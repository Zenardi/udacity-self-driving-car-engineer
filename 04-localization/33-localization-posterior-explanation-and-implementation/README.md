# Localization Posterior Explanation and Implementation

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lGpIgbA5ZdA)

## Summary

**Localization: Estimating Probability Distribution of State**

This README file summarizes the key concepts and practical notes from a Udacity lesson on localization, specifically focusing on estimating the probability distribution of the state `xt`, which represents the pose of a car.

### Key Concepts

* **State xt**: The pose of the car, which is the position where the car is located.
* **Observations**: The car measures the distances to nearby landmarks (street lamps and trees) in its driving direction. These observations are represented as vectors `zt` containing the distances from 1 to `k`.
* **Control vector**: The control input is defined by the distance the car traveled between consecutive time stamps, which is a direct move of the car.
* **Map**: A landmark-based map that includes the positions of street lamps and trees in 1D. In this case, the map is a vector of six landmarks with values 9, 15, 25, 31, 59, and 77.
* **Belief of xt**: The probability distribution of the state `xt`, represented as a vector of 100 elements, where each element represents the probability that the car is located at the corresponding position.

### Practical Notes

To estimate the probability distribution of the state `xt`, you need to understand how the car senses and moves in a specific scenario. This involves defining the input data for a 1D localization problem, including:

* The map: A vector of landmark positions (e.g., street lamps and trees)
* Observations: Vectors `zt` containing distances from 1 to `k`
* Control vector: Distance traveled by the car between consecutive time stamps

The goal is to estimate the probability distribution of the state `xt`, which can be represented as a vector of probabilities for each possible position.

## Transcript

<v English>Localization is all about estimating the probability distribution of the state xt,</v> <v English>which is the pose of the car,</v> <v English>another condition that all previous observations that,</v> <v English>from time 1 to t,</v> <v English>and all previous controls u,</v> <v English>from time 1 to t, are given.</v> <v English>To solve the pure localization problem,</v> <v English>we assume the map is correct and does not change.</v> <v English>Therefore, the map is also given.</v> <v English>If we would like to estimate also the map,</v> <v English>then we would solve the simultaneous localization and mapping problem,</v> <v English>or called SLAM problem,</v> <v English>which is much more complex.</v> <v English>But today I don't talk about this.</v> <v English>Today, I will talk about the posterior distribution right here.</v> <v English>Before we go deeper into math,</v> <v English>I want to show you how we define</v> <v English>the different input data for a specific 1D localization scenario.</v> <v English>This means I will explain how the car is sensing and moving.</v> <v English>I will also show you how the map looks.</v> <v English>This example is very similar to what you already learned with Sebastian.</v> <v English>So, let's talk about the map first.</v> <v English>The map includes the position of street lamps and trees in 1D.</v> <v English>This means we are working with landmark-based maps which are,</v> <v English>in general, more sparse than grid-based maps.</v> <v English>In the 1D case,</v> <v English>the map is a vector of the position where these objects are.</v> <v English>Here, the map includes six landmarks with the values 9, 15, 25, 31, 59, and 77.</v> <v English>For the observation we</v> <v English>state that the car measures the nearest k,</v> <v English>seen static objects, in driving direction.</v> <v English>So we assume that the car can detect the distances to street lamps and trees.</v> <v English>This results in an observation list which includes,</v> <v English>for each time stamp t,</v> <v English>a vector of distances zt,</v> <v English>from 1 to zt to</v> <v English>k. It is possible that we detect multiple trees or street lamps at a time stamp t,</v> <v English>or detect nothing at all.</v> <v English>The control vector includes a direct move of the car between consecutive time stamps.</v> <v English>This means the control is defined by</v> <v English>the distance the car traveled between t and t minus 1.</v> <v English>In this case, the car moves 2 meters to the right.</v> <v English>The true pose of the car is somewhere on the mapped area.</v> <v English>Since the map is discrete,</v> <v English>the pose of the car could be any integer between 0 and 99 meters.</v> <v English>This means the belief of xt is defined as a vector of hundred elements,</v> <v English>and each element represents</v> <v English>a probability that the car is located at the corresponding position.</v> <v English>The goal is now to estimate these values.</v>
