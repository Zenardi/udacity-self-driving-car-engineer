# Jerk Minimizing Trajectories

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=pomDFkzy2bk)

## Summary

**Jerk Minimizing Trajectory for 1D Motion**
=============================================

This project focuses on computing a jerk minimizing trajectory for one-dimensional motion. The goal is to find a function that minimizes the total square jerk accumulated over a given duration.

**Key Concepts**
---------------

* **Jerk**: A third derivative of position with respect to time.
* **Total Square Jerk**: An equation representing the total accumulated jerk over a duration, including both positive and negative jerk.
* **Minimum Jerk Trajectory**: A function that minimizes the total square jerk.
* **Fifth Order Polynomial**: Any minimum jerk trajectory can be represented as a fifth order polynomial with six coefficients (tunable parameters).
* **Boundary Conditions**: Initial position, velocity, acceleration, final position, velocity, and acceleration.

**Practical Notes**
------------------

To compute a jerk minimizing trajectory, you need to:

1. Specify the boundary conditions (initial position, velocity, acceleration, final position, velocity, and acceleration).
2. Use the fifth order polynomial representation of the minimum jerk trajectory.
3. Choose the six coefficients (tunable parameters) to define the shape of the trajectory.
4. Apply these coefficients to compute the position, velocity, and acceleration over time.

Note: The lesson provides an example of computing the coefficients for a simple case where a car moves from one point to another with zero initial and final lateral velocities and accelerations.

## Transcript

What is a jerk minimizing trajectory? An interesting and useful fact to us is that it is relatively easy to compute a jerk optimal trajectory in one dimension. In fact, consider a function s of t different from time zero to time tf. and recall that jerk is a third relative of position. So the total jerk accumulated over the duration of this trajectory is given by this equation. And here, we want to analyze both positive and negative jerk. Therefore, we're going to look at total square jerk. Our problem is then to find a function s of t that minimizes this integral. If we go through the math required to find the minimum, you'll find that all the time derivatives of s are further six and more have to be zero in order for S to be jerk minimal. Now, we can also use a helpful fact about functions, which is that any function can be written like this or more compactly like this. When you take this form of s and add in the information that we have about it's time derivative, you find this. All of the coefficient bigger than five or zero, which means that all minimum jerk trajectories can be represented as a fifth order polynomial like this. You can see this equation has six coefficients and six coefficients means six tuneable parameters that we can choose from in order to define the shape of a 1D trajectory. And in practice, we use them to specify the boundary conditions of our trajectory. The things we'd like to constrain are the initial position, velocity, and acceleration as well as the final position, velocity and acceleration. Now, this is just the 1D representing the longitude of displacement. But, the same for the lateral displacement applies. This gives us 12 variables to pick in order to fully define the motion of our vehicle in S&D over time. The initial state of our vehicle give us the longitudinal and lateral boundary conditions t equals zero, and we get to pick the end boundary condition. I'm going to show you plots of what lateral trajectories look like for a simple case, where a car moves from here to here and make the simplifying assumption that the initial and final lateral velocities and accelerations are zero. Which is reasonable for lane change. Then, all boundary conditions look like this. And the only nonzero quantity of this 1D problem is the final lateral displacement. Let's look at what some of these trajectories look like. Keep in mind, this is a one dimensional motion. The X axis here is time and the Y axis is lateral position of the vehicle as it makes its lane change. The F and T are the final lateral displacements and the duration of our trajectory. You can see at equal zero, the position is zero. The slope is zero so velocity is now and so is acceleration. Likewise, for the final position that equals 10. And this curves looks pretty smooth. But let's also look at velocity over time and acceleration over time. Although not all of these curves might be meaningful to you, let's think back about what just happened here. We've specified a position we wanted to reach and a time we wanted to reach it at in some equations and we end up with a nice looking trajectory. It's very nice indeed because a lot of drivers would not attain that level of comfort if we were to ask them to reproduce it. Now, let's see what happens if I try to reach the destinations more quickly by turning down T. Sure enough, we can still find the trajectory over time, but it's much more jerky. It is important to realize that although the trajectory that we generate using this method or jerk optimal for a given set of boundary conditions, they still depend heavily on these conditions. Therefore, it would be important in the future to wisely pick these end conditions. Now, I want to show you how I computed what the six coefficient had to be in order to satisfy these boundary conditions.
