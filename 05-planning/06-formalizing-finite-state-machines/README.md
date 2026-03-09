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

<v English>Let's consider a simple vending machine where everything costs 20 cents.</v> <v English>And let's say that this vending machine only takes</v> <v English>nickels and dimes but nothing larger or smaller.</v> <v English>Then we can model the state of</v> <v English>this vending machine by the amount of money that's been deposited.</v> <v English>The start state would be zero cents.</v> <v English>And from this date there are two things that can happen.</v> <v English>We could put in a nickel,</v> <v English>which would make the state five cents or we</v> <v English>could put in a dime to take the state to 10 cents.</v> <v English>The rest of the transitions are fairly straightforward until we think about</v> <v English>what to do if we are in the 15 cent state and someone puts in a dime.</v> <v English>We could just count that as 20.</v> <v English>But let's say that this machine requires exact change so that</v> <v English>a dime would just fall through and come</v> <v English>out of the little tray at the bottom of the machine.</v> <v English>As you can see, finite state machines are pretty straightforward conceptually.</v> <v English>So why talk about them?</v> <v English>They have their strengths and weaknesses.</v> <v English>Let's start with our strengths.</v> <v English>First, finite state machines are very easy to reason about.</v> <v English>They are basically self-documenting because they map</v> <v English>the logical state of a system directly to the physical state.</v> <v English>When a nickel goes into the vending machine</v> <v English>the state changes to the state that is five cents bigger than the current one.</v> <v English>Next, they are maintainable.</v> <v English>If we wanted to tweak this machine so that everything costs</v> <v English>a quarter it would be pretty trivial to just add one more state.</v> <v English>Which brings us to the weaknesses of the finite state machine.</v> <v English>The primary one being that they are easily abused.</v> <v English>If they aren't designed well to begin with or if the problem</v> <v English>changes you can easily find yourself saying things like,</v> <v English>I hadn't considered that.</v> <v English>Let's just add another state and this can lead to some sloppy code and sloppy logic.</v> <v English>Which in practice means that finite state machines can be</v> <v English>very difficult to maintain as the states base gets bigger.</v>
