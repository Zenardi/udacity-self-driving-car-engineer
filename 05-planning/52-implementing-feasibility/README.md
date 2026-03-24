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

Here we're not going to discuss how to solve these feasibility check exactly. But I want to give you a few hints about how to do some initial validation for your trajectory. In order to do so, we're going to neglect the curvature of the road and assume it is locally straight. Regarding longitudinal acceleration, we make the additional assumption that our heading is pretty much aligned with the road. This allows us to say that S doubled dots is the longitude acceleration of the car. Therefore, we need to check that at any point of the trajectory, this acceleration is less than the maximum acceleration that the engine would need to supply, and more than the maximum braking deceleration of the car. Right now, this could be a fixed value. In real life however, this should probably be computed using information about the friction of the road. Similarly, for lateral acceleration, we can check that all d double dot values are less than a fixed lateral acceleration value that can be set for comfort, or to avoid any risk of rollover in our car. Regarding steering angle, the bicycle model tells us that there's a nice relationship between the steering angle of the car and the radius of the circle of curvature, where L is the distance between the wheel axis and R is the circle radius. The curvature is then given by this formula, and therefore the maximum curvature allowed at any point of the trajectory is given by this equation. If you remember, in the reading assignment about [inaudible] the curvature for path is defined like this, where Δφi is the heading difference between two points of the trajectory and Δχi is the distance between them. Finally the velocity is checked against values specified by the map or the behavioral layer. For example, we could use the speed limit of the road in most cases. That gives us a maximal velocity but also sometimes, we need a minimal velocity like on highways where we don't want to drive too slow or we're backing up, negative S dot is not allowed.
