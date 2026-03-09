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

<v English>Now I'm going to emphasize why it is</v> <v English>important to not just compute a sequence of configurations,</v> <v English>but also to decide when we're going to be in each configuration.</v> <v English>So let's say I told you that some car recently</v> <v English>drove along this road following this trajectory.</v> <v English>If I asked you to describe what the driver did,</v> <v English>you might be tempted to say that they passed the slow moving vehicle or maybe,</v> <v English>you think they swerved to avoid a pothole.</v> <v English>Well, let me tell you what actually happened up here,</v> <v English>we had a broken down vehicle stopped on the road,</v> <v English>and down here we have</v> <v English>a quickly moving vehicle that will travel the trajectory we just saw.</v> <v English>Now, I'm going to track the location of this vehicle with little blue dots.</v> <v English>Add one here for T equals zero.</v> <v English>In the next time step,</v> <v English>the vehicle has moved forward quite a bit and again and again,</v> <v English>but this time not as much because it started to slow down and slowing down again.</v> <v English>At this point, this vehicle would</v> <v English>like to change lane in order to pass the stopped vehicle.</v> <v English>However, at the same moment it senses a vehicle</v> <v English>arriving behind it in the other lane at high speed.</v> <v English>Therefore, it has to wait until this new car has passed it in order to change</v> <v English>lane which only gives it the option to come to a full stop and wait.</v> <v English>T=7, T=8 and T=9 when the red vehicle has passed it.</v> <v English>The blue vehicle decide that it's safe to keep driving.</v> <v English>It does this by turning left and accelerating.</v> <v English>It continues with the lane change maneuver,</v> <v English>until it gets into the left lane where it keeps</v> <v English>accelerating and accelerating until it gets to highway speed.</v> <v English>Once it has passed the stop vehicle,</v> <v English>it gets back into the right lane and continues on its way.</v> <v English>I told you this story using discrete time increments,</v> <v English>but the vehicle was following a continuous path that looked something like this.</v> <v English>If we remove the dots,</v> <v English>we're left with the same path I asked you about in the beginning.</v> <v English>The problem was not incorporating timing into our planning,</v> <v English>is that you don't tell the full story.</v> <v English>You describe the motion of your vehicle in the next few seconds,</v> <v English>but you don't actually specify where</v> <v English>the vehicle should be at a given time within this time frame.</v> <v English>When we were solving static Mayes's problems this was fine but highways aren't Mayes's.</v> <v English>There is traffic on highways which means that</v> <v English>the traversal space is constantly changing over time.</v> <v English>To avoid collision in dynamic environment,</v> <v English>we need to think about time as well.</v> <v English>And that means that driving in traffic is fundamentally a three dimensional problem.</v> <v English>It is important to note that you have</v> <v English>the same situation if you were using Cartesian coordinates.</v> <v English>For any coordinates help us simplify the problem,</v> <v English>but do not change the nature of the problem,</v> <v English>which is planning a trajectory in dynamic environment.</v>
