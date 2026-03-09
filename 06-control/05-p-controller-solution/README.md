# P Controller Solution

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=wvdFPAOCb64)

## Summary

**Robot Control Implementation**
=====================================

This README file summarizes the implementation of a basic robot control system, which involves executing a loop to adjust the steering angle based on the crosstrack error.

**Key Concepts**
---------------

* **Crosstrack Error**: The difference between the robot's current position and its target position in the x-axis.
* **Steering Angle**: The angle at which the robot turns to correct its course.
* **Control Parameter**: A constant value used to adjust the steering angle based on the crosstrack error.
* **Move Command**: A function that takes a steering angle and speed as input and moves the robot accordingly.

**Practical Notes**
------------------

The implementation provided in this lesson is a simple example of how to control a robot's movement. The code executes a loop 100 times, updating the steering angle based on the crosstrack error using the formula:

`steering_angle = -control_parameter * crosstrack_error`

The `move_command` function is then called with the updated steering angle and speed to move the robot. This implementation can be used as a starting point for more complex robot control systems.

**Code**
```python
for _ in range(100):
    # Set crosstrack error to robot y position
    crosstrack_error = robot.y
    
    # Calculate steering angle based on crosstrack error and control parameter
    steering_angle = -control_parameter * crosstrack_error
    
    # Call move command with updated steering angle and speed
    move_command(steering_angle, speed)
    
    # Print output: robot along with steering direction
    print(robot, "steering", "left" if steering_angle < 0 else "right")
```

## Transcript

Here is my implementation. It's really simple. I execute the following loop 100 times. I set the crosstrack error to my robot y. The steering angle becomes minus my control parameter times the crosstrack error.

I call the move command with a steering angle and the given speed. I print as an output my robot along with the steering direction. This simple routine just does it.

## Additional Content

```python
def run(robot, tau, n=100, speed=1.0):
    x_trajectory = []
    y_trajectory = []
    for i in range(n):
        cte = robot.y
        steer = -tau * cte
        robot.move(steer, speed)
        x_trajectory.append(robot.x)
        y_trajectory.append(robot.y)
    return x_trajectory, y_trajectory
```

The cross track error, `cte` is the current y position of the robot (our reference is a horizontal line) along the x-axis. To get the steering value we multiply the `tau` parameter with the cte. We then call the `move` method which causes the robot to move based on the `steer` and `speed` values. Add the x and y coordinates to the respective lists and then return them at the end.
