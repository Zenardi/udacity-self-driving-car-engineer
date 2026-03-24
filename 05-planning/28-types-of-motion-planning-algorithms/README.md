# Types of Motion Planning Algorithms

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6-K1aLTEvk8)

## Summary

**Motion Planning Algorithms: An Overview**
=============================================

This project explores various classes of motion planning algorithms used in robotics and autonomous systems. The goal is to understand the strengths and limitations of each approach, enabling informed decision-making when selecting an algorithm for a specific application.

### Key Concepts
---------------

* **Combinatorial Methods**: Divide free space into small pieces (atomic elements) and solve motion planning by connecting these elements.
	+ Pros: Intuitive initial solution; Cons: Scales poorly in large environments.
* **Potential Fields**: Obstacles create anti-gravity fields, repelling vehicles and preventing collisions.
	+ Pros: Easy to implement; Cons: May get stuck in local minima.
* **Optimal Control**: Solve motion planning and control problems simultaneously using a dynamic model and numerical optimization methods.
	+ Pros: Minimizes gas consumption and maintains distance from other vehicles; Cons: Difficult to incorporate constraints related to other vehicles.
* **Sampling-Based Methods**: Use collision detection modules to probe free space, reducing the need for exhaustive environment analysis.
	+ Pros: Easier to compute definition of free space; Cons: May not be probabilistically complete or optimal.

### Practical Notes
-------------------

When implementing motion planning algorithms, consider the following:

* Combinatorial methods are suitable for small environments but may not scale well.
* Potential fields can be used to avoid collisions with pedestrians or other vehicles.
* Optimal control methods require numerical optimization and may struggle with incorporating constraints related to other vehicles.
* Sampling-based methods use collision detection modules and graph search algorithms (e.g., D*, A*) to efficiently explore the environment.

This project aims to provide a foundation for understanding motion planning algorithms. Further exploration of specific algorithms, such as Hybrid A*, is encouraged to deepen knowledge in this area.

## Transcript

There are many classes of Motion Planning Algorithms. And today, we'll focus on one of these classes, but it is worth mentioning the others. Combinatorial Methods usually consists in dividing the freespace into small pieces, and first solving the motion planning problem by connecting these atomic elements. There are very intuitive ways to find an initial approximate solution, but they usually do not scale well for large environments. Next, potential fields are reacting methods, each obstacle is going to create a sort of anti-gravity field, which makes it harder for the vehicle to come close to it. For example, you can imagine using this idea around pedestrians or bikes to include your Planning Algorithm to find Trajectories that stay away from them. The main problem with most Potential Field Methods, is that they sometimes push us into Local Minima which can prevent us from finding a solution. Optimal Control consists in trying to solve the Motion Planning Problem, and the Controlling PoD Generation in one Algorithm. Using a dynamic model for a vehicle, or start configuration, then end configuration, we want to generate a sequence of inputs. For example, steering goal and throttle input that would lead us from start to end configuration, while optimizing a cost function relative to the control inputs, such as minimizing gas consumption and relative to the configuration of the car. Such as staying at a distance from other vehicles. There are a lot of very nice ways to do that. Most of them based on Numerical Optimization Methods. However, it is hard to incorporate all of the constraints related to the other vehicles in a good enough way, in order for these Algorithms to work fast. And finally, there are Sampling Based Methods which are what we will focus on today. These Algorithms are very popular because they require a somewhat easier to compute definition of the free space. Sampling Based Methods use a Collision Detection Module, that probes the free space to see if a configuration is in collision on that. Unlike Combinatorial or Optimal Control Methods which analyzes the whole environment, not all parts of the free space need to be explored in order to find a solution. Explored parts are stored in a graph structure that can be searched with a Graph Search Algorithm like D* or A*. Two main classes of methods can be identified as Sampling Based. Discrete methods which rely on a finer set of contributions and or inputs like a grid superposed on top of our configuration space. And Probabilistic methods which rely on the probabilistic sample of a continuous configuration space. The set of possible configurations or states that will be explored is potentially infinite, which gives some of these methods the nice property that they are Probabilistically complete. And sometimes, Probabilistically Optimal, meaning that they will always find a solution, if you allow them enough computation time. We have barely scratched the surface on all the different sorts of Planning Algorithms that exist. Far from me the idea to create an exhaustive list, I strongly encourage you to look up some of these Algorithms and learn more about how they work. Next, I'm going to present the Hybrid A* Algorithm. But before that, I suggest you really watch a video you saw earlier on A* and then answer a few questions about some of its properties.
