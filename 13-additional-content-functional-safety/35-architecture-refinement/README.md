# Architecture Refinement

> Part of: **Functional Safety: Functional Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=SK85D4cvwXo)

## Summary

**System Architecture Refinement**
=====================================

This README file summarizes the key concepts and practical steps introduced in the Udacity lesson on refining system architecture.

**Key Concepts**
---------------

* **Subsystems**: The three main subsystems discussed are:
	+ Car display subsystem
	+ Camera subsystem
	+ Electronic power steering subsystem
* **Software Blocks**: Each subsystem requires additional software blocks to implement specific functionality, such as:
	+ Lane keeping and departure warning systems
	+ Torque request processing
	+ Steering wheel motor control
* **Functional Safety Requirements**: The lesson emphasizes the importance of deriving functional safety requirements and allocating them to the architectural diagram.
* **Torque Request Processing**: The electronic power steering subsystem requires three software blocks to process torque requests, including:
	+ Sensing driver input
	+ Receiving vibrational torque request from camera subsystem
	+ Combining torque requests for motor output

**Practical Notes**
------------------

* When refining system architecture, it's essential to identify and allocate functional safety requirements to specific subsystems.
* The car display subsystem requires additional software blocks to control lights indicating lane keeping and departure warning status.
* The camera subsystem needs two software blocks: one for lane sensing and another for sending torque requests to the electronic power steering subsystem.
* The electronic power steering subsystem requires three software blocks to process torque requests, including limiting amplitude and frequency.

## Transcript

<v English>Now that we have a better sense of what the system needs to do,</v> <v English>we are going to draw all the extra functionality on the architectural diagram.</v> <v English>Here is our original system architecture.</v> <v English>Let's add more details to the three subsystems.</v> <v English>The car display subsystem will need extra software blocks.</v> <v English>One controls a light that tells the driver if the lane keeping item is on or off.</v> <v English>A second will control a light telling</v> <v English>the driver that the lane departure warning is activated.</v> <v English>The camera subsystem needs two software blocks, as well.</v> <v English>One for lane sensing and a separate block to send</v> <v English>a torque request to the electronic power steering subsystem.</v> <v English>The electronic power steering subsystem will need three software blocks.</v> <v English>The first will sense how much the driver is turning the steering wheel.</v> <v English>A second software block will receive</v> <v English>the vibrational torque request from the camera subsystem.</v> <v English>This is where we will limit the amplitude and frequency to be</v> <v English>low max torque amplitude and max torque frequency.</v> <v English>The third block will add these torque requests together to</v> <v English>output a final torque to the motor that moves the steering wheel.</v> <v English>We have now derived functional safety requirements and</v> <v English>allocated those requirements to the architectural diagram.</v> <v English>In the next step, we will label the architectural diagram with a.</v>

## Additional Content

### Architecture Refinement
### Lane Keeping Assistance Function

What about the lane keeping assistance function? For now, we can also assume that the lane keeping assistance function will be part of the lane keeping software block that we already added to the system architecture.

Not all requirements, however, need software blocks. For example, requirements can also be solved with mechanical systems. Oftentimes, it is easier to implement a mechanical solution rather than using software.
