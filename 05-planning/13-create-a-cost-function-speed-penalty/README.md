# Create a Cost Function - Speed Penalty

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=wGRDT2wTnn8)

## Summary

**Designing Cost Functions for Vehicle Speed Control**
=====================================================

This README file provides a summary of the key concepts and practical steps involved in designing cost functions for vehicle speed control.

### Key Concepts

* **Cost Functions**: A mathematical representation of the penalties or rewards associated with different velocities.
* **Velocity**: The rate at which an object moves, measured in miles per hour (mph) or other units.
* **Desired Velocity**: The target velocity that the vehicle should aim for.
* **Speed Limit**: The maximum allowed velocity on a particular road or route.
* **Cost Function Domains**:
	+ **Zero-Velocity Case**: The cost associated with not moving at all.
	+ **Target Speed Range**: The range of velocities between the desired velocity and the speed limit.
	+ **Above-Speed-Limit Case**: The cost associated with exceeding the speed limit.

### Practical Notes

* To design a cost function, consider the trade-off between reaching the destination quickly and avoiding excessive speeds that may be illegal or hazardous.
* Assign costs to different velocities based on their desirability, with higher costs for undesirable velocities (e.g., above the speed limit).
* Use linear functions to connect points in the cost function graph, making it easier to adjust parameters later.
* Define parameters such as **Stop Cost** and **Buffer Velocity** to control the behavior of the cost function.

Example code snippet:
```python
import numpy as np

# Define the cost function domains
def zero_velocity_cost(velocity):
    return Stop_Cost

def target_speed_range_cost(velocity, desired_velocity, speed_limit):
    if velocity < desired_velocity:
        return (desired_velocity - velocity) / (speed_limit - desired_velocity)
    elif velocity > speed_limit:
        return 1.0
    else:
        return 0.0

# Define the overall cost function
def cost_function(velocity, desired_velocity, speed_limit):
    if velocity < desired_velocity:
        return zero_velocity_cost(velocity) + target_speed_range_cost(velocity, desired_velocity, speed_limit)
    elif velocity > speed_limit:
        return 1.0
    else:
        return 0.0
```
Note that this is a simplified example and actual implementation may vary depending on the specific requirements of the project.

## Transcript

<v English>A key part of getting transitions to happen when we want</v> <v English>them to is the design of reasonable cost functions.</v> <v English>We want to penalize and reward the right things.</v> <v English>I'm going to work through an example of</v> <v English>one way you might think about designing a cost function.</v> <v English>Let's consider how we would design a cost function for vehicle speed.</v> <v English>On one hand, we want to get to our destination quickly,</v> <v English>but on the other hand,</v> <v English>we don't want to break the law.</v> <v English>An essential quantity we have to control is the desired velocity of the car.</v> <v English>Some velocities are more beneficial,</v> <v English>some are even illegal.</v> <v English>Let's fill in this graph and try to assign some costs to every velocity.</v> <v English>For the sake of simplicity,</v> <v English>let's assume that all of the cost functions will have an output between zero and one.</v> <v English>We will adjust the importance of each cost function later by adjusting the weights.</v> <v English>Let's say the speed limit for the road we are on is here.</v> <v English>Well, we know that if we're going well above the speed limit,</v> <v English>that should be maximum cost.</v> <v English>And maybe we want to set</v> <v English>an ideal zero cost speed that's</v> <v English>slightly below the speed limit so that we have some buffer.</v> <v English>And then we can think about how much we want to penalize not moving at all.</v> <v English>Obviously, not moving is bad,</v> <v English>but maybe not as bad as breaking the speed limit,</v> <v English>so we would put it here.</v> <v English>To keep it simple,</v> <v English>we could just say there is a linear cost between zero and the target speed.</v> <v English>And since breaking the law is a binary thing,</v> <v English>let's just say any speed greater than or equal the speed limit has maximal cost.</v> <v English>And again, we can arbitrarily connect these points with</v> <v English>a linear function and the flat maximum cost for anything above the speed limit.</v> <v English>Now, in practice, we might actually want to parametrize some of</v> <v English>these quantities so that we could later adjust them until we got the right behavior.</v> <v English>So first, we might define a parameter called Stop Cost for</v> <v English>the zero-velocity case and a parameter called</v> <v English>buffer velocity which would probably be a few miles per hour.</v> <v English>Then, our overall cost function has three domains.</v> <v English>If we're going less than the target speed,</v> <v English>the cost function would look like this.</v> <v English>If we are above the speed limit,</v> <v English>the cost is just one.</v> <v English>And if we are between,</v> <v English>the cost would look like this. Awesome.</v>
