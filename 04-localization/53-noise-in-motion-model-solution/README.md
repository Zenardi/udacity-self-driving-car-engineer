# Noise in Motion Model: Solution

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=zJ9NWz7IlOM)

## Summary

**Bayesian Filtering: Understanding the Impact of Noise on Belief Distributions**
====================================================================================

This summary provides an overview of key concepts related to Bayesian filtering and the effect of noise on belief distributions.

### Key Concepts
* **Noise**: The amount of uncertainty or randomness in a system, which can affect the accuracy of predictions.
* **Belief Distribution**: A mathematical representation of the probability distribution of a system's state, updated based on new observations and noise levels.
* **Low Noise**: When the system has minimal uncertainty, resulting in a concentrated belief distribution.
* **High Noise**: When the system has high uncertainty, resulting in a highly dispersed belief distribution.

### Practical Notes
When applying Bayesian filtering to real-world systems, it's essential to consider the impact of noise on the accuracy of predictions. With low noise levels, the belief distribution will be more precise and concentrated around the true state. Conversely, with high noise levels, the belief distribution will spread out and become less accurate.

Example code (not provided in this transcript) might involve implementing a Bayesian filter algorithm that updates the belief distribution based on new observations and noise levels. The goal is to develop a system that can adapt to changing noise conditions and provide accurate predictions accordingly.

## Transcript

If we move with no noise-- which means the transition model is certain-- then we would result in C. This means we just shift the initial belief 10 meters to the right. No noise does not mean we get a better precision. If we move with low noise, the belief is spread out-- so, answer B is correct. And if we move with high noise, the belief is very spread out and almost looks uniform-- so answer A is correct.