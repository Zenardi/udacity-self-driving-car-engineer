# Finite State Machines

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=NERRPjU08NU)

## Summary

**Finite State Machines for Behavior Planning**
=====================================================

This project introduces the concept of Finite State Machines (FSMs) as a solution to behavior planning in autonomous vehicles. An FSM is a mathematical model that makes decisions based on a finite set of discrete states.

### Key Concepts

* **Finite State Machine**: A system that makes decisions based on a finite set of discrete states.
* **States**: Discrete points in the system's behavior, e.g., S0, S1, S2, S3, and S4.
* **Transitions**: Connections between states, allowing the system to move from one state to another.
* **Self Transition**: A transition back to the same state.
* **Accepting State**: A state that does not transition to any other state (e.g., S4).
* **Transition Function**: A function that determines which state to transition to next based on input.

### Practical Notes

To implement an FSM for behavior planning, you would:

1. Define a set of states representing the possible behaviors (e.g., changing lanes, following lanes, turning).
2. Create transitions between these states, specifying which actions can be taken from each state.
3. Identify accepting states that do not transition to any other state.
4. Implement a transition function to determine which state to move to next based on input.

Note: This is just an introduction to FSMs and behavior planning. In the following lessons, we will explore more advanced topics and provide code examples for implementing FSMs in autonomous vehicles.

## Transcript

In the previous administration the navigator gave various suggestions on what to do next. And the instructions they gave were about things like changing lanes, following lanes, turning and so on. But in fact there really aren't that many types of suggestions you would expect to hear from a navigator. In this lesson we're going to teach an approach to behavior planning that uses something called a Finite State Machine to solve the behavior planning problem. A Finite State Machine makes decisions based on a finite set of discrete states. In this example five. When initialized, a Finite State Machine begins in some start state, let's call it S Zero. Any pair of states within the finite state machine can be connected by one or more transitions. And sometimes there is a transition back to the same state. This is called a Self Transition. Not all transitions are necessarily possible. For example, S four doesn't transition to any other state. In the language of finite state machines this would be called an Accepting State. For non-accepting states that can often be multiple potential successors states. To decide which state to transition to next, a Finite State Machine needs to handle some sort of input and then use a state transition function to decide what state to go next. We'll talk more about transition functions and the states associated with a self driving car in a minute. But first, we want to formalize what a Finite State Machine is, with the help of a simple example.
