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

Our goal is to generate continuous trajectories, but how do you do that? Let's start with a native approach and then gets more realistic. Let's say, our car has been driving along the road at a constant speed for some time. The s versus time graph is just a straight line, since the velocity is constant, and the differences time graph is flat, since the car is just staying in the center of the lane. Also note that I've shifted my axis a bit so that the origin of the frame is our current positioning as TNT. This will end up being computer showing the efficient layer. Now let's say we're getting off this highway soon. So we want to change lane in order to end up there. After some delta-T which let's say it's 10 second. On the SNT-graph that goal would be here and here. The stop position and go position are fixed. They define what we call the boundary conditions of our trajectory at t equals zero, and t equals ten. If those were our only boundary conditions, then we might consider s and t-trajectory is looking like this. But it turns out that these aren't physically possible. This kink in the slope would translate in an instantaneous jumping speed which would require infinite acceleration. Now, if we were to send that to our motion control module, maybe they can track this trajectory, but probably not. And even if they tried to track it, it would result in a very strong acceleration of our car, which is both uncomfortable and dangerous. This is why we need both continuity and smoothness in our trajectories. But how much continuity and smoothness? We know we want continuity in position, since our car cannot teleport. And it would not make sense to compute a trajectory starting 10 metres ahead of us. And we also know that our car cannot instantaneously change speed, therefore the speed should also be continuous. Following this logic you could also say that the acceleration should be continuous and maybe the acceleration's derivity as well and so on. Position becomes velocity, velocity because acceleration, acceleration becomes jerk, and going even further you get snap, crackle, and pop. It turns out that one of these quantities is directly related to human perception of comfort. So let's think about it. In a vehicle, humans feel discomfort when which of these values is high? Velocity? No. When they cruise down the highway at high velocity, people usually don't find it less comfortable than when they drive at lower speed. And if you think about airplanes, they move very fast and they aren't really uncomfortable. Acceleration maybe? That's slightly more tricky. We are indeed sensitive to acceleration but mostly when it becomes very high. For example, we are all used to supporting acceleration up to one G which is the most you can usually sustain in a normal car. Therefore, we shouldn't reach acceleration levels that are high enough to become uncomfortable. Jerk, then? It turns out, this is the quantity that humans perceive as uncomfortable. We can tolerate high acceleration but we don't like it when our acceleration changes too quickly which is high jerk. So when we design trajectories for self-driving car, we would like it, if they were jerk minimizing.
