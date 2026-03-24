# Hybrid A* in Practice

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Mkz_WjyRzag)

## Summary

**Hybrid A* Algorithm: A Summary**

This README file provides an overview of the Hybrid A* algorithm, its key concepts, and practical notes.

### Key Concepts

* **Configuration Space**: The space where the robot's configuration is represented, including position, orientation, and velocity.
* **Omega (Ω)**: The heading rate of change, which can be specified independently or using a bicycle model for more realistic car behavior.
* **Bicycle Model**: An equation that relates Omega to the distance between the front and rear axle, steering angle, and constant positive velocity.
* **Steering Angles**: A set of possible steering angles used in the Hybrid A* algorithm, typically including maximum left steer, zero steer, and maximum right steer.
* **Motion Primitives**: Basic actions that the robot can take, such as going straight, turning left, or turning right.

### Practical Notes

When implementing the Hybrid A* algorithm:

* Use a bicycle model to specify Omega for more realistic car behavior.
* Choose a set of steering angles that balance exploration and computation time. In this example, three angles are used: maximum left steer, zero steer, and maximum right steer.
* Keep track of not only the cell's position but also its orientation and heading.
* Consider using a three-state space that includes heading to reduce premature closure of cells.

Example use case:

* Given a maze with a start position and goal position, use Hybrid A* to find a path from the start to the goal. The algorithm will expand the search tree by generating trajectories for each possible steering angle, discarding infeasible or colliding paths.
* Continue expanding the search tree until the goal is reached or no more feasible paths are found.

Note: This summary provides an overview of the key concepts and practical notes from the lesson transcript. For a complete understanding of the Hybrid A* algorithm, refer to the original lesson material.

## Transcript

In the first video about Hybrid A*, the update equations that we used were somewhat generic to most X Y field configuration spaces. In particular, we don't specify what Omega is. Omega is the heading rate of change. Now for some robots, it might be that we can specify any omega independently of its state. But that would mean that the robot can turn around its Z axis without constraints. For car though, this is not very realistic, and we should probably use the bicycle model. This gives us an equation for Omega like this. Here, 'L' is the distance between the front and rear axle, 'δ' is the steering angle and ⱴ is the constant positive velocity. Now, for our Hybrid A* algorithm, we need to decide which configuration can be reached from the current node considered, in order to add them to the open set. In practice, we would probably use some number of steering angles between maximum left steer and maximum right steer angle. But the more different Deltas you add the longer it takes for your algorithm to complete. Therefore, in this example, we will only choose three angles to pick delta from; the maximum left steering angle, zero steering angle and the maximum right steering angle. In the case of a car that can turn its wheels 35 degrees at most, that would be -35, 0 and 35. This allows us to expand the search tree with three new motion primitives; go straight, steer left and steer right. Let's see how that works in a robot maze. Let's say we have a maze like this. The red square is the goal and this is the start position. The first thing we would do is add this cell to open list. I'll use gray to indicate that. And then we would generate three trajectories, the one for going straight, the one for turning right, the one for turning left. And in this case, we can discard the trajectories that go off the map or collide. This gives us one new cell to open, which we do, and then we mark the first cell closed which am indicating with this check-mark. Now, there is only one open cell so I choose to expend that one next. And again, I generate the three trajectories from this stage, one of them is infeasible, so let's not keep looking at it. And this leaves us with two new cells to open. I close the previous. Now there are two choices of what cell to expand. Assuming i have some heuristic that values being closer to the goal, I choose the cell on the right, and then generate trajectories from this new state. Note, how, in all these steps, I'm keeping track of, not just what cell I am in, but also where in that cell I am, including orientation. In practice, we could also use a three state space that include heading. If we don't do that, then we're likely to prematurely close cells. I'm not doing it that way here, mostly because it's harder to visualize. Let's keep going. I have three new cells to open. I have to close the previous cell, find the best option in the set of open cells and repeat. Again leaving me with three new cells to add to the open list. Which means I can close the the previous cells and things get a little more interesting here. My heuristic will probably suggest that I expand the lower right cell and generate trajectories from there. But this time, all of them would collide with the wall. Therefore, I don't need to add any new cell to the open set. Now, since I did expand this cell I have to mark it closed, and then I can look at my remaining open cells. So same as before, I take a closest cell the goal, generate trajectories, that is, that all of these collides and close that cell. Of the remaining open cells, this upper right one is closest or the one with the best heuristic. So I repeat the process, on and on, until I reach the goal. Now, let's look at what this trajectory really looks like by getting rid of some of the clutter. And what we're left with is a continuous path, that might not be the smoothest solution to our planning problem. Indeed we can easily find examples of environment, where the resulting path doesn't look very good compared to what human drivers would have done in this situation. And that's not the only problem. Sometimes, everyday stuff fails to even find the solution when one actually exists. For example, let's go back to the stage in the algorithm and consider what would happen if the map were slightly changed. In this case, we would have made all the same decisions up until this point. But now we have close this crucial cell. Clearly, there is a path to the goal that could be reached. But in these circumstances, Hybrid A* will not find any. We can reduce the likelihood of this problem by increasing the resolution of our grid or adding a third dimension to the search space for the heading. Indeed, this would allow us not to close this position in the map for all headings but only for a specific range which may allow us to find the solution in this-