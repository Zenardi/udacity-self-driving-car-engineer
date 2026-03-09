# Track State

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=KlkXH2jrmfg)

## Summary

**Track State Management**
==========================

This lesson introduces the concept of defining a **track state** based on its score in object tracking systems. The track state is used to indicate the level of confidence or certainty that the tracked object actually exists.

### Key Concepts
* **Track Score**: A numerical value representing how well the tracked object matches the expected characteristics.
* **Track State**: A descriptive label indicating the level of confidence in the existence of the tracked object (e.g., initialized, tentative, confirmed).
* **Thresholds**: Specific score values used to determine when to transition between different track states.

### Practical Notes
To implement a track management module, you can use heuristics and experience values to define your own thresholds for transitioning between different track states. In the final project, you will have the opportunity to replace the given track management values with your own custom implementation.

Note: This lesson does not provide explicit code or formulas, but rather discusses the concept of track state management and its application in object tracking systems.

## Transcript

In addition to the track score, it might make sense to define a track state based on the score. For example, when the track is first initialized and the score is very low, we can define the track state as initialized. After our first threshold has been passed, the track state can be set to tentative. Finally, for example, at a score threshold of 0.8, we're quite certain that our track really exists and we can therefore set the track state to confirmed. Again, there's an infinite number of possibilities to define a track state.

A track management module often consists of many heuristics and experience values. In the final project, you can replace the given track management values and define your own. Let's see what happens.

## Additional Content

## Track State
Based on the track score, a track state can be defined, for example "initialized", "tentative" or "confirmed".
