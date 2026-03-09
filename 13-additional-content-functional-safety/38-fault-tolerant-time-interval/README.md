# Fault Tolerant Time Interval

> Part of: **Functional Safety: Functional Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=o4PzRfVN_to)

## Summary

**Functional Safety Requirements and System Architecture**
===========================================================

This document summarizes the key concepts and practical notes from the lesson on deriving functional safety requirements and allocating them to system architecture.

### Key Concepts

* **Fault Tolerant Time Interval**: The time it takes for a system to detect and react to a malfunction. It is calculated as the sum of the diagnostic test interval, fault reaction time, and time in safe state before an accident.
* **Diagnostic Test Interval**: The time it takes for the system to detect a malfunction, such as a high vibration amplitude in the ADS lane departure warning system.
* **Fault Reaction Time**: The time it takes for the vehicle to turn off the lane departure warning function after detecting a malfunction.
* **Time in Safe State**: The time between when the system reaches a safe state and when an accident would have occurred.

### Practical Notes

* To calculate the fault tolerant time interval, add the diagnostic test interval, fault reaction time, and time in safe state before an accident.
* Each safety requirement receives a fault tolerant time interval, which can be used to determine how much time the vehicle has to react to a malfunction. For example, the lane departure warning system has a fault tolerant time interval of 50 milliseconds.

**Example Formula**

Fault Tolerant Time Interval = Diagnostic Test Interval + Fault Reaction Time + Time in Safe State

Note: The actual value of the fault tolerant time interval may vary depending on the specific system and application.

## Transcript

<v English>Deriving functional safety requirements and allocating those requirements to</v> <v English>the system architecture is the main part of a functional safety concept.</v> <v English>To finish up the lesson,</v> <v English>we still need to talk about three more attributes of a functional safety requirement.</v> <v English>The fault tolerant time interval,</v> <v English>the warning and degradation concept,</v> <v English>and the verification of validation acceptance criteria.</v> <v English>We'll start with the fault tolerant time interval.</v> <v English>We need to define how long the system has to detect and then react to a malfunction.</v> <v English>We call this the fault tolerant time interval.</v> <v English>Let's look at our ADS lane departure warning as an example.</v> <v English>One concern is that the warning vibration amplitude will be too high.</v> <v English>If the amplitude does get too high then a malfunction,</v> <v English>also called the fault, has occurred.</v> <v English>It will take the system a certain amount of time to detect</v> <v English>a malfunction and signals travel through the hardware and the software.</v> <v English>This is the diagnostic test interval.</v> <v English>Once the system detects the high amplitude,</v> <v English>it will take time for the vehicle to turn off the lane departure warning function.</v> <v English>This is the fault reaction time.</v> <v English>Once turned off, the lane assistance system has reached</v> <v English>a safe state where risk is at acceptable levels.</v> <v English>We want the lane assistance system to reach a safe state before an accident has occurred.</v> <v English>So there is a buffer between when the system reaches</v> <v English>a safe state and when an accident would have occurred.</v> <v English>So fault tolerant time interval equals</v> <v English>diagnostic test interval plus fault</v> <v English>reaction time plus time in safe state before an accident.</v> <v English>Each safety requirement receives a fault tolerant time interval.</v> <v English>We will say that the lane departure warning system</v> <v English>has a fault tolerant time interval of 50 milliseconds.</v> <v English>You can use this value for the two functional safety requirements already discussed.</v> <v English>This is an example of value you might see in practice but</v> <v English>the real world lane departure warning function might have a different value.</v> <v English>The fault tolerant time interval let's us know</v> <v English>how much time the vehicle has to react to a malfunction.</v>

## Additional Content

### Fault Tolerant Time interval
### Measuring Fault Tolerant Time Intervals

Depending on the hazardous situations, you might also have to consider the fault reaction time of a human driver. So you would have to run tests with actual drivers to see how long they take to react to a fault and avoid a hazardous situation. 

On the other hand, software and hardware diagnostic test intervals and fault reaction times could be measured with a bench test. 

You can't change a human's fault reaction time; however, you can optimize your software and hardware to minimize the diagnostic test interval and fault reaction time. 

Whatever the hazardous situation, the idea of the fault tolerant time interval is to investigate how long your system has to avoid accidents when faults occur. 
### ISO 26262 Revisions
A second addition of ISO 26262 is in production and may redefine some FTTIs presented here.
### Fault Tolerant Time Interval: Lane Keeping Assistance Fault


In terms of the lane keeping assistance, the concern was that the functionality wasn't time limited. If the lane keeping assistance goes beyond the time limit we set, then a fault has occurred and you will want to shut off the system. 

The fault tolerant time interval might be 500 ms since the situation would be more controllable than for the warning system case. Because the system is now time limited, the driver will be unable to misuse the system as if it were fully autonomous, and will be more likely to keep their hands on the wheel at all times. If the lane keeping assistance function goes beyond the time limit and keeps turning the vehicle towards the center of the lane, the driver could still remain in control of the car. The lane assistance system is merely adding extra steering torque to the torque that the driver is already providing.
