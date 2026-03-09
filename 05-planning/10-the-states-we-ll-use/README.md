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

<v English>In planning this lesson, we knew we wanted to focus on highway driving,</v> <v English>but we still debated what states we should use for our finite state machine.</v> <v English>We quickly agreed on three,</v> <v English>since it seemed to us like these were</v> <v English>the bare minimum and that a single lane change wouldn't suffice.</v> <v English>And we also agreed to rule out a lot of states because most of</v> <v English>these can be thought of as various implementations of the keep lane state.</v> <v English>But these last two, prepare lane change</v> <v English>left and prepare lane change right, we were unsure about.</v> <v English>Eventually, we did decide to use these states for these lessons.</v> <v English>So we should probably clarify what we mean by these states.</v> <v English>Let's start by imagining what vehicle behavior would</v> <v English>look like without these two prep states.</v> <v English>First, let me explain how this example will work.</v> <v English>Up here we have a two-lane highway with traffic driving to the right.</v> <v English>This is our self-driving car and other traffic is shown in red.</v> <v English>As you watch this animation,</v> <v English>you should imagine watching from a helicopter which is flying</v> <v English>above the highway at the self-driving car's target speed.</v> <v English>These red trails indicate the relative speed of other vehicles.</v> <v English>In this situation, the vehicles in lane one are moving faster</v> <v English>than we are while the vehicles in lane two are moving slower.</v> <v English>When we only have three states plus a fourth ready state,</v> <v English>the finite state machine looks like this.</v> <v English>We'll assume that as we begin watching we are already in the keep lane state.</v> <v English>Now before we watch what happens to our vehicle when it uses this finite state machine,</v> <v English>let me explain what these states mean.</v> <v English>The lane keep state attempts to stay in</v> <v English>the current lane by staying near the center line for that lane.</v> <v English>So thinking in finite coordinates,</v> <v English>we might just say that target d for the vehicle is whatever the d for the lane is.</v> <v English>And for the s direction,</v> <v English>keep lane state attempts to drive at the vehicle's target speed when that's feasible,</v> <v English>but when it's not, it will try to drive at whatever speed is safest for the lane.</v> <v English>For lane changes the goal is to move from the initial lane to the target lane.</v> <v English>The d behavior is what you might expect to move left or right as appropriate.</v> <v English>So the target d is the d for whatever lane is to</v> <v English>the left or right of the ego's current lane.</v> <v English>For s, the same rules as lane keeping apply.</v> <v English>The vehicle will try to drive at the target speed,</v> <v English>but if that's not feasible,</v> <v English>then it will drive at whatever speed is safe for the initial lane.</v> <v English>Now, let's observe the vehicle's behavior as we move forward in time.</v> <v English>For the first few timesteps,</v> <v English>we see that the ego-vehicle gets closer and closer to vehicle</v> <v English>2.2 while the vehicle in the left lane pas the ego-vehicle.</v> <v English>And during this time the vehicle remains in the lane keep state</v> <v English>since there isn't really enough gap to make a safe lane change.</v> <v English>Note that at this point the ego-vehicle does</v> <v English>begin to slow down even though it doesn't change state.</v> <v English>That's because the lane keep state contains this behavior.</v> <v English>When the target speed is no longer feasible,</v> <v English>it will adjust speed to something safe for the lane.</v> <v English>At this point, the vehicle has decided that the lane change left is the best move.</v> <v English>Now, in the lane change state,</v> <v English>you can see the vehicle has moved left in its lane but hasn't adjusted its speed.</v> <v English>This is consistent with the rules we defined for lane change behavior.</v> <v English>At this point, the vehicle has crossed the dotted line,</v> <v English>so its current lane is the left lane.</v> <v English>Now it wants to transition back to the lane keep state to stay in this lane,</v> <v English>and when it does that,</v> <v English>it immediately starts accelerating so it can get to a speed that's safe for this lane.</v> <v English>Right now it is moving at the same speed as other traffic in the left lane,</v> <v English>which it can continue doing until it passes the vehicles on the right.</v> <v English>Even though this worked, there were some problems.</v> <v English>First, even when it was clear that there was</v> <v English>a gap we could probably move into on the left,</v> <v English>we had no way to tell the vehicle to try to get alongside that gap.</v> <v English>We had to just wait for the gap to get close to us.</v> <v English>Second, this lane change wasn't all that safe.</v> <v English>Ideally, we would have been able to get closer to</v> <v English>the left lane speed before actually making the lane change.</v> <v English>Third, it isn't clear when we would have turned on the turn signal in this scenario.</v> <v English>The turn signal is the responsibility of the behavior team and</v> <v English>ideally we would like to turn it on</v> <v English>a few seconds before we actually start changing lanes.</v> <v English>Using this finite state machine,</v> <v English>it would have been hard to do that.</v> <v English>To address that problem,</v> <v English>we can introduce a prepare for lane change state.</v> <v English>In this state we do whatever we can to prepare for a lane change left or right,</v> <v English>which means in the d directions we still can</v> <v English>stay in this current lane but in the s direction we</v> <v English>tried to match the position and speed of some gap in one of the adjacent lanes.</v> <v English>This is also when we would turn on the appropriate signal.</v> <v English>We also changed the finite state machine to look like this.</v> <v English>And note that the only way to change lanes is to first prepare for a lane change.</v> <v English>Let's see what that would look like.</v> <v English>At the first timestep we can decide to prepare</v> <v English>for a lane change by tracking this gap over here,</v> <v English>which allows us to immediately start slowing down.</v> <v English>At this point, the car may begin slowly increasing</v> <v English>speed to get closer to the left lane speed,</v> <v English>and at this point the vehicle has reached the same speed as the left lane traffic</v> <v English>and is in a good position to execute a lane change, which it begins here.</v> <v English>From here on, everything looks pretty similar to before.</v> <v English>With these added states,</v> <v English>we're now able to perform a lane change more safely and efficiently.</v>
