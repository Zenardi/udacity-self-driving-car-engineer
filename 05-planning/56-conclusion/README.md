# Conclusion

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=R56iixkZvEE)

## Summary

**Trajectory Generation in Self-Driving Cars**
=====================================================

This README file summarizes the key concepts and practical notes from a lesson on trajectory generation in self-driving cars.

### Key Concepts
* **Hybridized Trajectory Planning**: A method used for specific situations, such as parking lots.
* **Polynomial Trajectory Generation**: A technique suitable for low-traffic highways.
* **Multiple Trajectory Planners**: Self-driving cars often use multiple planners depending on the situation, including intersections and high traffic areas.

### Practical Notes
When implementing trajectory generation in a self-driving car project, consider using a combination of planners to adapt to different situations. Polynomial trajectory generation is a suitable choice for low-traffic highways. The final project will allow you to choose how to implement trajectory generation, so be prepared to experiment with different approaches.

## Transcript

In this lesson, you saw several approaches to the trajectory generation problem. None of them is the best for every situation that a self-driving car will encounter. In reality, most self-driving cars have several trajectory planners they can use depending on the situation. A car may use hybridized style in parking lots, polynomial trajectory generation on low traffic highways, and maybe several others for situations like intersections, high traffic, et cetera. In the final project, you'll get to choose how you implement trajectory generation. But I suspect you'll find that polynomial trajectory generation is well-suited for this problem. Good luck, and safe driving.
