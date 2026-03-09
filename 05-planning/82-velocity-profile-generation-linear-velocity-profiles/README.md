# Velocity Profile Generation: Linear Velocity Profiles

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ZEAl2vFS0Ec)

## Summary

**Linear Velocity Profiles: A Building Block for Motion Analysis**
===========================================================

This lesson introduces linear velocity profiles, a fundamental concept in motion analysis. These profiles are characterized by constant acceleration and are used as building blocks to analyze more complex motion patterns.

### Key Concepts

* **Constant Acceleration**: The acceleration is always constant in a linear velocity profile.
* **Equations of Rectilinear Motion with Constant Acceleration**: These equations form the basis for calculations involving linear velocity profiles. Specifically, they include:
	+ `a = (v_f^2 - v_i^2) / 2 * d`
	+ `v_i = sqrt(2 * a * S_i + v_i^2)`
* **Path Points**: The path is divided into points (`i`) spaced at regular intervals. Each point has a corresponding distance traveled (`S_i`).
* **Maximum Speed Allowed (V_ki)**: Due to the curvature of the path, there may be a maximum speed allowed at each point.
* **Final Speed (V_if or V_i final)**: The minimum of both the calculated speed (`v_i`) and the maximum speed allowed (`V_ki`).

### Practical Notes

To apply these concepts in practice:

1. Calculate the constant acceleration required to achieve a specific final speed from an initial speed, given a fixed distance.
2. Use the equations of rectilinear motion with constant acceleration to calculate the speed at each point along the path.
3. Consider the curvature of the path and calculate the maximum speed allowed at each point (V_ki).
4. Determine the final speed at each point by taking the minimum of both the calculated speed and the maximum speed allowed.

By mastering these concepts, you'll be able to analyze linear velocity profiles and apply them to more complex motion patterns in various fields.

## Transcript

Let's just start with a linear velocity profiles, which are the building blocks of all the other profiles that we will see in this section. As we mentioned earlier, the main characteristic of this profile is that is represented by a line, and therefore the acceleration is always constant. We will base all our calculations on the well-known equations of rectilinear motion with constant acceleration. First, and since we know what the initial and final speeds are, we can just calculate what this constant acceleration should be. Let's do a small exercise to get you familiar with this.

We are going to calculate the constant acceleration that is required to go from an initial speed of two meters per second to our final speed of 10 meters per second when we have 40 meters to accomplish that. Following the equation you have here, we get that the acceleration is equal to 10 squared minus 2 squared divided by 2 times 40. This equates to 96 over 80, which is 1.2 meters per second squared. The second step after we have the acceleration is to calculate the speed at each point i on the path. In our example, i will vary from 1-7 as you can see here.

The speed at every point is the square root of 2 times the acceleration times S_i plus the initial speed squared. S_i is the distance traveled from the origin all the way to point i along the curve. In our example, S_3 would be 15 meters, for instance. Let's continue with the exercise we started so we can see how V_i is calculated for several points. In this example, we want to calculate V_1, V_2, V_3, all the way to V_7.

Let's recap very quickly what the problem conditions were. We had an initial speed of two meters per second. We calculated that the constant acceleration required was 1.2 meters per second squared. We also know that the path points are nicely spaced, five meters apart from each other. Now, if we apply the equation we have here, we get that V_1 is equal to the square root of 2 times the acceleration, 1.2 meters per second squared times the distance traveled to get to this point, which is five meters, plus the initial speed squared, which is two squared.

The result is about 2.8 meters per second. If we repeat this for V_7, we see that the only difference is that the distance traveled to get to 0.7 is 35 meters. In this case, V_7 is about 8.9 meters per second. You can pause the video and calculate the rest of the speed, V_2, V_3, all the way to V_6 to practice. Let's summarize what we have learned from the linear velocity profiles.

Since this profiles have always a constant acceleration, the first thing we do is calculate this acceleration. Once we have the acceleration, we calculate the speed at each point V_i, where i is just the path point number. Once we have this speed for every point, we must also calculate the maximum speed allowed at every point, V_ki, due to its curvature, which we already talked about earlier. The final speed at each point, V_if or V_i final, will be the minimum of both speeds.

## Additional Content

### Linear Velocity Profiles
1. This means we have always a constant acceleration:
  -

$a = \frac{(v_f^2 - v_0^2)} {2s_f}$

-

$s_f$

is known from solving the Path Planning Problem and is the total length of the curve

2. Once we have the constant acceleration we can calculate every single path point speed:

  -

$v_i = \sqrt{(2as_i + v_0^2)}$

- Where i = 1, 2, 3, 4, .... = all path points between 0 and final
3. Calculate the velocity limit due to curvature for all the points on the path.
  -

$V_{k_i}= \sqrt{( a_{maxlat} / k_i)}$

-  Where k

i

is the curvature at every path points "i" between 0 and final.

4. Finally chose the minimum
  -

$V_{i_final} = min (V_i, V_{k_i})$

## Check it out!

[https://www.desmos.com/calculator/pqspexvxut](https://www.desmos.com/calculator/pqspexvxut)
