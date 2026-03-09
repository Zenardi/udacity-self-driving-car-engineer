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

<v English>What is a jerk minimizing trajectory?</v> <v English>An interesting and useful fact to us is that it is</v> <v English>relatively easy to compute a jerk optimal trajectory in one dimension.</v> <v English>In fact, consider a function s of t different from time zero to time tf.</v> <v English>and recall that jerk is a third relative of position.</v> <v English>So the total jerk accumulated over</v> <v English>the duration of this trajectory is given by this equation.</v> <v English>And here, we want to analyze both positive and negative jerk.</v> <v English>Therefore, we're going to look at total square jerk.</v> <v English>Our problem is then to find a function s of t that minimizes this integral.</v> <v English>If we go through the math required to find the minimum,</v> <v English>you'll find that all the time derivatives of s are further</v> <v English>six and more have to be zero in order for S to be jerk minimal.</v> <v English>Now, we can also use a helpful fact about functions,</v> <v English>which is that any function can be written like this or more compactly like this.</v> <v English>When you take this form of s and add in</v> <v English>the information that we have about it's time derivative, you find this.</v> <v English>All of the coefficient bigger than five or zero,</v> <v English>which means that all minimum jerk trajectories</v> <v English>can be represented as a fifth order polynomial like this.</v> <v English>You can see this equation has six coefficients and six coefficients means</v> <v English>six tuneable parameters that we can choose</v> <v English>from in order to define the shape of a 1D trajectory.</v> <v English>And in practice, we use them to specify the boundary conditions of our trajectory.</v> <v English>The things we'd like to constrain are the initial position, velocity,</v> <v English>and acceleration as well as the final position, velocity and acceleration.</v> <v English>Now, this is just the 1D representing the longitude of displacement.</v> <v English>But, the same for the lateral displacement applies.</v> <v English>This gives us 12 variables to pick in order to fully</v> <v English>define the motion of our vehicle in S&amp;D over time.</v> <v English>The initial state of our vehicle give us</v> <v English>the longitudinal and lateral boundary conditions t equals zero,</v> <v English>and we get to pick the end boundary condition.</v> <v English>I'm going to show you plots of what lateral trajectories look like for a simple case,</v> <v English>where a car moves from here to here and make</v> <v English>the simplifying assumption that</v> <v English>the initial and final lateral velocities and accelerations are zero.</v> <v English>Which is reasonable for lane change.</v> <v English>Then, all boundary conditions look like this.</v> <v English>And the only nonzero quantity of this 1D problem is the final lateral displacement.</v> <v English>Let's look at what some of these trajectories look like.</v> <v English>Keep in mind, this is a one dimensional motion.</v> <v English>The X axis here is time and</v> <v English>the Y axis is lateral position of the vehicle as it makes its lane change.</v> <v English>The F and T are the final lateral displacements and the duration of our trajectory.</v> <v English>You can see at equal zero,</v> <v English>the position is zero.</v> <v English>The slope is zero so velocity is now and so is acceleration.</v> <v English>Likewise, for the final position that equals 10.</v> <v English>And this curves looks pretty smooth.</v> <v English>But let's also look at velocity over time and acceleration over time.</v> <v English>Although not all of these curves might be meaningful to you,</v> <v English>let's think back about what just happened here.</v> <v English>We've specified a position we wanted to reach and a time we wanted to</v> <v English>reach it at in some equations and we end up with a nice looking trajectory.</v> <v English>It's very nice indeed because a lot of drivers would not attain</v> <v English>that level of comfort if we were to ask them to reproduce it.</v> <v English>Now, let's see what happens if I try to reach the destinations more</v> <v English>quickly by turning down T. Sure enough,</v> <v English>we can still find the trajectory over time,</v> <v English>but it's much more jerky.</v> <v English>It is important to realize that although the trajectory that we generate</v> <v English>using this method or jerk optimal for a given set of boundary conditions,</v> <v English>they still depend heavily on these conditions.</v> <v English>Therefore, it would be important in the future to wisely pick these end conditions.</v> <v English>Now, I want to show you how I computed what</v> <v English>the six coefficient had to be in order to satisfy these boundary conditions.</v>
