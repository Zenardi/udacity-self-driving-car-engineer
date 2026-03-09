# Inputs to Transition Functions

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=8jStt2d_SYc)

## Summary

**Finite-State Machine Transition Function**

A finite-state machine's behavior depends on how its states are chosen and how they transition from one to another. This lesson focuses on determining what inputs a transition function needs to process these transitions.

### Key Concepts

* **Transition functions**: These are the rules that govern how a finite-state machine moves from one state to another.
* **Inputs for transition functions**: The data required by a transition function to determine the next state of a finite-state machine.
* **State transition**: The process of moving from one state to another in a finite-state machine.

### Practical Notes

When implementing a finite-state machine, it's essential to identify all the necessary inputs for the transition function. For example, in a self-driving car, this might include data such as sensor readings, GPS coordinates, and weather conditions. However, the previous state itself should not be passed into the transition function.

```python
# Example of passing required inputs to a transition function
def transition_function(current_state, input_data):
    # Process input data to determine next state
    return next_state

# Example usage:
current_state = "DRIVING"
input_data = {"speed": 60, "weather": "SUNNY"}
next_state = transition_function(current_state, input_data)
```

## Transcript

<v English>You just saw how the states we choose to use can impact the behavior of the vehicle.</v> <v English>But deciding how those states transition and what inputs</v> <v English>the transition functions use is crucial to</v> <v English>the actual implementation of a finite-state machine.</v> <v English>For the example with the vending machine,</v> <v English>the only input was the coin.</v> <v English>The self-driving car is more complicated.</v> <v English>So the question is,</v> <v English>what data will we need to pass into our transition function as input.</v> <v English>Check all that apply.</v>

<v English>The answer is that we have to pass all of the data</v> <v English>into the transition function except for the previous state.</v>
