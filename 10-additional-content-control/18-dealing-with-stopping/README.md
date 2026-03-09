# Dealing With Stopping

> Part of: **Model Predictive Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2gkRWj7KIMU)

## Summary

**Vehicle Trajectory Optimization**
=====================================

This summary covers key concepts for optimizing a vehicle's trajectory from point A to point B.

### Key Concepts

* **Reference Velocity**: A target velocity that the vehicle should maintain along its trajectory, used to penalize deviations.
	+ Example: Setting a reference velocity of 35 mph.
* **Cost Function**: A mathematical function that calculates the cost or penalty for not following the reference trajectory.
	+ Alternative approaches:
		- Cross-functional penalization
		- Measuring Euclidean distance between current position and destination
* **Optimization Techniques**: Methods to improve the vehicle's trajectory, such as using a set of reference velocities or measuring distances.

### Practical Notes

When implementing optimization techniques for vehicle trajectories, consider the following:

* Use a cost function that penalizes deviations from the reference velocity.
* Explore alternative approaches, such as cross-functional penalization or measuring Euclidean distance.
* Think creatively to develop new optimization techniques.

## Transcript

<v English>If the goal is to move the vehicle from A to B then</v> <v English>coming to a halt in the middle of the reference trajectory is a problem.</v> <v English>A simple solution is a set of reference velocity,</v> <v English>to cross-functional penalize the vehicle for not maintaining that reference velocity.</v> <v English>In this case imagine the reference velocity is 35 mph.</v> <v English>Another option is to measure the Euclidean distance between the current position of</v> <v English>the vehicle and the destination and then add that distance to the cost.</v> <v English>There may be other great alternatives though. Feel free to think of one.</v>
