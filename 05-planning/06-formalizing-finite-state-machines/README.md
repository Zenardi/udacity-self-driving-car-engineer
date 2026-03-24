# Formalizing Finite State Machines

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=sEZn3iZgOaI)

## Summary

**Finite State Machines: A Simple Vending Machine Example**
===========================================================

This project demonstrates a simple vending machine modeled using a finite state machine. The vending machine takes nickels and dimes, but only accepts exact change.

### Key Concepts

* **Finite State Machine**: A mathematical model that consists of a set of states and transitions between them.
* **States**: Represented as the amount of money deposited into the vending machine (0 cents, 5 cents, 10 cents, etc.).
* **Transitions**: Define how the state changes when a nickel or dime is inserted (e.g., from 0 cents to 5 cents with a nickel).
* **Exact Change**: A requirement that the vending machine only accepts money that exactly matches the cost of an item.
* **Strengths and Weaknesses**: Finite state machines are easy to reason about, self-documenting, and maintainable, but can be easily abused if not designed well.

### Practical Notes

* To implement a finite state machine in code, you would need to define the states and transitions between them using a programming language.
* In this example, the vending machine's behavior is defined by a simple set of rules (e.g., insert nickel -> 5 cents, insert dime -> 10 cents).
* The concept of exact change can be implemented as a special case in the state transition logic.

## Transcript

Let's consider a simple vending machine where everything costs 20 cents. And let's say that this vending machine only takes nickels and dimes but nothing larger or smaller. Then we can model the state of this vending machine by the amount of money that's been deposited. The start state would be zero cents. And from this date there are two things that can happen. We could put in a nickel, which would make the state five cents or we could put in a dime to take the state to 10 cents. The rest of the transitions are fairly straightforward until we think about what to do if we are in the 15 cent state and someone puts in a dime. We could just count that as 20. But let's say that this machine requires exact change so that a dime would just fall through and come out of the little tray at the bottom of the machine. As you can see, finite state machines are pretty straightforward conceptually. So why talk about them? They have their strengths and weaknesses. Let's start with our strengths. First, finite state machines are very easy to reason about. They are basically self-documenting because they map the logical state of a system directly to the physical state. When a nickel goes into the vending machine the state changes to the state that is five cents bigger than the current one. Next, they are maintainable. If we wanted to tweak this machine so that everything costs a quarter it would be pretty trivial to just add one more state. Which brings us to the weaknesses of the finite state machine. The primary one being that they are easily abused. If they aren't designed well to begin with or if the problem changes you can easily find yourself saying things like, I hadn't considered that. Let's just add another state and this can lead to some sloppy code and sloppy logic. Which in practice means that finite state machines can be very difficult to maintain as the states base gets bigger.
