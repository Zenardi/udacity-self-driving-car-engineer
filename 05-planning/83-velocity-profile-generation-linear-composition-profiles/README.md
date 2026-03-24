# Velocity Profile Generation: Linear Composition Profiles

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=dhBYhFQkzGU)

## Summary

### Composition Profiles for Speed Planning

This project focuses on creating composition profiles for speed planning in autonomous vehicles. Composition profiles are used to determine the speeds at which a vehicle should travel through different segments of its path.

### Key Concepts

* **Decel-to-stop profile**: A composition profile with three segments: constant deceleration, transition-speed cruise, and final deceleration.
* **Transition speed ($V_t$)**: The speed at which the vehicle transitions from one segment to another.
* **Gentle deceleration ($a$)**: The target deceleration used by the profile.
* **Distance ($s_t$)**: The distance required for the vehicle to reach transition speed $V_t$.
* **Speed calculation**: The process of determining the speeds at each point on the path, taking into account curvature and other factors.

### Practical Notes

To implement a decel-to-stop profile, you will need to:

1. Calculate the distance $s_t$ required to reach transition speed $V_t$:

   $$
   s_t = \frac{V_t^2 - v_0^2}{2a}
   $$

2. Calculate speed at each point on segment 1:

   $$
   v_i = \sqrt{2as_i + v_0^2}
   $$

3. Calculate the distance required to slow down from $V_t$ to final speed $V_f$.
4. Calculate the speeds at each point on the third segment using the same equation as above.
5. Assign constant speed $V_t$ to all points between $s_t$ and $s_b$.

You will also need to handle edge cases where the discriminant is negative or infinite, and ensure that you can calculate the square root of the discriminant.

The code for this project involves implementing the equations mentioned above in a programming language. You will need to write functions to calculate the final speed and distance traveled given an initial speed, acceleration, and distance.

## Transcript

Let's move on to the composition profiles. We're going to use the decel-to-stop profile as an example of how to build these profiles. In particular, this profile has three linear segments, and in the next few slides, we will address each segment separately. Let's focus on the first segment for now. This segment is a constant deceleration segment similar to what we've seen earlier.

We will start calculating the distance, s_t or deceleration distance required to reach a transition speed, V_t from the vehicle's current speed assuming a gentle deceleration a. Both the transition speed V_t and the gentle deceleration a will be chosen by us depending on the profile we want to create. The next step, consistent calculating the speed of every point that falls between the starting point s_0 and s_t. Remember that as we mentioned earlier in previous slides, the distance s_i is the distance traveled from the origin of the curve to point i. The third step as usual, is to calculate the maximum speed allowed at each one of these points due to their curvature.

Finally, we choose the final speed at every point i as the minimum between the both V_i and V_ki. Let's jump into the third segment. The reason we have skipped the second segment for now is because we need first to know the distance s_b, that the second segment we'll extend to. This distance can only be calculated with the third segment information. Let's see how that is.

Since we know the final speed V_f, and we know that on the third segment we start at speed V_t, we can figure out the distance will take to slow down from V_t to V_f, assuming a gentle deceleration a. That distance subtracted from the total length of the path will give us s_b. In a similar fashion as we did earlier, we can now calculate the speed V_i at every point on the third segment by applying the same common equation with the difference that now our initial speed is V_t and the distance traveled is s_i minus s_b. As it's usual, we must calculate also the maximum speed allowed at each point due to its curvature. Finally, we choose the final speed at every point i on the third segment as the minimum of both values.

Feel free to pause the video and take a look at these equations until you understand every detail. Now that we know the distance s_b, we can go back to the second segment. All the points that fall between s_t and s_b will be assigned a constant speed, V_t. As it's usual, we must calculate also the maximum speed allowed at each point due to its curvature. Finally, we choose the final speed at every point i on the second segment as the minimum of both.

Let's check how it looks when we put all these three segments together. In the previous few slides, we explained that first we calculate the s_t, the distance needed to ramp down the speed from our initial speed to a transition speed V_t assuming a gentle deceleration. With that information, we calculated V_i for all points on the first segment. Then we moved to the third segment and started calculating the distance required to slow down from V_t to our final speed V_f, assuming a gentle deceleration. With that distance, we calculated the speed of all points lying on the third segment.

Finally, the second segment corresponded to all points lying between s_t and s_b, all having a constant speed V_t. Before assigning any of these speeds we calculated, we also calculated the maximum speed at every point due its curvature, and we selected the minimum of both. Let's recap what we learned in this section. We introduced the two steps required to generate speed profiles. The first step was to calculate the final speed V_f at the end of the path, given the information from the behavioral planner, the leading vehicle speed, and the speed restrictions due to curvature.

