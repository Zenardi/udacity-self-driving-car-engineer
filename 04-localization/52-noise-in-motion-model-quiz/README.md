# Noise in Motion Model: Quiz

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=zRbT36RTlhs)

## Summary

**Bayesian Localization in 1D Space**
=====================================

This README file summarizes the key concepts and practical notes from a lesson on Bayesian localization in one-dimensional space.

### Key Concepts
* **Uniform Distribution**: The initial belief of the robot's location, representing maximum confusion or uncertainty.
* **Non-Uniform Distribution**: The updated belief after incorporating new information, such as proximity to a tree.
* **Motion Model**: The process of updating the belief based on the robot's movement, including noise levels (no noise, low noise, high noise).
* **Bayesian Localization**: A method for estimating the robot's location using probabilistic inference and Bayes' theorem.

### Practical Notes
The lesson demonstrates how to update the initial uniform distribution with new information about the robot's proximity to a tree. The instructor asks students to consider how the belief changes after moving 10 meters to the right under different noise conditions (no noise, low noise, high noise). This exercise illustrates the application of Bayesian localization in real-world scenarios.

Note: The lesson does not provide explicit code or formulas for implementing Bayesian localization. However, it lays the foundation for understanding the key concepts and principles involved in this technique.

## Transcript

Assume you have a 1D space between 0 and 30 meters. At the very beginning, the robot or the car has no clue where it is. So our initial belief would be the uniform distribution, which means maximum confusion. Now we assume the car knows it is parked closely to a tree. Then, the initial belief would look like this. And here's my question to you. How does that belief look like after we move 10 meters to the right with no noise, with low noise, and with high noise? And these are the four possible answers.
## Images

![quiz screenshot ](images/screen-shot-2017-04-07-at-12_08_14-pm.png)
*quiz screenshot *

## Additional Content

Here is a screenshot of the quiz for reference:
