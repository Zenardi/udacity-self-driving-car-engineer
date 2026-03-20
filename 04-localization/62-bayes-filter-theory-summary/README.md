# Bayes Filter Theory Summary

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lMyu2-PZGuk)

## Summary

**Bayes Localization Filter: A General Framework for Recursive State Estimation**

The Bayes localization filter, also known as the Bayes filter, is a fundamental concept in robotics and computer vision. It provides a general framework for recursive state estimation, which means that it uses previous states to estimate new states based on current observations and controls.

**Key Concepts:**

* **Recursive State Estimation**: The process of using previous states to estimate new states.
* **Bayes Filter**: A general framework for recursive state estimation.
* **Motion Model**: Describes the predictions step of the filter, which predicts the next state given the current state and control inputs.
* **Observation Model**: Describes the update step of the filter, which updates the state probabilities based on current observations.
* **Probabilistic Reasoning**: The use of probability theory to reason about uncertainty in state estimation.

**Practical Notes:**

* The Bayes localization filter is a general framework that can be used for various applications, including 1D localization and particle filters.
* Real-world applications include self-driving cars and robotics, where accurate state estimation is crucial for navigation and control.
* The C++ example code will be finalized in the next steps to demonstrate the implementation of the Bayes filter.

## Transcript

Since I went through a lot of math, I want to present the core achievements of the last steps. So let's sum it up. The Bayes localization filter, or Bayes filter, is a general framework for recursive state estimation. Recursive means that we use the previous state to estimate the new state by using only current observations and controls, and not the whole history of data. The motion model describes the predictions step of the filter. The observation model is the update step to estimate the new state probabilities. You already heard about this interaction between prediction and update step before. For example, when Andray talked about common filters in the fusion lesson. This means the current 1D localization, common filters, and also particle filters are realizations of the Bayes filter. Now you understand probabilistic reasoning, and recursive of state estimation. This is an amazing achievement, not only for localization, but also for the whole self-driving car nanodegree. Now that you know all the theory behind it, let's go back to the C++ example and finalize the localizer.


## Additional Content

![image](images/22-l-bayes-filter-theory-summary_00-00-22-29_still001.png)


The image above sums up the core achievements of this lesson.
- The Bayes Localization Filter Markov Localization is a general framework for recursive state estimation.
- That means this framework allows us to use the previous state (state at t-1) to estimate a new state (state at t) using only current observations and controls (observations and control at t), rather than the entire data history (data from 0:t).

![image](images/22-l-bayes-filter-theory-summary_00-00-52-03_still002.png)


- The motion model describes the prediction step of the filter while the observation model is the update step.
- The state estimation using the Bayes filter is dependent upon the interaction between prediction (motion model) and update (observation model steps) and all the localization methods discussed so far are realizations of the Bayes filter.
- In the next few sections we will learn how to estimate pseudo ranges, calculate the observation model probability, and complete the implementation of the observation model in C++.
