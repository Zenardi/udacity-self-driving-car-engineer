# Putting it All Together

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=UhrmXmnKhQE)

## Summary

**Summary**

This project involves developing an autonomous vehicle control system that can navigate through complex scenarios. The system uses a sampling-based approach to generate multiple possible trajectories for the vehicle to reach its desired position, while minimizing jerk (the rate of change of acceleration) and considering other factors such as distance to obstacles and center line.

**Key Concepts**

* **Sampling-based approach**: A method used to generate multiple possible trajectories for the vehicle to reach its desired position.
* **Jerk minimization**: The process of finding a trajectory that minimizes jerk, which is the rate of change of acceleration.
* **Cost functions**: Mathematical formulas used to evaluate the quality of each trajectory. Examples include:
	+ Jerk cost: penalizes high lateral jerk (side-to-side movement)
	+ Distance to obstacles cost: penalizes trajectories that are too close to other vehicles or pedestrians
	+ Distance to center line cost: penalizes trajectories that deviate from the center of the lane
	+ Time cost: penalizes trajectories that take longer to reach the destination
* **Weighted cost function**: A combination of multiple cost functions, where each cost is given a weight to determine its importance.

**Practical Notes**

The system generates multiple possible trajectories and evaluates their quality using the defined cost functions. The trajectory with the lowest combined cost is selected as the optimal path for the vehicle to follow. In practice, balancing the weights of different cost functions can be challenging, as they often conflict with each other (e.g., minimizing lateral jerk may not minimize distance to center line).

## Transcript

Now, in most cases, the behavior layer might not send an exact end configuration to reach but rather an approximate one like that. Therefore, we want to identify a varied goal state that leads our vehicle in the approximate end configuration that's being sent to us here in the other lane. Now, that's where our sampling based approach comes in handy. We don't know for sure what a good end state is. Even if we receive an exact S&amp;D co-ordinate from the behavior layer, we still have to find a good end velocity and acceleration for our car. Most times, S&amp;D aren't fixed either. Therefore, we want to sample a large number of end configurations are on the approximate desired position that we wish to drive our car to. And we generate the corresponding Jerk minimizing trajectories for each goal configuration. Then, we discard all non-derivable trajectories, all trajectories that collide with the road boundaries, or with other vehicles or pedestrians as predicted by the prediction layer. Now, we have a nice set of derivable trajectories which are all collision free and Jerk optimal in each dimension with respect to the start and goal configurations. We need to decide which one the car should follow. That means we need to rank them, which we are going to do by defining a cost function. What makes sense as a cost function? First, consider Jerk. For each pair of end configurations, a quintic polynomial is Jerk optimal. But given that all the trajectories obtained are different final configuration, maybe some are better than others. In addition to that, we want to consider longitudinal versus lateral Jerk. What is worse for comfort? Turns out that side to side Jerk is more uncomfortable. So we want to prioritize minimizing that over minimizing longitudinal Jerk. Next, consider distance to obstacles. Given these two configurations, we would prefer being further away from the other vehicle to a situation where we are right next to their rear bumper. Also, we want to consider distance to center line. We might prefer to be close to the center of the line. So, in choosing between these two scenarios, maybe we would prefer the one on the right. Finally, it is time to go. All else being equal given the final S, we would prefer to arrive at our destination earlier rather than later. So we might prefer this situation. And there are plenty of other cost functions one might think of. The tricky part is balancing all of these costs correctly. Often, our goals conflict. So the trajectory that minimizes lateral Jerk may not be the one that keeps us closest to the center line. In practice, most of the hard work is in the details of balancing these cost functions. Now that we have defined all these cost functions and combined them into one weighted cost function, we can look back at the scenario we just saw and use the supplied cost functions to calculate the cost for each trajectory. For example, this trajectory looks nice. However, its rather close to the boundary of the lane. And even more important, it is close to another moving vehicle. Remember that we have to consider the full car dimension when looking at distance to obstacles. And in this case, we would be dangerously close to another car. Therefore, we would associate a high cost with this trajectory. Similarly, we don't like these two trajectories too much because they make us drive on this side of the lane. And there is not really a reason for that in this scenario. So, they would be associated with a high cost as well. Regarding these two trajectories, they're okay but the lateral Jerk associated with them would be higher than for trajectories whose end configuration has a larger S value. Therefore, they would be associated with a medium cost. Now, consider the last trajectory. It's nice and smooth, it doesn't turn too fast, we end up moving further away along the road, none of our cost functions end up with a higher value. Therefore, when we combine them, this trajectory gets a low cost and ends up being selected.
