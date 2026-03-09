# The Behavior Problem

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=5t-oVAZagT8)

## Summary

**Behavior Planner: A Key Component in Self-Driving Cars**

A behavior planner is a critical module in self-driving cars that determines the best course of action for the vehicle to reach its destination safely and efficiently. In this lesson, we will explore the responsibilities of a behavior planner and learn how to implement one.

**Key Concepts**

* **Behavior Planner**: A black box that takes input from a map of the world, route to destinations, and predictions about obstacles, and produces output in the form of adjusted maneuvers for the vehicle.
* **Responsibilities of Behavior Planner**: Suggest feasible, safe, legal, and efficient maneuvers. Do not handle execution details or collision avoidance.
* **Approach to Behavior Planning**: The approach used by most vehicles, including those that have won competitions like the DARPA Urban Challenge.
* **Behavior Planning Process**: Takes into account static and dynamic obstacles, traffic rules, and vehicle capabilities to determine the best course of action.

**Practical Notes**

The behavior planner is responsible for determining the maneuvers required to reach a destination safely and efficiently. It takes input from various sources, including maps, routes, and predictions about obstacles. The output of the behavior planner is then used by the trajectory planner to ensure that the vehicle reaches its destination collision-free, smoothly, and safely.

In this lesson, we will learn how to implement a behavior planner using a widely known approach in the field. This approach has been used successfully in various self-driving car applications, including navigating complex traffic situations like intersections and dense urban traffic.

## Transcript

<v English>Imagine you're driving in a city with your friend.</v> <v English>You have a goal that you're trying to get to.</v> <v English>You are sitting in the passenger seat and your friend is driving.</v> <v English>You plug that goal into Google Maps and you</v> <v English>get some route that will get you to your destination.</v> <v English>The driver shouldn't be concerned about the details of what the route exactly is.</v> <v English>Right, because the driver trusts that you acting, as the navigator,</v> <v English>will tell them what maneuvers they need to make and it's</v> <v English>understood that they are just responsible for executing them.</v> <v English>In this situation, the responsibilities of the passenger are</v> <v English>analogous to the responsibilities of a behavior planner in a self-driving car.</v> <v English>So if you tell your friend to go left, they will do that.</v> <v English>And when you tell the driver to pass a slow vehicle,</v> <v English>the driver won't worry about whether they have enough time to do so because they</v> <v English>will assume that you have thought about that</v> <v English>and that you're confident that they can make it.</v> <v English>But the navigator is not responsible for safety.</v> <v English>If you tell the driver to get back to the left lane but there is a vehicle in the way,</v> <v English>you will assume that they will wait to move</v> <v English>left until there is enough room to do so safely.</v> <v English>The navigator will also tell the driver when to keep their lane and when it is</v> <v English>time to turn or change lanes or maybe adjust the speed.</v> <v English>And finally, once you're arrived at your destination,</v> <v English>you will tell the driver to stop.</v> <v English>So, to summarize, the behavior planner is</v> <v English>currently a black box which takes as input a map of the world,</v> <v English>a route to the destinations,</v> <v English>and predictions about what other static and dynamic obstacles are likely to do,</v> <v English>and it produces as output a adjusted maneuver for the vehicle which</v> <v English>the trajectory planner is responsible for reaching collision-free, smooth, and safe.</v> <v English>The goal of this lesson is to open up</v> <v English>this black box and learn how to implement a behavior planner.</v> <v English>So the responsibilities of</v> <v English>the behavior module are to suggest maneuvers which are feasible,</v> <v English>as safe as possible, legal, and efficient.</v> <v English>What the behavior planner is not responsible</v> <v English>for are execution details and collision avoidance.</v> <v English>The approach to behavior planning we are going to teach in</v> <v English>this lesson is the same one used by most of the vehicles,</v> <v English>including the winning one in the DARPA Urban Challenge.</v> <v English>In fact, it's the approach to</v> <v English>behavior planning that Mercedes used in their Bertha Benz Drive,</v> <v English>which you can see is capable of handling</v> <v English>complex traffic situations like navigating intersections and dense urban traffic.</v> <v English>And while this approach is not necessarily the most common anymore,</v> <v English>for reasons we will discuss later,</v> <v English>it is widely known in the field and it does give</v> <v English>a very high-level understanding of what is going on in a behavior planner.</v>
