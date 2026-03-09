# A* Reminder Solution

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=HtQjw7qr2-o)

## Summary

**A\* Algorithm Fundamentals**
=====================================

This summary covers the key concepts and practical notes from a lesson on the A\* algorithm, a complete planning algorithm used for finding the shortest path between two points in a weighted graph or network.

### Key Concepts
* **Discrete States**: The first step before running A\* is to define a discrete set of states that represent the world you want to plan in.
* **Optimistic Heuristic**: A valid A\* heuristic must be optimistic, meaning it should underestimate the actual cost to go from one cell to another.
* **Completeness**: A\* always finds a solution if one exists, making it a complete planning algorithm.
* **Graph Search Algorithm**: A\* is a graph search algorithm that can be used on more complex search spaces, including those with headings and restricted connections between cells.

### Practical Notes
* When using A\*, the discretization of the environment affects the quality of the solution. The more granular the discretization, the better the solution.
* To ensure derivable paths when moving a car or other object, define a complex search space including heading and restrict connections between cells to only those that are drivable.

**Example Code**
```python
# Define a discrete set of states (e.g., positions x, y)
states = [(x, y) for x in range(10) for y in range(10)]

# Define an optimistic heuristic function (e.g., Euclidean distance)
def heuristic(state):
    return math.sqrt((state[0] - goal[0])**2 + (state[1] - goal[1])**2)

# Run A\* algorithm
path = a_star_search(states, heuristic, start, goal)
```

## Transcript

<v English>And the answer to the first question is No.</v> <v English>The first step before running A* is defining</v> <v English>a discrete set of states that represent the world we want to plan in.</v> <v English>Before we say A* is a discrete method.</v> <v English>For the second question, the answer is yes.</v> <v English>In order to be a valid,</v> <v English>A* heuristic have to be optimistic.</v> <v English>Meaning that they should underestimate the actual cost to go from the cell to the goal.</v> <v English>A* does always find the solution if one exists.</v> <v English>Which as you recall meaning that A* is a complete planning algorithm.</v> <v English>So, the next assertion is somewhat tricky</v> <v English>because it depends on the search space that is being used and what it represents.</v> <v English>If the search space represent only the position x,</v> <v English>y like you saw in the previous examples,</v> <v English>and we're trying to move a car,</v> <v English>there is no guarantees that the sequence of position returned by A* will be drivable.</v> <v English>Therefore, the answer to this question is no.</v> <v English>However, remember that A* is the graph search algorithm.</v> <v English>We can define a more complex search space including heading</v> <v English>for example and restrict connections between cells such</v> <v English>that when we close a cell we add to the up and set only cells</v> <v English>such that the transition from the closing cell to the new cells are derivable.</v> <v English>If we do that the resulting path will be derivable as well.</v> <v English>This corresponds to running A* on the letters.</v> <v English>Now the last question.</v> <v English>It is true that the solution A* finds are always</v> <v English>optimal with respect to the discretization of the environment that was used as an input.</v> <v English>The more granular the discretization,</v> <v English>the better the solution.</v> <v English>We call this resolution optimal.</v>

## Additional Content

## Note Regarding A* Heuristics and Optimal Solutions:
  A\* will find an optimal solution if the heuristic is [Admissible](https://en.wikipedia.org/wiki/Admissible_heuristic).  A* may find a suboptimal path if the heuristic function is not Admissible.
