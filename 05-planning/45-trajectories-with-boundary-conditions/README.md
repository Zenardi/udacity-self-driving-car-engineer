# Trajectories with Boundary Conditions

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=p73Jma9nW-Q)

## Summary

**Generating Continuous Trajectories for Self-Driving Cars**

This project aims to generate smooth and continuous trajectories for self-driving cars. The goal is to create a motion plan that can be followed by the car without sudden changes in speed or direction.

### Key Concepts

* **Trajectory**: A path that describes the position of an object over time.
* **Boundary conditions**: Constraints on the trajectory at specific points in time, such as initial and final positions.
* **Continuity**: The property of a function being smooth and continuous, without sudden changes or discontinuities.
* **Smoothness**: The rate of change of a function, with a focus on minimizing jerk (the derivative of acceleration).
* **Jerk**: A measure of the rate of change of acceleration, which is perceived as uncomfortable by humans.

### Practical Notes

To generate smooth and continuous trajectories for self-driving cars:

1. Define the boundary conditions of the trajectory at specific points in time.
2. Ensure continuity in position and velocity to prevent sudden changes or teleportation.
3. Minimize jerk (the derivative of acceleration) to create a comfortable driving experience.
4. Use algorithms that can track and follow smooth trajectories, such as motion control modules.

Example code for generating continuous trajectories may involve using numerical methods, such as:

```python
import numpy as np

def generate_trajectory(t):
    # Define boundary conditions
    s0 = 0  # initial position
    v0 = 10  # initial velocity
    sf = 100  # final position
    vf = 20  # final velocity
    
    # Generate smooth trajectory using a polynomial function
    t_poly = np.poly1d([1, -2, 1])  # polynomial coefficients for s(t)
    v_poly = np.polyder(t_poly)  # derivative of polynomial for v(t)
    
    # Evaluate trajectory at specific points in time
    s = t_poly(t)
    v = v_poly(t)
    
    return s, v
```

Note that this is a simplified example and actual implementation may involve more complex algorithms and considerations.

## Transcript

<v English>Our goal is to generate continuous trajectories,</v> <v English>but how do you do that?</v> <v English>Let's start with a native approach and then gets more realistic.</v> <v English>Let's say, our car has been driving along the road at a constant speed for some time.</v> <v English>The s versus time graph is just a straight line,</v> <v English>since the velocity is constant,</v> <v English>and the differences time graph is flat,</v> <v English>since the car is just staying in the center of the lane.</v> <v English>Also note that I've shifted my axis a bit so that</v> <v English>the origin of the frame is our current positioning as TNT.</v> <v English>This will end up being computer showing the efficient layer.</v> <v English>Now let's say we're getting off this highway soon.</v> <v English>So we want to change lane in order to end up there.</v> <v English>After some delta-T which let's say it's 10 second.</v> <v English>On the SNT-graph that goal would be here and here.</v> <v English>The stop position and go position are fixed.</v> <v English>They define what we call the boundary conditions of our trajectory at t equals zero,</v> <v English>and t equals ten.</v> <v English>If those were our only boundary conditions,</v> <v English>then we might consider s and t-trajectory is looking like this.</v> <v English>But it turns out that these aren't physically possible.</v> <v English>This kink in the slope would translate in</v> <v English>an instantaneous jumping speed which would require infinite acceleration.</v> <v English>Now, if we were to send that to our motion control module,</v> <v English>maybe they can track this trajectory, but probably not.</v> <v English>And even if they tried to track it,</v> <v English>it would result in a very strong acceleration of our car,</v> <v English>which is both uncomfortable and dangerous.</v> <v English>This is why we need both continuity and smoothness in our trajectories.</v> <v English>But how much continuity and smoothness?</v> <v English>We know we want continuity in position,</v> <v English>since our car cannot teleport.</v> <v English>And it would not make sense to compute a trajectory starting 10 metres ahead of us.</v> <v English>And we also know that our car cannot instantaneously change speed,</v> <v English>therefore the speed should also be continuous.</v> <v English>Following this logic you could also say that the acceleration should be</v> <v English>continuous and maybe the acceleration's derivity as well and so on.</v> <v English>Position becomes velocity, velocity because acceleration,</v> <v English>acceleration becomes jerk, and going even further you get snap, crackle, and pop.</v> <v English>It turns out that one of these quantities</v> <v English>is directly related to human perception of comfort.</v> <v English>So let's think about it.</v> <v English>In a vehicle, humans feel discomfort when which of these values is high?</v> <v English>Velocity? No. When they cruise down the highway at high velocity,</v> <v English>people usually don't find it less comfortable than when they drive at lower speed.</v> <v English>And if you think about airplanes,</v> <v English>they move very fast and they aren't really uncomfortable.</v> <v English>Acceleration maybe?</v> <v English>That's slightly more tricky.</v> <v English>We are indeed sensitive to acceleration but mostly when it becomes very high.</v> <v English>For example, we are all used to supporting acceleration up to</v> <v English>one G which is the most you can usually sustain in a normal car.</v> <v English>Therefore, we shouldn't reach</v> <v English>acceleration levels that are high enough to become uncomfortable.</v> <v English>Jerk, then? It turns out,</v> <v English>this is the quantity that humans perceive as uncomfortable.</v> <v English>We can tolerate high acceleration but we don't like it</v> <v English>when our acceleration changes too quickly which is high jerk.</v> <v English>So when we design trajectories for self-driving car,</v> <v English>we would like it, if they were jerk minimizing.</v>
