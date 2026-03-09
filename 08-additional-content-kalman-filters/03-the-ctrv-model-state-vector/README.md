# The CTRV Model State Vector

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=hLVz0YOhntA)

## Summary

**CTRV Model: A More Realistic Motion Model**

The CTRV (Constant Turn Rate and Velocity) model is an extension of the previous motion model, which assumed objects move in a straight line. This new model accounts for objects that can change direction while maintaining a constant speed.

### Key Concepts

* **CTRV Model**: A more realistic motion model that assumes objects can move with a constant turn rate and velocity magnitude.
* **State Vector**: The CTRV model uses a state vector to describe the object's position, speed, yaw angle, and yaw rate. The state vector is represented as follows:
```python
[x, y, v, psi, psi_dot]
```
	+ `x` and `y`: The two-dimensional position of the object.
	+ `v`: The magnitude (speed) of the velocity.
	+ `psi`: The orientation (yaw angle) of the object.
	+ `psi_dot`: The rate of change of the yaw angle (yaw rate).
* **Constant Turn Rate**: The CTRV model assumes that the object's turn rate is constant, which means it can change direction while maintaining a consistent rate of turn.

### Practical Notes

The CTRV model is often used in real-world traffic scenarios to predict vehicle behavior. By incorporating the yaw rate and speed into the state vector, the model becomes more accurate for objects that can change direction quickly. This model provides a more realistic representation of motion, which is essential for applications such as autonomous vehicles or robotics.

## Transcript

<v English>The model we use so far assumes</v>
<v English>objects always keep going straight.</v> <v English>The model we will use from now on</v>
<v English>assumes objects can move straight, but</v> <v English>they can also move with a constant turn</v>
<v English>rate and a constant velocity magnitude.</v> <v English>This model is often</v>
<v English>called the CTRV model.</v> <v English>Let's have a look at the state</v>
<v English>vector we are going to use.</v> <v English>We keep calling the two-dimensional</v>
<v English>position of the bike px and py,</v> <v English>where p stands for position.</v> <v English>But instead of describing the velocity</v>
<v English>with vx and vy, we use the speed and</v> <v English>yaw angle.</v> <v English>The speed is the magnitude of</v>
<v English>the velocity, which we'll call v.</v> <v English>And the yaw angle is the orientation,</v>
<v English>which we'll call psi.</v> <v English>Since we also want to be able to</v>
<v English>estimate the yaw rate psi dot,</v> <v English>we add it to the state vector too.</v> <v English>Constant yaw rate and</v>
<v English>constant speed is a good model for</v> <v English>vehicle behavior in</v>
<v English>real traffic scenarios.</v> <v English>Let's try to get a feeling for that.</v>

## Images

![A diagram of the CTRV model.](images/screenshot-from-2017-02-27-20-45-49.png)
*A diagram of the CTRV model.*

## Additional Content

In the following quizzes, you'll be using state vectors to draw qualitative observations about the motion of turning objects.

### General State Vector

$$x = \begin{bmatrix}
p_x\\
p_y\\
v\\
\psi\\
\dot{\psi}
\end{bmatrix}$$

### State Vector 1

$$x = \begin{bmatrix}
2 \space m\\
4 \space m\\
7 \space m/s\\
0.5 \space rad\\
0.6 \space rad/s
\end{bmatrix}$$

### State Vector 2

$$x = \begin{bmatrix}
2 \space m\\
4 \space m\\
7 \space m/s\\
0.5 \space rad\\
0 \space rad/s
\end{bmatrix}$$

### State Vector 3

$$x = \begin{bmatrix}
2 \space m\\
4 \space m\\
9 \space m/s\\
0.5 \space rad\\
0.6 \space rad/s
\end{bmatrix}$$
