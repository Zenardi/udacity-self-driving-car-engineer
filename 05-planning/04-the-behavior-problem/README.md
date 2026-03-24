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

Imagine you're driving in a city with your friend. You have a goal that you're trying to get to. You are sitting in the passenger seat and your friend is driving. You plug that goal into Google Maps and you get some route that will get you to your destination. The driver shouldn't be concerned about the details of what the route exactly is. Right, because the driver trusts that you acting, as the navigator, will tell them what maneuvers they need to make and it's understood that they are just responsible for executing them. In this situation, the responsibilities of the passenger are analogous to the responsibilities of a behavior planner in a self-driving car. So if you tell your friend to go left, they will do that. And when you tell the driver to pass a slow vehicle, the driver won't worry about whether they have enough time to do so because they will assume that you have thought about that and that you're confident that they can make it. But the navigator is not responsible for safety. If you tell the driver to get back to the left lane but there is a vehicle in the way, you will assume that they will wait to move left until there is enough room to do so safely. The navigator will also tell the driver when to keep their lane and when it is time to turn or change lanes or maybe adjust the speed. And finally, once you're arrived at your destination, you will tell the driver to stop. So, to summarize, the behavior planner is currently a black box which takes as input a map of the world, a route to the destinations, and predictions about what other static and dynamic obstacles are likely to do, and it produces as output a adjusted maneuver for the vehicle which the trajectory planner is responsible for reaching collision-free, smooth, and safe. The goal of this lesson is to open up this black box and learn how to implement a behavior planner. So the responsibilities of the behavior module are to suggest maneuvers which are feasible, as safe as possible, legal, and efficient. What the behavior planner is not responsible for are execution details and collision avoidance. The approach to behavior planning we are going to teach in this lesson is the same one used by most of the vehicles, including the winning one in the DARPA Urban Challenge. In fact, it's the approach to behavior planning that Mercedes used in their Bertha Benz Drive, which you can see is capable of handling complex traffic situations like navigating intersections and dense urban traffic. And while this approach is not necessarily the most common anymore, for reasons we will discuss later, it is widely known in the field and it does give a very high-level understanding of what is going on in a behavior planner.
