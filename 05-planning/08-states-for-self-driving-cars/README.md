# States for Self Driving Cars

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=zoN0-IPe0I4)

## Summary

**Finite State Machines for Vehicle Behavior**

This project involves designing a finite state machine (FSM) to model vehicle behavior on a highway. The goal is to identify the key states that a vehicle can be in while driving on a highway.

### Key Concepts

* **Finite State Machine**: A mathematical system that can be in one of a finite number of states.
* **States**: Specific conditions or situations that a vehicle can be in, such as "driving normally", "changing lanes to the left", or "slowing down".
* **Transitions**: The changes between different states, such as from "driving normally" to "changing lanes to the left".
* **Determining States**: Identifying the necessary states to represent all possible physical conditions of a vehicle on a highway.

### Practical Notes

The lesson demonstrates how to brainstorm and identify potential states for a finite state machine. The instructor uses a simple example of a vending machine and then applies it to a more complex scenario, modeling car driving on a highway.

Some key takeaways from the practical steps include:

* Enumerating all possible states is not always necessary; sometimes it's better to start with a small set of states and add more as needed.
* The number of states should be balanced between maintainability (keeping the state space small) and accuracy (representing all physical states).
* Different scenarios, such as having multiple cars on the road or changing lanes, may require different sets of states.

The instructor encourages the student to think critically about what states are necessary for a vehicle to behave correctly on a highway. The exercise involves identifying and selecting relevant states from a list, demonstrating how to apply the concepts learned in the lesson to a real-world problem.

## Transcript

When we're thinking about a simple vending machine it's easy to enumerate the states. Now let's consider the states we may want to model for car driving on a highway. Benny, let's just throw out all the ideas we can come up with and then prune the list afterwards so we can show how we might think about coming up with a finite state machine from scratch. Okay, let's keep it simple first. What happens if we are the only car on the road? I guess we would need a state for normal staying in your lane driving. If we are changing lanes, we want a state to represent that. Or maybe two states since changing lanes to the left is different than to the right. Okay. I guess. What changes if there's a vehicle in front of us? Well we might want to stay behind it, so we should have a state for that or we might want to pass it. I suppose, but isn't pass just a lane change to the left and then a lane change to the right? Do we really need in your state for that? Hey, we're brainstorming no bad ideas. Okay, fine. Well, what changes if we had more cars? I could imagine in this situation you might want to slow down so that you could merge into this gap here and then pass this car if it's going slow. We should really have a slow downstate which I guess means we will also need a speed upstate. We should probably add a stop state in case there is some emergency situation. I guess we could do all of that at once by having a keep target speed state. Well I don't know. Shouldn't speed just be dictated by the lane you're driving in and the speed limit? What if we just add a prepare lane change state to represent when the ego vehicle is trying to go next to an empty gap in traffic before a lane change? Yeah, that could work but we should probably have a prepare lane change left and to prepare a lane change right, since those really are different maneuvers. Oh, and we could also turn on the turn signals down. Good point. The truth is there isn't a single correct set of states to choose from. On one hand we want to keep our state space as small as possible for maintainability reasons, but on the other hand we want to make sure we have enough logical States to actually represent all the physical states that we care about. As you've seen in the discussion we've just had it's not easy to find the perfect set of states for this scenario. Why don't you think for a minute about what states you would want to use to represent vehicle behavior on a highway. Check the boxes next to each state that you'd keep and write any additional ones in the empty boxes on the left.
