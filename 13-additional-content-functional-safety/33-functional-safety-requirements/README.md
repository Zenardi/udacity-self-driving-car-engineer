# Functional Safety Requirements

> Part of: **Functional Safety: Functional Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=9z5YqMYH7mY)

## Summary

**Lane Departure Warning System Functional Safety Requirements**
===========================================================

This project focuses on deriving functional safety requirements from a given safety goal for a lane departure warning system. The goal is to limit the oscillating steering torque caused by the system's malfunction, which was too strong.

### Key Concepts
* **Functional Safety Requirements**: Derived from safety goals to ensure the safe operation of a system.
* **Safety Goal**: A high-level statement that defines what needs to be achieved for the system to operate safely.
* **Malfunction**: An error or failure in the system's behavior, which led to the definition of a safety goal.
* **Lane Departure Warning System**: A system designed to prevent vehicles from drifting out of their lane.
* **Torque Amplitude and Frequency**: Measures used to describe the oscillating steering torque caused by the system.

### Practical Notes
To implement this in practice:

1. Identify the malfunction or error that led to a safety goal.
2. Derive functional safety requirements from the safety goal, as shown in this example:
	* Functional Safety Requirement 1: Ensure the lane keeping items limit the oscillating torque amplitude below the maximum allowed value.
	* Functional Safety Requirement 2: Ensure the lane keeping items limit the oscillating torque frequency below the maximum allowed value.
3. Use these requirements to guide the design and development of the system, ensuring that it meets the safety goals defined.

## Transcript

<v English>Going back to the lane departure warning example.</v> <v English>Let's derive a couple of functional safety requirements from our first safety goal.</v> <v English>Our malfunction was that the steering wheel warning vibration was too strong.</v> <v English>The malfunction led to the safety goal that the oscillating</v> <v English>steering torque of a lane departure warning function shall be limited.</v> <v English>For the lane departure warning system,</v> <v English>it makes sense to define</v> <v English>a maximum allowed torque amplitude and a maximum allowed frequency.</v> <v English>From the safety goal,</v> <v English>we will define two functional safety requirements for the lane warning departure system.</v> <v English>Functional safety requirement one.</v> <v English>The lane keeping items shall ensure that the lane departure</v> <v English>oscillating torque amplitude is below max torque amplitude.</v> <v English>Functional safety requirement two.</v> <v English>The lane keeping item shall ensure that</v> <v English>the lane departure oscillating torque frequency is below max torque frequency.</v> <v English>Notice again that we use the term shell,</v> <v English>because these are requirements.</v> <v English>So what have we done so far?</v> <v English>We started with a safety goal requiring the vibration to be limited.</v> <v English>We looked at the item architecture and came up with</v> <v English>two new requirements that would meet our safety goal.</v> <v English>We then figured out that the lane assistance item needed to</v> <v English>limit the vibration amplitude and vibration frequency.</v>

## Additional Content

### Lane Keeping Assistance Functional Safety Requirement


For the lane keeping assistance function, the malfunction was that there was no time limit, and the driver could treat the system as if it were designed for autonomous driving. We determined a safety goal saying the "lane keeping assistance function shall be time limited and the additional steering torque shall end after a given timer interval so that the driver can not misuse the system for autonomous driving". In other words, the lane assistance system should stop applying extra torque after a certain amount of time.

In this example as well, we can still meet the safety requirement by merely adding functionality to the power steering ECU. For the lane keeping assistance function, we'll define a new requirement that "the electronic power steering ECU shall ensure that the lane keeping assistance torque is applied for only Max_Duration".

### Safety Analysis Methods

We have used some basic logic to derive functional safety requirements from the safety goals. 

There are also more formal methods for deriving functional safety requirements. These methods are not only used in functional safety but also in general systems engineering. In functional safety, these methods can be used in a variety of situations:
* Deriving safety requirements
* Identifying conditions and causes that could lead to requirement violations
* Identifying other hazards not identified in the Hazard Analysis and Risk Assessment

Different companies might use different methods including: 

* [Failure Modes and Effects Analysis (FMEA)](https://en.wikipedia.org/wiki/Failure_mode_and_effects_analysis)

* [Hazard and Operability Study (HAZOPS)](https://en.wikipedia.org/wiki/Hazard_and_operability_study)  Note that HAZOP differs from the other items here in that it is a technique that used to derive hazards similar to the methods used in ISO 26262 HARA .

* [Failure Modes Effects and Diagnostic Analysis FMEDA](https://en.wikipedia.org/wiki/Failure_modes,_effects,_and_diagnostic_analysis)

* [Fault Tree Analysis (FTA)](https://en.wikipedia.org/wiki/Fault_tree_analysis)

* [Reliability Block Diagram](https://en.wikipedia.org/wiki/Reliability_block_diagram)

* [ETA](https://en.wikipedia.org/wiki/Event_tree_analysis)
