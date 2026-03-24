# The Need for Time

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=4WsqXkB8zqQ)

## Summary

**README: Planning Trajectories in Dynamic Environments**

This project focuses on developing algorithms for planning trajectories in dynamic environments, such as highways with moving vehicles. The main topic of this project is to understand the importance of incorporating timing into motion planning and how it affects the complexity of the problem.

**Key Concepts**

* **Discrete Time Increments**: Breaking down time into discrete steps to plan vehicle movements.
* **Trajectory Planning**: Determining a sequence of configurations for a vehicle to follow over time.
* **Dynamic Environments**: Situations where the traversal space is constantly changing, such as highways with moving vehicles.
* **Three-Dimensional Problem**: Planning trajectories in dynamic environments requires considering time as well as spatial coordinates.

**Practical Notes**

* When planning trajectories, it's essential to consider not only the sequence of configurations but also when they should be executed.
* Using discrete time increments can help simplify the problem by breaking down complex motion into manageable steps.
* In dynamic environments, the traversal space is constantly changing, making it crucial to incorporate timing into motion planning.

Note: This README provides a summary of the main concepts and ideas presented in the Udacity lesson video. It's intended to serve as a starting point for further exploration and development of algorithms for planning trajectories in dynamic environments.

## Transcript

Now I'm going to emphasize why it is important to not just compute a sequence of configurations, but also to decide when we're going to be in each configuration. So let's say I told you that some car recently drove along this road following this trajectory. If I asked you to describe what the driver did, you might be tempted to say that they passed the slow moving vehicle or maybe, you think they swerved to avoid a pothole. Well, let me tell you what actually happened up here, we had a broken down vehicle stopped on the road, and down here we have a quickly moving vehicle that will travel the trajectory we just saw. Now, I'm going to track the location of this vehicle with little blue dots. Add one here for T equals zero. In the next time step, the vehicle has moved forward quite a bit and again and again, but this time not as much because it started to slow down and slowing down again. At this point, this vehicle would like to change lane in order to pass the stopped vehicle. However, at the same moment it senses a vehicle arriving behind it in the other lane at high speed. Therefore, it has to wait until this new car has passed it in order to change lane which only gives it the option to come to a full stop and wait. T=7, T=8 and T=9 when the red vehicle has passed it. The blue vehicle decide that it's safe to keep driving. It does this by turning left and accelerating. It continues with the lane change maneuver, until it gets into the left lane where it keeps accelerating and accelerating until it gets to highway speed. Once it has passed the stop vehicle, it gets back into the right lane and continues on its way. I told you this story using discrete time increments, but the vehicle was following a continuous path that looked something like this. If we remove the dots, we're left with the same path I asked you about in the beginning. The problem was not incorporating timing into our planning, is that you don't tell the full story. You describe the motion of your vehicle in the next few seconds, but you don't actually specify where the vehicle should be at a given time within this time frame. When we were solving static Mayes's problems this was fine but highways aren't Mayes's. There is traffic on highways which means that the traversal space is constantly changing over time. To avoid collision in dynamic environment, we need to think about time as well. And that means that driving in traffic is fundamentally a three dimensional problem. It is important to note that you have the same situation if you were using Cartesian coordinates. For any coordinates help us simplify the problem, but do not change the nature of the problem, which is planning a trajectory in dynamic environment.
