# Other Types of Technical Safety Requirements

> Part of: **Functional Safety: Technical Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=9xIlkXobXS0)

## Summary

**Technical Safety Requirements in ISO 26262**

This lesson covers the various categories of Technical Safety Requirements mandated by ISO 26262. While Software Safety Requirements are crucial, there are five other essential categories that ensure overall system safety.

### Key Concepts

* **Fault Detection**: There are two types of fault detection:
	+ **Internal Fault Detection**: detecting faults within a system (e.g., software errors or hardware malfunctions)
	+ **External Fault Detection**: detecting faults in external devices interacting with the system
* **Safe State Transition**: ensuring the system reaches and maintains a safe state in case of failure
* **Warning and Degradation Concepts**: implementing measures to warn users of potential hazards and degrade system functionality when necessary
* **Latent Fault Prevention**: taking measures during power up, power down, or maintenance to prevent undetected errors (latent faults)
* **ASIL (Automotive Safety Integrity Level)**: a measure of the required safety integrity for each item in the system

### Practical Notes

When implementing Technical Safety Requirements, consider the following:

* Code needs to be added to check for communication errors between ECUs
* A safe state can be defined as switching off the Lane Assistance System
* Warning lights should turn on when a failure is detected by the LDW function
* Memory tests should be conducted at startup to prevent latent faults in ASIL C or D items

Note: This summary focuses on the main concepts and practical steps introduced in the lesson. For more detailed information, refer to the original transcript or additional resources provided.

## Transcript

<v English>Not all Technical Safety Requirements are</v> <v English>derived directly from Software Safety Requirements.</v> <v English>There are actually five other categories of</v> <v English>Technical Safety Requirements that ISO 26262 requires.</v> <v English>Two of the categories are for detecting false either within</v> <v English>the system or in an external device interacting with the system.</v> <v English>The other three categories are from</v> <v English>measures that enable the system to reach a safe state,</v> <v English>to implement a warning and degradation concept,</v> <v English>or to prevent latent faults.</v> <v English>Here is an example of each case for the lane departure warning function.</v> <v English>A fault within a system could either be</v> <v English>a software error or a hardware component that malfunctions.</v> <v English>A general technical safety requirement would be that the validity and</v> <v English>integrity of the data transmission for the LDW_Torque_Request signal shall be ensured.</v> <v English>We will talk about specific methods for checking</v> <v English>data validity and integrity in the text below the video.</v> <v English>Now, let's look at a fault that is external to the Lane Assistance Item.</v> <v English>Let's say hypothetically, an external anti-lock brake</v> <v English>ECU was transmitting speed information to the Lane Keeping Assistance Item.</v> <v English>An error in the communication line between</v> <v English>the brake ECU and the power steering ECU could cause a failure.</v> <v English>Code needs to be added that checks for</v> <v English>communication errors and the information gets transmitted between ECUs.</v> <v English>We will derive a technical safety requirement that</v> <v English>enables the system to reach and maintain a safe state.</v> <v English>We already derived the safe state in the functional safety concept.</v> <v English>The Lane Assistance System shall be switched off.</v> <v English>A technical safety requirement would be that,</v> <v English>as soon as a failure is detected by the LDW function,</v> <v English>it shall deactivate the LDW feature and the LDW_Torque_Request shall be set to zero.</v> <v English>The next category involves</v> <v English>Technical Safety Requirements for implementing warning and degradation concepts.</v> <v English>We have already said in the previous lesson that a warning light</v> <v English>will turn on if the Lane Assistance Item malfunctions.</v> <v English>A technical safety requirement would be that,</v> <v English>as soon as the LDW function deactivates the LDW feature,</v> <v English>the LDW safety software block shall send</v> <v English>a signal to the car display ECU to turn on a warning light.</v> <v English>And finally, let's discuss an example of measure that prevents latent faults.</v> <v English>Latent faults are errors that exist but can not be detected.</v> <v English>An example would be a software error in the code that actually checks for the failures.</v> <v English>Measures against latent faults generally take place during power up,</v> <v English>power down, or during maintenance.</v> <v English>A Technical Safety Requirement for the Lane Keeping Assistance would be;</v> <v English>memory test shall be conducted at the start up</v> <v English>of EPS ECU to check for any faults in memory.</v> <v English>The functional safety standard only requires avoiding latent faults for items labeled</v> <v English>ASIL C or D. Now that we have described different types of Technical Safety Requirements,</v> <v English>we are going to discuss adding attributes to these requirements.</v> <v English>Attributes include ASIL, Fault Tolerant Time Intervals,</v> <v English>and a description of Safe State Transition.</v>

## Additional Content

## ISO 26262 Definition of Latent Faults

A more rigorous definition of latent faults from ISO 26262 reads:
> multiple-point fault (3.96) whose presence is not detected by a safety mechanism (3.141) nor perceived by the driver within the multiple-point fault detection time interval (3.97)
### Faults External to the Lane Keeping Item

We mentioned that a possible technical safety requirement for an external fault could be for code that checks communication errors between the anti-lock brake ECU and the power steering ECU. The anti-lock brake ECU might share vehicle speed data with the power steering ECU. We are not going to expand on this example in the rest of the lesson. But if you want to challenge yourself, consider expanding on this idea in the final project. 

Imagine that the lane keeping assistance function does not take driver speed into account when deciding how much torque to apply. This could lead to a potentially hazardous situation where the system turns the wheel too abruptly at a high vehicle speed. Or the lane keeping assistance provides too much extra torque on a sharp curve. The driver could lose control of the vehicle. So this idea could be part of a hazard and risk analysis, which would lead to a safety goal. Then you'd derive functional safety requirements from the safety goal. And finally you'd derive technical safety requirements from the functional safety requirements.
### More Technical Safety Requirements

Soon it will be your turn to identify technical safety requirements! In the project, you will be responsible for deriving technical safety requirements for the other two functional safety requirements.

The other two functional safety requirements were: 

"the electronic power steering ECU shall ensure that the lane departure warning oscillating torque frequency is below Max_Torque_Frequency". 

"the lane keeping assistance function shall be time limited and the additional steering torque shall end after a given timer interval so that the driver can not misuse the system for autonomous driving".

You will use the examples we've already given as a guide for deriving technical safety requirements. The truth is, most of the technical safety requirements already derived would also be relevant to the two other functional safety requirements. You might have to change variable names or architectural element names.

Remember that some technical safety requirements can be derived directly from a functional safety requirement; other technical safety requirements will fall under the five categories described in the above video.
### Methods for Checking Data Validity and Integrity

One of the technical safety requirements mentioned checking the data validity and integrity of the data transmission: "The validity and integrity of the data transmission for LDW_Torque_Request signal shall be ensured."

To check data validity and integrity, you can add a CRC (cyclic redundancy check); a [CRC](https://en.wikipedia.org/wiki/Cyclic_redundancy_check) is a well established methods that looks for changes to raw data. A qualifier can then be added as well, which is a signal indicating whether or not a signal is valid. The CRC ensures the data that is sent out by one element is the same data received by another element.

Another common mechanism is an alive counter. An alive counter checks that the signal is new and not an old signal; an alive counter increases the count every time a signal goes out.

CRCs and alive counters can be used together to guarantee correct transmission. The final lesson on software requirements will also discuss a specific CRC protocol in more depth.
