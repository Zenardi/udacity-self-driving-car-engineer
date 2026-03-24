# The States We'll Use

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=QXU6ptbxfyo)

## Summary

**Highway Driving Finite State Machine**
=====================================

This project focuses on implementing a finite state machine for highway driving, specifically handling lane changes. The main goal is to create a safe and efficient system that can adapt to changing traffic conditions.

**Key Concepts**
---------------

* **Finite State Machine (FSM)**: A mathematical model used to describe the behavior of a system by dividing it into distinct states.
* **Lane Keep State**: Attempts to stay in the current lane by maintaining a safe distance from the center line and adjusting speed as necessary.
* **Lane Change State**: Moves the vehicle from the initial lane to the target lane, with the goal of minimizing disruptions to traffic flow.
* **Prepare for Lane Change State**: Prepares the vehicle for an upcoming lane change by tracking a gap in an adjacent lane and adjusting speed accordingly.
* **Target Speed**: The desired speed of the vehicle, which may be adjusted based on factors such as traffic conditions and road safety.

**Practical Notes**
------------------

To implement this finite state machine, you can follow these steps:

1. Define the states and transitions between them using a programming language or a visual modeling tool.
2. Implement the lane keep state by adjusting speed and maintaining a safe distance from the center line.
3. Implement the lane change state by moving the vehicle to the target lane while minimizing disruptions to traffic flow.
4. Introduce the prepare for lane change state to improve safety and efficiency of lane changes.

Example Code
```python
class FiniteStateMachine:
    def __init__(self):
        self.states = {
            'keep_lane': LaneKeepState(),
            'lane_change': LaneChangeState(),
            'prepare_lane_change_left': PrepareLaneChangeLeftState(),
            'prepare_lane_change_right': PrepareLaneChangeRightState()
        }

    def transition(self, current_state, next_state):
        # Update the state machine based on the current and next states
        pass

class LaneKeepState:
    def __init__(self):
        self.target_speed = 60  # mph

    def update_speed(self, vehicle_speed):
        if vehicle_speed > self.target_speed:
            return self.target_speed
        else:
            return vehicle_speed

# ... (rest of the code)
```
Note that this is a simplified example and may require modifications to suit your specific use case.

## Transcript

In planning this lesson, we knew we wanted to focus on highway driving, but we still debated what states we should use for our finite state machine. We quickly agreed on three, since it seemed to us like these were the bare minimum and that a single lane change wouldn't suffice. And we also agreed to rule out a lot of states because most of these can be thought of as various implementations of the keep lane state. But these last two, prepare lane change left and prepare lane change right, we were unsure about. Eventually, we did decide to use these states for these lessons. So we should probably clarify what we mean by these states. Let's start by imagining what vehicle behavior would look like without these two prep states. First, let me explain how this example will work. Up here we have a two-lane highway with traffic driving to the right. This is our self-driving car and other traffic is shown in red. As you watch this animation, you should imagine watching from a helicopter which is flying above the highway at the self-driving car's target speed. These red trails indicate the relative speed of other vehicles. In this situation, the vehicles in lane one are moving faster than we are while the vehicles in lane two are moving slower. When we only have three states plus a fourth ready state, the finite state machine looks like this. We'll assume that as we begin watching we are already in the keep lane state. Now before we watch what happens to our vehicle when it uses this finite state machine, let me explain what these states mean. The lane keep state attempts to stay in the current lane by staying near the center line for that lane. So thinking in finite coordinates, we might just say that target d for the vehicle is whatever the d for the lane is. And for the s direction, keep lane state attempts to drive at the vehicle's target speed when that's feasible, but when it's not, it will try to drive at whatever speed is safest for the lane. For lane changes the goal is to move from the initial lane to the target lane. The d behavior is what you might expect to move left or right as appropriate. So the target d is the d for whatever lane is to the left or right of the ego's current lane. For s, the same rules as lane keeping apply. The vehicle will try to drive at the target speed, but if that's not feasible, then it will drive at whatever speed is safe for the initial lane. Now, let's observe the vehicle's behavior as we move forward in time. For the first few timesteps, we see that the ego-vehicle gets closer and closer to vehicle 2.2 while the vehicle in the left lane pas the ego-vehicle. And during this time the vehicle remains in the lane keep state since there isn't really enough gap to make a safe lane change. Note that at this point the ego-vehicle does begin to slow down even though it doesn't change state. That's because the lane keep state contains this behavior. When the target speed is no longer feasible, it will adjust speed to something safe for the lane. At this point, the vehicle has decided that the lane change left is the best move. Now, in the lane change state, you can see the vehicle has moved left in its lane but hasn't adjusted its speed. This is consistent with the rules we defined for lane change behavior. At this point, the vehicle has crossed the dotted line, so its current lane is the left lane. Now it wants to transition back to the lane keep state to stay in this lane, and when it does that, it immediately starts accelerating so it can get to a speed that's safe for this lane. Right now it is moving at the same speed as other traffic in the left lane, which it can continue doing until it passes the vehicles on the right. Even though this worked, there were some problems. First, even when it was clear that there was a gap we could probably move into on the left, we had no way to tell the vehicle to try to get alongside that gap. We had to just wait for the gap to get close to us. Second, this lane change wasn't all that safe. Ideally, we would have been able to get closer to the left lane speed before actually making the lane change. Third, it isn't clear when we would have turned on the turn signal in this scenario. The turn signal is the responsibility of the behavior team and ideally we would like to turn it on a few seconds before we actually start changing lanes. Using this finite state machine, it would have been hard to do that. To address that problem, we can introduce a prepare for lane change state. In this state we do whatever we can to prepare for a lane change left or right, which means in the d directions we still can stay in this current lane but in the s direction we tried to match the position and speed of some gap in one of the adjacent lanes. This is also when we would turn on the appropriate signal. We also changed the finite state machine to look like this. And note that the only way to change lanes is to first prepare for a lane change. Let's see what that would look like. At the first timestep we can decide to prepare for a lane change by tracking this gap over here, which allows us to immediately start slowing down. At this point, the car may begin slowly increasing speed to get closer to the left lane speed, and at this point the vehicle has reached the same speed as the left lane traffic and is in a good position to execute a lane change, which it begins here. From here on, everything looks pretty similar to before. With these added states, we're now able to perform a lane change more safely and efficiently.