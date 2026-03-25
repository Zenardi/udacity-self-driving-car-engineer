# Velocity Profile Generation

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=wU48Gs0kc1g)

## Summary

**Velocity Profile Generation**
=====================================

This project focuses on assigning a time component to each point of a discretized path by generating a velocity profile. The goal is to determine the speed at which the vehicle should travel at each way-point.

**Key Concepts**
---------------

* **Velocity Profile**: A time component assigned to each point of a discretized path, determining the speed at which the vehicle should travel.
* **Speed Constraints**: Three major contributors to the final speed calculation:
	+ **V_ref (Behavioral Planner Reference Speed)**: The speed requested by the behavioral planner based on the driving scenario.
	+ **V_lead (Leading Vehicle Speed)**: The speed of a leading vehicle, forcing the vehicle to be below it to avoid collision.
	+ **V_kf (Speed Based on Curvature at Goal Point)**: The maximum speed that can be traveled while complying with comfort constraints.
* **Final Speed**: Selected as the minimum of V_ref, V_lead, and V_kf to ensure no speed constraint is violated.
* **Linear Profiles**: Simple profiles where speeds follow a straight line connecting the starting speed and final speed.
* **Linear Composition Profiles**: Combination of linear profiles to achieve a desired behavior.

**Practical Notes**
------------------

To generate a velocity profile:

1. Calculate the final speed by selecting the minimum of V_ref, V_lead, and V_kf.
2. Assign speeds to path points between the start and end using various profiles (linear or linear composition).

Example use cases for linear composition profiles include:

* Decel-to-Stop profiles when approaching a red light or stop sign
* Gentle versus sportive driving experiences based on driving parameters

Note: The math behind each profile will be covered in the next section.

## Transcript

In this section, we're going to tackle the last piece of the motion planning problem. We must now assign a time component to each and every point of the discretized path. We can do so by either calculating the time at which the vehicle needs to reach every way-point, or by assigning a speed at which the vehicle needs to be traveling at, on each and every way-point. Speeds are ideal for a motion controller, and for this reason we will use the second approach. This is called velocity profile generation.

In the next slide we will explain how we can generate speed profiles according to what we want the vehicle to do. There are just two steps to follow on this process. First, we calculate the final speed at the end of the path, and then we follow a profile to assign speeds to the rest of the path points. Let's see exactly how we are going to do that. Let's start with step one and calculate the final speed.

There are three major contributors to this calculation. First, the behavioral planner reference speed V_ref. This is the speed that the behavioral planner is requesting us to go at. One example is a path with no stop signs or red lights. In this case, the behavioral planner will tell us to go at a speed limit.

Another example would be a stop maneuver, where our final speed would be at zero meters per second. Second is the leading vehicle speed V_lead. This is the speed that a leading vehicle is traveling at and forces us to be below it to avoid a collision. Finally, the speed based on the curvature at the goal point, V_kf. This is the maximum speed we can travel at to comply with the comfort constraint.

The final speed will be selected at the minimum of the three to make sure that we don't violate any of the given speed constraints. In the next slides, we will take a look at how to calculate V_kf, and how V_lead affects the way we assign the intermediate speeds. Let's start with the effects that V_lead has in the way we can proceed to generate the velocity profile. To guarantee that we will not collide with the vehicle ahead of us, we must assign a speed equal to the leading vehicle speed, V_lead, to the first path point that is at a safe distance behind it. All path points ahead of this point will get assigned V_lead speed, so we can guarantee no collision and a smooth following behavior.

You can see this represented with a red color circles in this example sketch. The rest of the points behind this point get assigned speeds accordingly to velocity profile, which we'll address in the next coming slides. Now let's focus on how we can calculate the speed based on a curvature at any point of the path. Let's remember that for now, we are interested in the final speed. This equation would allow us to calculate the maximum speed we can travel at, if we want to make sure we will not violate the maximum lateral acceleration allowed for comfort.

Remember that K_i, or Kappa_i, is the curvature at point i on the path. The final speed, which was the objective of the first step into velocity profile generation, is just a minimum of the three speeds we have introduced in the previous slides: V_ref, V_lead, and V_kf. At this point, we just need to focus on assigning speeds to the rest of the path points, those between the start and the final. There are many profiles we can follow to assign speeds to the path points between the start and the end. We are talking about assigning the speeds V_1, V_2, V_3, and so on.

The most simple and common profiles are: the linear profiles, where the speeds follow a straight line connecting the starting speed and the final speed, and the linear composition profiles, where we stitch together a few linear profiles to generate the intended behavior. In the next few slides we'll go over each type in detail. We are going to start with the linear profiles. As we said earlier, this profiles follow a line connecting the start and final speeds. This line means that the acceleration that our vehicle will follow will be constant at all times.

This three sketches you see here depict exactly this. On the first one, the acceleration is zero. On the second one, the acceleration is a constant positive number, and on the third one, the acceleration is a constant negative number. The linear composition profiles use a combination of linear profiles to achieve a desired behavior. The linear ramp profile you see depicted here on the left, uses an acceleration segment, segment one, and a constant velocity, segment two.

The sketch on the right is a perfect example of a Decel-to-Stop profile. You can see it's composed of three linear profiles. The first segment is a gentle deceleration to a transition speed V_t. Then a center segment, segment two, where we maintain a constant speed V_t, until we reach the beginning of the braking distance, and a third segment, with a gentle deceleration to a stop. You can see how we can build any linear profile by stitching this segments together.

We could create this profiles based on the driving scene. For example, a Decel-to-Stop profile when we get close to a red light or a stop sign, as you can see here, or based on some driving parameters to provide different experiences to the passengers. For example, gentle versus sportive driving. In the next section, we will dig deeper into the simple math for each one of this profiles.

## Additional Content

## Velocity Profile Generation 
We need to add a time element to our state vector **$(x_i, y_i, \Theta_i, \kappa_i)$**  by either:
- Calculating the “time” at which the vehicle needs to reach every waypoint
- Assigning a speed to each waypoint

**We will choose the latter since it will give us a nice and convenient target (the speed) for the motion controller.**

### Steps:
1. Calculate the **Final Speed$(V_f)$** at the end of the path
2. **Follow a speed profile** (adequate for the driving scene) to assign speed values to all path points in between.

### Calculate the **Final Speed

$(V_f)$** at the end of the path Contributors to calculate/select the **$Final Speed (V_f)$**:
- The Behavioral Planner reference speed: **$V_{ref}$**
- Leading Vehicle speed: **$V_{lead}$**
- Speed based on the curvature at the goal and the max comfortable lateral acceleration allowed: **$V_{\kappa f}$**

The final Speed will be:

$V_f = min (V_{ref}, V_{lead}, V_{\kappa f})$

### Velocity Profile when we have a vehicle ahead of us
- The first waypoint behind a safety distance from the vehicle ahead MUST have a speed not higher than $V_{lead}$. 
- The rest of the waypoints ahead should keep that speed $(V_{lead})$ to make sure there is no collision.
- A Velocity Profile will be applied only to the waypoints behind. This profile will depend on the driving scene. We might want to accelerate or we might have been traveling faster so we will slow down to $V_{lead}$.

### Velocity limit based on path point curvature

$(\kappa_i)
 V_{\kappa f} = \sqrt{( a_{max_lat} / \kappa_i)}$

### Velocity Profiles
Now we need to decide how we would generate all the speeds between

$V_0\, \, and \, \,  V_f: V_i (i=1,2,3,...)$

- Linear profiles: Constant Acceleration
- Linear composition profiles: Linear Ramp & Decel-to-Stop profiles (Trapezoidal)
