# s, d, and t

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=SD1iyzgFf8s)

## Summary

**README: Time-Aware Path Planning for Autonomous Vehicles**

This project introduces time-aware path planning for autonomous vehicles. The main topic is to understand how to plan a vehicle's motion in both space (s) and time (t), taking into account dynamic objects on the road.

### Key Concepts

* **Path planning**: generating a sequence of configurations for a vehicle to follow
* **Trajectory**: a function that associates a configuration with each point in time
* **Discretized grid**: representing the driving surface as a grid, where each cell represents a possible position and velocity
* **A\*** and Hybrid A\*: algorithms used for path planning, but not taking into account dynamic objects or time
* **Time-aware path planning**: planning a vehicle's motion in both space (s) and time (t)
* **Separating s and d dimensions**: reasoning about two separate pictures, one for space and one for time

### Practical Notes

To implement time-aware path planning, you will need to:

* Represent the driving surface as a discretized grid
* Use algorithms like A\* or Hybrid A\* to plan a vehicle's motion in space (s)
* Plan a vehicle's motion in time (t) by separating the s and d dimensions
* Visualize the trajectory of the vehicle over time using graphs

Note: This project builds upon previous work on path planning, and requires understanding of algorithms like A\* and Hybrid A\*. The goal is to generate a trajectory that takes into account dynamic objects on the road and plans the vehicle's motion in both space and time.

## Transcript

Up until now you learn about generating a sequence of configurations for vehicle using algorithms like A* and Hybrid A*. We refer to this as path planning. But what about time? In path planning, we imagine taking our driving surface and length some sort of discretized grid on top of it. Then, we make plans by specifying a start state and a goal state. And the trajectories we generate looks something like this for algorithms like A* or something like this for algorithms like Hybrid A*. These algorithms play an important role in autonomous driving. But the path they generate don't really take predictions into account. For example, let's project back to when the blue vehicle first wanted to change lane. Here we will include the time as a third dimension. One way to visualize it is to imagine looking at the road from some angle and time would be the dimension going up. And one way for a vehicle to move along the path that goes around the start vehicle, would be something like that. The fast moving vehicle we perceived behind us is predicted to move in on the lane at a fast speed which would look something like that. And that's how we know that we cannot change lane immediately. If we try to go before the vehicle that passed us, which is another red Polygram in the two dimension. We will collide with the vehicle. We have to wait for this vehicle to drive past us. Once the Red car has passed us, we can proceed with all ancient. Now as you can see, having a path is nice, but it is not sufficient to solve the planning problem when there are dynamic objects around us which in autonomous driving is all the time. Therefore, we have to plan not only a sequence of configuration, sd and fita but also have these configurations all set up in time. The trajectory is a function which for any time t associates a configuration of a vehicle. Now, we need a way to generate such a trajectory. And the way we're going to do this, is by separating the planning we do in the S dimension, from the planning we do in a d dimension. Instead of thinking about one picture in three dimension, we usually decide to reason about two pictures. Each of which is in two dimensions. I'm going to walk you through the same vehicle tracking exercise I did in the previous video, two more times. One for s and one for d. Let's start with s. At t=0. The vehicle is here at s=0. Then at t=1, it's here. And it keeps moving until it reaches the situation where it goes to a full stop. Note that we can see the vehicle has stopped by looking at this graph. Here we can see a flat slope and the flat slopes means no movement. This is something we couldn't see in that t over s graph that we used before to represent a path. Then the vehicle starts moving again until it reaches its final configuration at t=15. Now, let's do the same thing for d versus t. As we move along the road, d remains constant. Then the vehicle goes to a full stop and after the stop, start shifting left. And after it has passed the green vehicle, it goes back to its original lane. Finally, we can look at both trajectories simultaneously and the great thing is that we can finally visualize the whole motion of the car over time. It's not just a path now, it's a trajectory and we can fully describe what the vehicle did within these 15 seconds. Next, I'm going to ask you to think about some questions involving graphs like these.
