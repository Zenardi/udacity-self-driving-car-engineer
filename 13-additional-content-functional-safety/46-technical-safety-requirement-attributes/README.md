# Technical Safety Requirement Attributes

> Part of: **Functional Safety: Technical Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=EOYTl2e8wEs)

## Summary

**Technical Safety Requirements Summary**
=====================================

This summary covers the key concepts and practical notes from a lesson on technical safety requirements, which are essential for ensuring the safe operation of complex systems.

**Key Concepts**
---------------

* **ASIL (Automotive Safety Integrity Level)**: A measure of the severity of potential hazards in automotive systems. Technical safety requirements inherit ASILs from functional safety requirements.
* **Fault Tolerant Time Interval**: The time it takes for a system to recover from a fault or error. This interval may need to be adjusted for each technical safety requirement, but for this discussion, we will use the intervals from functional safety requirements.
* **Description of Safe State Transition**: A description of how a system transitions to a safe state in case of an error or fault.

**Practical Notes**
-----------------

* When inheriting ASILs from functional safety requirements, technical safety requirements are typically assigned the same ASIL level (e.g., ASIL C).
* The only exception is the requirement for testing memory, which is assigned ASIL A due to specific standards allowing latent faults to be labeled as such.
* Fault tolerant time intervals may need to be adjusted for each technical safety requirement, but in this case, we will use the intervals from functional safety requirements (50 milliseconds for all technical safety requirements except memory test).
* For memory test, the fault tolerant time interval takes into account the time to check for memory corruption and system failure to detect it. This interval can be considered as the length of the vehicle ignition cycle.
* The safe state for all faults is that the lane departure warning talk request amplitude shall be set to zero.

Note: A table with the results so far is provided, and the next step is to allocate these technical safety requirements to the system architecture.

## Transcript

<v English>Technical safety requirements have some of the same</v> <v English>attributes that we discussed for functional safety requirements.</v> <v English>These attributes are ASIL,</v> <v English>fault tolerant time interval and description of safe state transition.</v> <v English>The technical safety requirements,</v> <v English>inherit ASILs from the functional safety requirements because</v> <v English>the safety requirements for the lane departure warning were ASIL C,</v> <v English>the technical safety requirements are ASIL C as well.</v> <v English>The only exception is the last requirement for testing memory.</v> <v English>This requirement is ASIL A because the standard says,</v> <v English>that the latent fault to deduction for ASIL C requirements can be labeled ASIL A.</v> <v English>It would be possible to decompose ASILs as we did for the functional safety concept.</v> <v English>Fault tolerant time intervals,</v> <v English>might need to be adjusted for each technical safety requirement.</v> <v English>But for the purposes of this discussion,</v> <v English>we will use the fault tolerant time intervals from the functional safety requirement.</v> <v English>So for all of the technical safety requirements of the lane departure warning function,</v> <v English>the time interval shall be 50 milliseconds.</v> <v English>Once again, the technical safety requirements for memory test is an exception.</v> <v English>Here, the fault tolerant time interval would take into account the time to</v> <v English>check for memory corruption and</v> <v English>the failure of the system to detect the memory corruption.</v> <v English>The system will do this on start up.</v> <v English>We can consider the fault tolerant time interval</v> <v English>to be the length of the vehicle ignition cycle.</v> <v English>The safe state for all of these faults is that,</v> <v English>the lane departure warning talk request amplitude shall be set to zero.</v> <v English>We're providing a table with the results we have so far.</v> <v English>With the technical safety requirements defined,</v> <v English>the next step is to allocate these requirements to the system architecture.</v>

## Additional Content

### Table of Results

| Requirement ID | Technical Safety Requirement                                                                                                                                                        | FTTI  | ASIL |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------|------|
| TechSafReq01   | The LDW safety component shall ensure that the amplitude of the 'LDW_Torque_Request' sent to the 'Final electronic power steering Torque' component is below 'Max_Torque_Amplitude. | 50 ms | C    |
| TechSafReq02   | As soon as the LDW function deactivates the LDW feature, the 'LDW Safety' software block shall send a signal to the car display ECU to turn on a warning light.                     | 50 ms | C    |
| TechSafReq03   | As soon as a failure is detected by the LDW function, it shall deactivate the LDW feature and the 'LDW_Torque_Request' shall be set to zero.                                        | 50 ms | C    |
| TechSafReq04   | The validity and integrity of the data transmission for 'LDW_Torque_Request' signal shall be ensured.                                                                               | 50 ms | C    |
| TechSafReq05   | Memory test shall be conducted at start up of the EPS ECU to check for any faults in memory.                                                                                        | ignition cycle | A    |
### Quiz
