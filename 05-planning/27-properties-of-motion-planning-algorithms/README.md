# Properties of Motion Planning Algorithms

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lNpD43L0qvw)

## Summary

**Planning Algorithms: Completeness and Optimality**
=====================================================

This project focuses on the fundamental properties of planning algorithms, specifically completeness and optimality. These concepts are crucial in ensuring that a planner can effectively find solutions to complex problems.

### Key Concepts
* **Completeness**: A planning algorithm is complete if it can always find a solution when one exists. If no solution exists, the planner should terminate and report this.
* **Optimality**: A planning algorithm is optimal if it returns the sequence that minimizes a given cost function. This ensures that the planner finds the most efficient or cost-effective solution.

### Practical Notes
When implementing a planning algorithm, consider the following:

* Ensure your algorithm is complete by testing it with both solvable and unsolvable problems.
* Define a clear cost function to optimize for optimality.
* Use examples like those shown in the lesson to illustrate completeness and optimality. For instance:
```python
# Example of an optimal solution (minimizes total distance traveled)
solution = [(0, 0), (3, 4), (6, 8)]
cost_function(solution)  # returns minimum cost

# Example of a non-optimal solution
solution = [(0, 0), (5, 5), (10, 10)]
cost_function(solution)  # returns higher cost than optimal solution
```
Note: The code above is just an example and may not be directly applicable to your project.

## Transcript

<v English>When discussing planning algorithms,</v> <v English>there are two important properties that we like to talk about.</v> <v English>The first one is called completeness.</v> <v English>And this means that if a solution exists through the multiplying problem,</v> <v English>the planner will find it.</v> <v English>And if a solution does not exist,</v> <v English>the planner will terminate and report that no solution exists.</v> <v English>So, consider the following two situations.</v> <v English>In the first one, the complete algorithm might correctly identify this as a solution.</v> <v English>and the second one,</v> <v English>the algorithm would terminates and tell us there is no solution.</v> <v English>Now, there may be something bothering you</v> <v English>about the solution identified in the first example.</v> <v English>Which brings us to the second property, optimality.</v> <v English>A planning algorithm is optimal if it always</v> <v English>return the sequence which minimizes some cost function.</v> <v English>So if we're using total distance traveled as a cost function for example,</v> <v English>then this would be an optimal solution while this would not.</v>
