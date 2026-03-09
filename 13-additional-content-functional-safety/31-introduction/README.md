# Introduction

> Part of: **Functional Safety: Functional Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=srUVh4mBvws)

## Summary

**Functional Safety Planning**
=====================================

This summary provides an overview of the key concepts and practical steps involved in planning for functional safety, a critical aspect of avoiding accidents by reducing risk to acceptable levels.

### Key Concepts

* **Functional Safety Requirements**: High-level goals that need to be refined into specific requirements to ensure safe operation.
* **Item Architecture**: A detailed design of the item's subsystems and elements, used to identify potential risks and allocate functional safety requirements.
* **Risk Reduction**: The process of identifying and mitigating high-risk areas in an item's architecture to prevent accidents.
* **Functional Safety Concept Document**: A document that outlines all relevant information for ensuring functional safety, including risk reduction strategies and allocated responsibilities.

### Practical Notes

To implement functional safety planning, follow these steps:

1. Identify potential risks by analyzing the item's architectural design.
2. Refine high-level goals into specific functional safety requirements.
3. Allocate each requirement to its appropriate place in the item architecture.
4. Document all relevant information in a functional safety concept document.

Note: This summary focuses on the key concepts and practical steps introduced in the lesson, providing a concise overview of the topic.

## Transcript

<v English>Let's emphasize again the ultimate goal of functional safety,</v> <v English>avoiding accidents by reducing risk to acceptable levels.</v> <v English>First let's figure out what subsystems actually</v> <v English>contain high levels of risk and what's needed to prevent accidents.</v> <v English>Looking at the items architectural design,</v> <v English>you'll figure out which subsystems and elements can be used to meet safety goals.</v> <v English>You'll need to further refine these high level goals</v> <v English>into what we call functional safety requirements.</v> <v English>And then you'll allocate</v> <v English>each functional safety requirement to its appropriate place in the item architecture.</v> <v English>We take all of this information and put it into</v> <v English>a document called the functional safety concept.</v>

## Additional Content

You might start recognizing a pattern as we continue to travel down the levels of the V model; you will keep identifying new requirements and then allocate those requirements to different parts of the item architecture.

### Attributes of a Functional Safety Requirement

First you refine the safety goals in what are called functional safety requirements. Remember that requirements define what the vehicle needs to do; in other words, requirements define the vehicle's functions..

You need to allocate these safety requirements to the relevant parts of the system diagram. Allocation means defining which part of the system architecture will implement each requirement. This could involve expanding the system architecture with new element blocks.

You will then refine the system architecture to handle the new requirements.

Functional safety requirements also have a few attributes that need to be specified in the functional safety concept:
- the ASIL level
- the fault tolerant time interval, which measures how quickly a system needs to react to a hazardous situation
- And the safe state, which discusses what a system looks like after it has avoided an accident

We are also going to discuss verification and validation, which is how you prove that a system actually meets your requirements.

All of this information will go into the functional safety concept.
### Scope of the Functional Safety Concept

While this lesson teaches how to create a functional safety concept, the next lesson will focus on a document called the technical safety concept. The functional safety concept and technical safety concept are similar in that you will need to identify new requirements and allocate these requirements to system diagrams. 

The difference is that the functional safety concept is looking at the item from a higher level. In the technical safety concept, you will start thinking about sensors, control units and actuators. Technical safety requirements are general hardware and software requirements but still without getting into specific details. For example, in the technical safety concept you might realize that you need to add more ECUs, sensors, and extra software blocks to your system. 

You will see in this lesson that the functional safety concept does not go into technical details. The functional safety concept looks at the general functionality of the item; the technical safety concept looks at the technical implementation of the item. In practice, developing these two documents is an iterative process where new functional requirements could lead to new technical requirements which could lead back to new functional requirements.
