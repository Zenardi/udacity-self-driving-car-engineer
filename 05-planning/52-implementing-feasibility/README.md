# Implementing Feasibility

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=8tD8Os9_gKc)

## Summary

**README: Initial Validation for Trajectory Feasibility**

This project provides a framework for initial validation of trajectory feasibility in autonomous vehicle navigation. The goal is to ensure that the planned trajectory meets certain safety and comfort criteria before executing it.

### Key Concepts

* **Neglecting road curvature**: For simplicity, we assume the road is locally straight.
* **Longitudinal acceleration**: We consider only the longitudinal acceleration (S double dot) of the car, assuming its heading is aligned with the road.
* **Acceleration limits**: The trajectory must satisfy two conditions:
	+ Acceleration must be less than the maximum engine supply acceleration
	+ Acceleration must be greater than the maximum braking deceleration
* **Lateral acceleration**: We check that all lateral acceleration (d double dot) values are below a fixed comfort threshold or rollover risk limit.
* **Steering angle and curvature**: The bicycle model relates steering angle to circle of curvature, with maximum allowed curvature given by:
	+ `κ = 1 / R`
	+ `R = L / tan(δ)`
* **Curvature for path**: We use the formula from the reading assignment: `κ = Δφi / (Δχi + ε)`

### Practical Notes

* To implement this validation, you'll need to:
	+ Define acceleration limits based on engine supply and braking deceleration
	+ Set a fixed lateral acceleration threshold or compute it using road friction information
	+ Use the bicycle model to calculate maximum allowed curvature at each point in the trajectory
	+ Check velocity against map-specified speed limits (maximal and minimal)

## Transcript

<v English>Here we're not going to discuss how to solve these feasibility check exactly.</v> <v English>But I want to give you a few hints about how to</v> <v English>do some initial validation for your trajectory.</v> <v English>In order to do so, we're going to neglect</v> <v English>the curvature of the road and assume it is locally straight.</v> <v English>Regarding longitudinal acceleration, we make</v> <v English>the additional assumption that our heading is pretty much aligned with the road.</v> <v English>This allows us to say that S doubled dots is the longitude acceleration of the car.</v> <v English>Therefore, we need to check that at any point of the trajectory,</v> <v English>this acceleration is less than</v> <v English>the maximum acceleration that the engine would need to supply,</v> <v English>and more than the maximum braking deceleration of the car.</v> <v English>Right now, this could be a fixed value.</v> <v English>In real life however,</v> <v English>this should probably be computed using information about the friction of the road.</v> <v English>Similarly, for lateral acceleration,</v> <v English>we can check that all d double dot values are less than</v> <v English>a fixed lateral acceleration value that can be set for comfort,</v> <v English>or to avoid any risk of rollover in our car.</v> <v English>Regarding steering angle, the bicycle model tells us that there's</v> <v English>a nice relationship between the steering angle of</v> <v English>the car and the radius of the circle of curvature,</v> <v English>where L is the distance between the wheel axis and R is the circle radius.</v> <v English>The curvature is then given by this formula,</v> <v English>and therefore the maximum curvature allowed at</v> <v English>any point of the trajectory is given by this equation.</v> <v English>If you remember, in the reading assignment about [inaudible]</v> <v English>the curvature for path is defined like this,</v> <v English>where Δφi is the heading difference between two points of</v> <v English>the trajectory and Δχi is the distance between them.</v> <v English>Finally the velocity is checked against</v> <v English>values specified by the map or the behavioral layer.</v> <v English>For example, we could use the speed limit of the road in most cases.</v> <v English>That gives us a maximal velocity but also sometimes,</v> <v English>we need a minimal velocity like on</v> <v English>highways where we don't want to drive too slow or we're backing up,</v> <v English>negative S dot is not allowed.</v>
