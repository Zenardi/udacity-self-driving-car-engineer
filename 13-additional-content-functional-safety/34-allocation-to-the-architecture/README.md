# Allocation to the Architecture

> Part of: **Functional Safety: Functional Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=cDkQLZ3PJqM)

## Summary

**Lane Departure Warning System: Functional Safety Requirements Allocation**
===========================================================

This README file summarizes the key concepts and practical steps involved in allocating functional safety requirements to a lane departure warning system's architecture.

### Key Concepts

* **Functional Safety Requirements**: Two requirements were introduced:
	+ Limiting steering wheel vibration frequency
	+ Limiting steering wheel amplitude
* **Subsystem Allocation**: The electronic power steering ECU is responsible for limiting the vibration torque and amplitude.
* **Simplified Solution**: Only requiring the power steering to limit the vibration, regardless of the camera's request.
* **Allocation Table**: A table can be used to visualize the allocation of requirements to subsystems.

### Practical Notes

* When allocating functional safety requirements, consider reducing complexity by assigning a single subsystem to handle multiple requirements.
* Use clear and explicit language in functional safety requirements, specifying which subsystem is responsible for limiting specific parameters (e.g., torque amplitude or frequency).
* In real-world scenarios, functional safety requirements may be allocated to multiple subsystems.

**Example Functional Safety Requirements**

| Requirement | Description |
| --- | --- |
| 1. | The electronic power steering ECU shall ensure that the lane departure warning oscillating torque amplitude is below max torque amplitude. |
| 2. | The electronic power steering ECU shall ensure that the lane departure warning oscillating torque frequency is below max torque frequency. |

Note: This example uses a simplified scenario to illustrate the concept of allocating functional safety requirements to subsystems. In real-world applications, you may encounter more complex scenarios with multiple subsystems involved.

## Transcript

<v English>Our lane departure warning system now has two functional safety requirements.</v> <v English>One requirement limits the steering wheel vibration frequency,</v> <v English>and the other requirement limits the steering wheel amplitude.</v> <v English>Now we have to figure out which part of the lane keeping the item will be</v> <v English>responsible for limiting the vibration torque and the amplitude.</v> <v English>The lane assistance item has three subsystems,</v> <v English>the camera, the display,</v> <v English>and the electronic power steering.</v> <v English>Let's take a look at the architectural diagram.</v> <v English>Logically, we could say that both the camera subsystem and</v> <v English>electronic steering subsystem could limit the frequency and the amplitude.</v> <v English>For instance, we could make a requirement that the camera subsystem</v> <v English>can only request a vibrational torque below a maximal threshold.</v> <v English>And we could also make a requirement that the power steering system</v> <v English>can only output a vibrational torque below the same limit.</v> <v English>But we want to reduce the complexity whenever possible.</v> <v English>The simpler solution is to only require</v> <v English>the power steering to limit the vibration no matter what the camera ask for.</v> <v English>Now the only relevant subsystem</v> <v English>from a functional safety standpoint is the power steering.</v> <v English>For the lane departure warning,</v> <v English>the allocation of the requirements to the architecture is straightforward.</v> <v English>Only an electronic power steering ECU is involved with limiting the vibration warning.</v> <v English>The two functional safety requirements are allocated to the power steering ECU.</v> <v English>We will also slightly change the wording in the functional safety requirements,</v> <v English>whereas before we said the lane keeping item had to limit the vibrational torque,</v> <v English>now we'll be more explicit and say the power steering, ECU,</v> <v English>will limit the vibrational torque.</v> <v English>Here are the final safety requirements: Functional safety requirement 1.</v> <v English>The electronic power steering ECU shall ensure that</v> <v English>the lane departure warning oscillating torque amplitude is below max torque amplitude.</v> <v English>Functional safety requirement 2.</v> <v English>The electronic power steering ECU shall ensure that</v> <v English>the lane departure warning oscillating torque frequency is below max torque frequency.</v> <v English>We can put the results in a table.</v> <v English>Note that we are using a simplified example.</v> <v English>Oftentimes, you will have</v> <v English>a functional safety requirement that gets allocated to multiple subsystems.</v>

## Additional Content

### Review
Let's reiterate what has been done so far. The hazard analysis and risk assessment led to two safety goals:
1. The oscillating steering torque from the lane departure warning function shall be limited
2. The lane keeping assistance function shall be time limited, and the additional steering torque shall end after a given time interval so that the driver cannot misuse the system for autonomous driving.

You then derived two functional safety requirements from safety goal number 1:
1. The lane keeping item shall ensure that the lane departure oscillating torque amplitude is below Max_Torque_Amplitude
2. The lane keeping item shall ensure that the lane departure oscillating torque frequency is below Max_Torque_Frequency

For safety goal number 2, you derived a functional safety requirement that "the electronic power steering ECU shall ensure that the lane keeping assistance torque is applied for only Max_Duration". 

Your next step will be to figure out where these requirements belong in the system architecture.

### Allocation of Requirements to the System Architecture
### Quiz