The second step was to apply any speed profile that fits the driving scene and generate the speeds between the starting point and the endpoint accordingly. We also presented some of the most common speed profiles and how they can be built from a combination of several linear profiles. Finally, we walked through the steps to assign speeds to every point on the path while using a decel-to-stop speed profile example. In this video, we'll go through velocity profile exercise. We're going to start looking at the code and the exercise description.

We have to calculate the final speed given an initial speed and acceleration and a distance. Here's the equation. The second part of the problem is to calculate the distance traveled given an initial speed of final speed and an acceleration. Here's the equation. We're going to tackle the first part of the problem, which is calculate the final speed.

This is located in this function, calc-final-speed. As we mentioned earlier, you are giving the initial speed, the acceleration, and the distance and you just need to follow this equation. One of the most important things that you need to take into account is that the discriminant, which is the inside of the square root, may not be negative because otherwise you will not be able to calculate the square root. As a requirement, if the discriminant is negative, you will return v_f equals 0, final speed will be 0. If for whatever reason the discriminant is infinite or not a number to prevent any errors or the function to crash, you will return infinity.

The first part of the to do is write the discriminant, which is basically the inside of the square root, then after you have the discriminant, you have to handle the different aspects of the if statement here. If it's negative and is less than zero, you know that you can not calculate the square root and therefore you've been asked to return v_f equals 0, which is here. If the discriminant is actually infinite or not a number, you know that also you cannot calculate the square root and that's why you're going to return infinite as you've been told here. Finally, if nothing went wrong, you might be able to calculate the square root of the discriminant and you will have to return this value. The second part of the problem is to calculate the distance.

In this case it's calculated distance given the initial velocity, the final velocity, and an acceleration. The equation has been given to you before and it's also here to remind you how to do it. The only thing you need to take care of is to make sure that you can handle a division by zero. Here is where you going to place your code and make sure that you take care of any acceleration that is equal to zero. As a hint, I'm telling you here that the way to express this is by using this if statement.

If the absolute value of the acceleration has a very small number, you know that the division will go to infinity. In this case you will return infinity.

## Additional Content

### Linear composition profiles

#### Segment 1

1. Calculate the distance $S_t$ required to reach $V_t$ from $V_0$ using gentle accel/decel $a$. $V_t$ and $a$ are design parameters.

   $$
   S_t = \frac{V_t^2 - V_0^2}{2a}
   $$

2. Calculate the speed for every point between $S_0$ and $S_t$:

   $$
   v_i = \sqrt{2as_i + v_0^2}
   $$

   Where:
   - $s_i$: distance traveled from the path origin to point $i$
   - $i = 1, 2, 3, \ldots$: all path points between $S_0$ and $S_t$

3. Calculate the speed limit at the same points based on curvature $k_i$ and maximum comfortable lateral acceleration:

   $$
   V_{k_i} = \sqrt{\frac{a_{maxlat}}{k_i}}
   $$

4. Choose the minimum:

   $$
   V_{i_{final}} = \min(V_i, V_{k_i})
   $$

#### Segment 3

1. Calculate the distance $S_b$ required to reach $V_f$ from $V_t$ using gentle accel/decel $a$.

   $$
   S_b = S_f - \frac{V_f^2 - V_t^2}{2a}
   $$

2. Calculate the speed for every point between $S_b$ and $S_f$:

   $$
   v_i = \sqrt{2a(s_i - s_b) + v_t^2}
   $$

   Where:
   - $s_i$: distance traveled from the path origin to point $i$
   - $i = 1, 2, 3, \ldots$: all path points between $S_b$ and $S_f$

3. Calculate the speed limit at the same points based on curvature:

   $$
   V_{k_i} = \sqrt{\frac{a_{maxlat}}{k_i}}
   $$

4. Choose the minimum:

   $$
   V_{i_{final}} = \min(V_i, V_{k_i})
   $$

#### Segment 2

1. Assign constant speed to all points between $S_t$ and $S_b$:

   $$
   V_i = V_t
   $$

2. Calculate the speed limit for the same points based on curvature:

   $$
   V_{k_i} = \sqrt{\frac{a_{maxlat}}{k_i}}
   $$

   Where $k_i$ is the curvature at all path points between $S_t$ and $S_b$.

3. Choose the minimum:

   $$
   V_{i_{final}} = \min(V_i, V_{k_i})
   $$

Where $i$ includes all path points between $S_t$ and $S_b$.
