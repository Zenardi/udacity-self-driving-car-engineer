# From Behavior to Trajectory

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=7yo_HJ1_J9Q)

## Summary

**Trajectory Planning for Autonomous Vehicles**
=====================================================

This lesson focuses on the concept of **trajectory planning**, a critical component in autonomous vehicle development. Trajectory planning involves determining not only the path that a vehicle should take, but also the speed at which it should travel over time.

**Key Concepts**
---------------

*   **Trajectory**: A trajectory is a combination of a curve (path) and a time sequence (speed profile) that defines how a vehicle moves through space.
*   **Time Sequence**: The time sequence in a trajectory determines when and how fast the vehicle should move along its path.
*   **Collision Avoidance**: One of the primary concerns in trajectory planning is ensuring that the vehicle does not collide with obstacles or other objects in its environment.
*   **Passenger Comfort**: Trajectory planning also considers factors like passenger comfort, aiming to create smooth and elegant paths that minimize unnecessary acceleration or deceleration.

**Practical Notes**
-------------------

While this lesson focuses on the theoretical aspects of trajectory planning, it's essential to note that practical implementation would involve integrating these concepts with other components of autonomous vehicle development, such as sensor data processing, control systems, and safety protocols.

## Transcript

<v English>I'm proud of your work on behavior selection,</v> <v English>but now we're going to go a level lower,</v> <v English>where we actually want to find a specific trajectory that the car can take.</v> <v English>A trajectory is not just a curve that the car can follow</v> <v English>but also a time sequence in which we say how fast the car should go.</v> <v English>In finding trajectory, there are many many important things to watch out for.</v> <v English>The most important one is don't crash,</v> <v English>don't collide with something else.</v> <v English>But also important is things like passenger comfort, right?</v> <v English>So you don't want to do crazy joke,</v> <v English>a trajectory that passes both back and forth.</v> <v English>You want to make this smooth and elegant as possible.</v>
