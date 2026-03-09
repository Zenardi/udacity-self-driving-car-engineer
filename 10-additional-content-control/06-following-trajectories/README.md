# Following Trajectories

> Part of: **Vehicle Models**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=sOSHaAf_7b8)

## Summary

**Autonomous Vehicle System Architecture**
=============================================

This summary provides an overview of the key components and concepts in autonomous vehicle system architecture, including perception, localization, path planning, and control.

### Key Concepts

* **Perception System**: Estimates the state of the surrounding environment, including landmarks, vehicles, and pedestrians.
* **Localization Block**: Compares a model to a map to determine the vehicle's location.
* **Path Planning Block**: Charts a trajectory using environmental models, maps, and vehicle location.
* **Control Loop**: Applies actuators to follow the planned trajectory.
* **Polynomial Trajectory**: A mathematical representation of the planned path, often a third-degree polynomial that can fit most road types.

### Practical Notes

When implementing an autonomous vehicle system architecture, consider the following:

* The perception system is critical in accurately estimating the environment and providing input for subsequent blocks.
* The localization block relies on accurate mapping data to determine the vehicle's location.
* Path planning typically involves passing a reference trajectory as a polynomial (e.g., third-degree) from the path planning block to the control block.

## Transcript

<v English>Autonomous vehicle system architecture starts with the perception system,</v> <v English>which estimates the state of</v> <v English>the surrounding environment including landmarks and vehicles and pedestrians.</v> <v English>The localization block compares a model to a map to figure out where the vehicle is.</v> <v English>The path planning block charts a trajectory using environmental model,</v> <v English>the map and vehicle location.</v> <v English>Finally, the control loop applies the actuators to follow this trajectory.</v> <v English>Typically, the path planning block passes</v> <v English>the reference trajectory to the control block as a polynomial.</v> <v English>Third degree polynomials are common so they can fit most roads.</v>
