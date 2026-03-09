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

<v English>Up until now you learn about generating a sequence of configurations</v> <v English>for vehicle using algorithms like A* and Hybrid A*.</v> <v English>We refer to this as path planning. But what about time?</v> <v English>In path planning, we imagine taking</v> <v English>our driving surface and length some sort of discretized grid on top of it.</v> <v English>Then, we make plans by specifying a start state and a goal state.</v> <v English>And the trajectories we generate looks something like this for algorithms like A*</v> <v English>or something like this for algorithms like Hybrid A*.</v> <v English>These algorithms play an important role in autonomous driving.</v> <v English>But the path they generate don't really take predictions into account.</v> <v English>For example, let's project back to when the blue vehicle first wanted to change lane.</v> <v English>Here we will include the time as a third dimension.</v> <v English>One way to visualize it is to imagine looking at the road</v> <v English>from some angle and time would be the dimension going up.</v> <v English>And one way for a vehicle to move along the path that goes around the start vehicle,</v> <v English>would be something like that.</v> <v English>The fast moving vehicle we perceived behind us is predicted to</v> <v English>move in on the lane at a fast speed which would look something like that.</v> <v English>And that's how we know that we cannot change lane immediately.</v> <v English>If we try to go before the vehicle that passed us,</v> <v English>which is another red Polygram in the two dimension.</v> <v English>We will collide with the vehicle.</v> <v English>We have to wait for this vehicle to drive past us.</v> <v English>Once the Red car has passed us,</v> <v English>we can proceed with all ancient.</v> <v English>Now as you can see, having a path is nice,</v> <v English>but it is not sufficient to solve the planning problem when there are</v> <v English>dynamic objects around us which in autonomous driving is all the time.</v> <v English>Therefore, we have to plan not only a sequence of configuration,</v> <v English>sd and fita but also have these configurations all set up in time.</v> <v English>The trajectory is a function which for</v> <v English>any time t associates a configuration of a vehicle.</v> <v English>Now, we need a way to generate such a trajectory.</v> <v English>And the way we're going to do this,</v> <v English>is by separating the planning we do in the S dimension,</v> <v English>from the planning we do in a d dimension.</v> <v English>Instead of thinking about one picture in three dimension,</v> <v English>we usually decide to reason about two pictures.</v> <v English>Each of which is in two dimensions.</v> <v English>I'm going to walk you through</v> <v English>the same vehicle tracking exercise I did in the previous video, two more times.</v> <v English>One for s and one for d. Let's start with s. At t=0.</v> <v English>The vehicle is here at s=0.</v> <v English>Then at t=1, it's here.</v> <v English>And it keeps moving until it reaches the situation where it goes to a full stop.</v> <v English>Note that we can see the vehicle has stopped by looking at this graph.</v> <v English>Here we can see a flat slope and the flat slopes means no movement.</v> <v English>This is something we couldn't see in that t</v> <v English>over s graph that we used before to represent a path.</v> <v English>Then the vehicle starts moving again until it reaches its final configuration at t=15.</v> <v English>Now, let's do the same thing for d versus</v> <v English>t. As we move along the road, d remains constant.</v> <v English>Then the vehicle goes to a full stop and after the stop, start shifting left.</v> <v English>And after it has passed the green vehicle,</v> <v English>it goes back to its original lane.</v> <v English>Finally, we can look at both trajectories</v> <v English>simultaneously and the great thing is that we can</v> <v English>finally visualize the whole motion of the car over time.</v> <v English>It's not just a path now,</v> <v English>it's a trajectory and we can fully describe what the vehicle did within these 15 seconds.</v> <v English>Next, I'm going to ask you to think about some questions involving graphs like these.</v>
