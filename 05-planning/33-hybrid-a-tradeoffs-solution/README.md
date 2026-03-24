# Hybrid A* Tradeoffs Solution

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6yAdF5u2B04)

## Summary

**Hybrid A* Algorithm**
=======================

The Hybrid A* algorithm is a continuous method that combines the benefits of A* with improved driveability. Unlike regular A*, Hybrid A* does not guarantee completeness or optimality, but it efficiently finds good paths in most cases.

### Key Concepts

* **Continuous Method**: The configuration space is not limited to a predefined discrete set.
* **Optimic Heuristic**: Similar to A*, Hybrid A* uses an optimic heuristic to guide the search.
* **Completeness and Optimality Trade-off**: Hybrid A* sacrifices completeness (i.e., it may not find a solution when one exists) in favor of driveability.
* **Driveability Guarantee**: The solutions found by Hybrid A* are guaranteed to be drivable, but not necessarily optimal.

### Practical Notes

Hybrid A* is an efficient algorithm for finding good paths almost all the time. However, it's essential to note that this comes at the cost of completeness and optimality guarantees. In practice, this trade-off can lead to significant improvements in pathfinding efficiency. 

Example Use Case:
```python
# Initialize Hybrid A* parameters
hybrid_a_star = HybridAStar(graph, start_node, goal_node)

# Run Hybrid A* algorithm
path = hybrid_a_star.find_path()

# Print the found path
print(path)
```
Note: The above code snippet is a simplified example and may not be directly applicable to your specific use case.

## Transcript

Now, unlike regular A*, Hybrid A* is a continuous method. Since, the configuration that we're end up being part of the trajectory are not part of a predefined discrete set. Similarly to A*, Hybrid A* star also uses an optimic heuristic. But one sacrifice made with Hybrid A* is that it does not always find a solution when one exists. Indeed, the completeness is sacrificed because we only allow one continuous configuration for discrete A*. The great improvement compared with A* is that the solution he does find are guaranteed to be driveable though not necessarily optimal compared to the properties of A*. With Hybrid A*, we have less completeness and optimality guarantees in favor of driveability. In practice, however, this algorithm is very efficient at finding good path almost all the time.
