# Warning and Degradation Concept

> Part of: **Functional Safety: Functional Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=khNhy3IwKa0)

## Summary

**Functional Safety Requirements and Warning Systems**
=====================================================

This lesson covers the essential aspects of functional safety requirements, including warning systems and safe states. It emphasizes the importance of informing drivers about system malfunctions and transitioning to a lower risk state.

### Key Concepts

* **Safe State**: A system state with an acceptable risk level that is achieved when a malfunction occurs.
* **Warning Lights**: Visual indicators on the driver dashboard that alert the driver to potential issues, such as a vibrational torque request beyond the allowed maximum.
* **Driver Alerting**: The process of informing drivers about system malfunctions and reduced functionality through warning lights, messages, or other means.
* **Degradation Concept**: A concept that outlines how the vehicle will transition to and recover from a safe state when system functionality is reduced or turned off.

### Practical Notes

When designing a vehicle's safety features, it's crucial to consider both the warning systems and the degradation concept. This includes:

* Displaying clear warnings on the driver dashboard for specific malfunctions (e.g., lane assistance item malfunction).
* Implementing a safe state by turning off critical functions when a safety requirement is violated.
* Providing information in the car manual about system limitations, such as the lane keeping assistance function not being suitable for autonomous driving.

Example code or formulas are not applicable to this lesson. However, the concepts discussed can be applied to various vehicle systems and software development projects that require attention to functional safety requirements.

## Transcript

<v English>For each functional safety requirement,</v> <v English>we need to discuss how the driver will be warned of the malfunction.</v> <v English>For the lane assistance item malfunctions,</v> <v English>we will display a warning on the driver dashboard.</v> <v English>If the steering wheel ECU receives</v> <v English>a vibrational torque request beyond the allowed maximum,</v> <v English>a warning light will turn on.</v> <v English>Here is an updated system diagram taking into account the warning lights.</v> <v English>Note that we have added a connection from</v> <v English>the power steering ECU to the driver display subsystem.</v> <v English>We also need to describe what the vehicle system will do after a malfunction occurs.</v> <v English>When a malfunction occurs,</v> <v English>the system needs to go to a state with a lower acceptable risk level.</v> <v English>This lower risk level is called a safe state.</v> <v English>We have already said that both the lane departure warning function and the lane</v> <v English>keeping the system function will turn off when a safety requirement is violated.</v> <v English>Turning a system off can generally be</v> <v English>considered a safe state with acceptable risk levels.</v> <v English>A warning and degradation concept will include how</v> <v English>the driver will be alerted when the system has reduced functionality,</v> <v English>or is turned off completely,</v> <v English>and how the vehicle will transition to and recover from the safe state.</v> <v English>The car manual should include information from the warning a degradation concept as well.</v> <v English>For the lane keeping assistance function,</v> <v English>the manual would probably include a warning that</v> <v English>the functionality is not meant for autonomous driving,</v> <v English>and the driver maintains responsibility for the safe operation of.</v>

## Additional Content

### Warning and Degradation Concept
### Summary of Warning and Degradation Concept

In functional safety, "concept" is synonymous with "document". So the warning and degradation concept would be a document that discusses:
*  how the driver will be warned of a malfunction
* what the system will do to "degrade" the functionality i.e. take the system to a safe state and also recover from a safe state.

For the lane assistance item, we discussed that the driver will see a warning light on the dashboard when the system malfunctions. 

The lane departure warning and lane keeping assistance functionality will degrade by turning the system off. In other words, the torque request from the lane keeping assistance will be set to zero.


### Gradual Degradation versus Turning a System Off

Turning off a system entirely is not the only option, however. Some systems can provide limited functionality and "degrade" to different levels depending how bad the malfunction is. A car engine control system is one example. If one sensor fails, the engine control system might reduce the torque output of the motor so that the vehicle can still be driven but at a lower speed.

A lane departure warning system is not critical for driving a vehicle. So if the system has a malfunction, we can shut the system down; on the other hand, a functioning motor is necessary for driving a vehicle. Degrading the motor system to a safer, but functioning, state would help the driver avoid getting stranded. 

### Warning and Degradation Concept in the Final Project


In the [final project template folder](https://github.com/udacity/CarND-Functional-Safety-Project/tree/master/Template_Files), there is a functional safety concept template file. 

Near the end of the file, you will see an empty data table with the following headers:

ID, Degradation Mode, Trigger for Degradation Mode, Safe State invoked?, Driver Warning

You will be responsible for filling out this table. Degradation mode describes how the vehicle will be taken to a safe state when there is a malfunction. For the lane departure warning function, the degradation mode is to turn off the functionality. For the lane keeping assistance function, the degradation mode is the same. 

What will trigger the degradation mode? The malfunctions that you have already learned about. Is the safe state invoked? Yes. 

The driver warning column discusses how the driver will be warned about the malfunction.
