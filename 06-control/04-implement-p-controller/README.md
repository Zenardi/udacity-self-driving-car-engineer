# Implement P Controller

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=OrJgrTc5d04)

## Summary

**Controller Implementation for Robot Navigation**

This project involves implementing a controller to navigate a robot along a desired path. The goal is to write code that simulates the robot's movement and steering based on its position and control parameters.

### Key Concepts

* **Proportional Controller**: A type of feedback control system where the output (steering angle) is proportional to the error between the current state and the desired state.
* **Crosstrack Error**: The difference between the robot's current y-coordinate and the x-axis, which serves as a measure of how far off course the robot is.
* **Tau (Response Strength)**: A parameter that sets the strength of the proportional controller's response to the crosstrack error.
* **Steering Angle Alpha**: The angle by which the robot turns in response to the crosstrack error, calculated as a proportion of the error.

### Practical Notes

To implement this project, you will need to:

1. Review the provided code for the `robot` class and its methods (`init`, `set`, `move`, etc.).
2. Implement the `run` command, which takes the control parameter `tau` as input and calculates the steering angle based on the crosstrack error.
3. Simulate the robot's movement for 800 steps using a proportionality term to set the steering angle in response to the crosstrack error.
4. Run the code with a coefficient of 0.1 to produce the desired output, which should show the robot navigating along the x-axis with overshooting and turning around.

**Example Code**

```python
class Robot:
    def __init__(self):
        self.x = 0
        self.y = 1
        self.speed = 1

    def run(self, tau):
        for i in range(800):
            crosstrack_error = self.y
            steering_angle = -crosstrack_error * tau
            # Update robot position and print output
```

Note: This is a simplified example code snippet to illustrate the key concepts. You will need to complete the implementation based on the provided instructions.

## Transcript

I want you to implement such a controller. Here is the code I've prepared for you. There is a class robot with which you're familiar. It has an "init." You can set the position using the function "set" as before. There are steering_noise and distance_noise.

You're familiar with this. There is also something called "drift," which you won't use right now, but later on it'll become handy. There is your move command, all the way we've implemented before. I've improved a little bit the print out of the coordinates using floats. I want you to implement the run command, which takes as input the control parameter that governs the proportional response of the steering angle to the crosstrack error.

The robot has an initial position of 0, 1, and 0, a speed of 1, and I wanted to simulate it for 100 steps. Here is what I envision to happen. Your robot is initially off the the x axis by 1. I want it to drive along the x axis. The y value is the same as the cross track error.

By turning, inversely proportional to the y value, using a parameter tau that sets the response strength of the proportional controller. I want the robot to turn towards the x axis, drive in that direction, overshoot, turn around, and drive back. To do this, simulate the world for a 800 steps, and use a proportionality term that sets my steering angle alpha in proportion to the crosstrack error y. Enter your code here, and when you're done with it, and you run it with the coefficient 0.1, here's the output that I want you to produce. It's 100 lines.

You can see the robot position starting 1 off in y. It then reduces y over time to go into negative territory. On the right side you see this corresponding steering orientation, and you can see as you move on the y coming back into positive territory, and you can see how the robot overshoots slowly around the reference trajectory of the x axis. Please go implement this.

## Additional Content

In the following quiz you'll implement a P controller.

Note that in all of the following programming quizzes the `run` function has been changed to return the x and y coordinates, or trajectory of the robot instead of printing the values. These will then be plotted against the reference line which should give you a better intuition for what the controller is doing. Thus, the code will look slightly different than in the videos but the general controller algorithms remain the same.
