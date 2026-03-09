# Software Safety Requirements Lane Departure Warning

> Part of: **Functional Safety at the Software and Hardware Levels**

## Images

![Software Architecture Diagram](images/refined-system-architecture-l6-01.png)
*Software Architecture Diagram*

## Additional Content

### Software Safety Requirements - Lane Departure Warning Amplitude Malfunction

For the purposes of this module, we do not expect you to derive software safety requirements. But the examples below should give you a sense for how to derive software safety requirements from technical safety requirements. The examples also show the major differences between technical requirements and software requirements; software requirements are much more specific than technical requirements. Software requirements specify variable names, signal paths, and software protocols and mechanisms. A software engineer should be able to write a program from the software requirements and software architecture.

We are going to show you examples of software safety requirements that we have derived from the technical safety requirements. First, we will show you the refined architecture and then explain all of the new elements that we have added:

### Software Safety Requirements Derived from Technical Safety Requirement 01
Let's take a look at our technical safety requirements one at a time and derive software safety requirements. You might want to refer back to this diagram as we explain the new functionality.

Here is our first technical safety requirement:
| ID | Technical Safety Requirement | ASIL | Fault Tolerant Time Interval | Allocation to Architecture | Safe State |
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|------------------------------|----------------------------|--------------------------------|
| TechnicalSafetyRequirement_01 | The LDW safety component shall ensure that the amplitude of the LDW_Torque_Request sent to the Final Electronic Power Steering Torque component is below Max_Torque_Amplitude | C | 50 mS | LDW Safety | LDW torque output is set to zero |
We are going to split the LDW safety component into three blocks. 

The first block will get the torque request from Basic/Main Lane Assistance functionality component. That first block will do any pre-processing needed. Then the block sends the results out to a torque limiter block that will check if the torque is beyond the allowed maximum amplitude. If the limit is reached, the torque request is set to zero. Finally, we'll add a third block that gets the signal ready for transmitting to the final torque generator.

Here are the new software safety requirements:
| ID | Technical Safety Requirement | ASIL | Allocation Software Elements | Safe State |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|------------------------------|---------------------------------------------|
| SoftwareSafetyRequirement01-01 | The input signal “Primary_LDW_Torq_Req” shall be read and pre-processed to determine the torque request coming from the “Basic/Main LAFunctionality” SW Component.  Signal “processed_LDW_Torq_Req” shall be generated at the end of the processing. | C | LDW_SAFETY_INPUT_PROCESSING | N/A |
| SoftwareSafetyRequirement01-02 | In case the “processed_LDW_Torq_Req” signal has a value greater than “Max_Torque_Amplitude_LDW” (maximum allowed safe torque), the torque signal “limited_LDW_Torq_Req” shall be set to 0,  else “limited_LDW_Torq_Req” shall take the value of “processed_LDW_Torq_Req”. | C | TORQUE_LIMITER | “limited_LDW_Torq_Req” = 0 (Nm=Newton-meter) |
| SoftwareSafetyRequirement01-03 | The “limited_LDW_Torq_Req” shall be transformed into a signal “LDW_Torq_Req” which is suitable to be transmitted outside of the LDW Safety component (“LDW Safety”) to the “Final EPS Torque”component. Also see SofSafReq02-01 and SofSafReq02-02 | C | LDW_SAFETY_OUTPUT_GENERATOR | LDW_Torq_Req= 0 (Nm) |
Compare these new software safety requirements against the new system architecture diagram.

Let's look at our second technical safety requirement.
### Software Safety Requirements Derived from Technical Safety Requirement 02

Here is technical safety requirement 02:
| ID | Technical Safety Requirement | ASIL | Fault  Tolerant  Time  Interval | Allocation to Architecture | Safe State |
|------------------------------|-------------------------------------------------------------------------------------------------|------|---------------------------------|------------------------------------|------------|
| TechnicalSafetyRequirement02 | The validity and integrity of the data transmission for LDW_Torque_Request signal shall be ensured | C | 50 ms | Data  Transmission Integrity Check | N/A |
This requirement is going to be solved with something called an End2End (E2E) protocol. We're going to discuss this protocol towards the end of the lesson in the part labeled "Freedom from Interference - Communication"

Here are software safety requirements derived from the technical safety requirements 02:
| ID | Technical Safety Requirement | ASIL | Allocation Software Elements | Safe State |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|------------------------------|----------------------|
| SoftwareSafetyRequirement02-01 | Any data to be transmitted outside of the LDW Safety component (“LDW Safety”) including "LDW_Torque_Req" and “activation_status” (see SofSafReq03-02) shall be protected by an End2End(E2E) protection mechanism | C | E2ECalc | LDW_Torq_Req= 0 (Nm) |
| SoftwareSafetyRequirement02-02 | The E2E protection protocol shall contain and attach the control data: alive counter (SQC) and CRC to the data to be transmitted. | C | E2ECalc | LDW_Torq_Req= 0 (Nm) |
### Software Safety Requirements Derived from Technical Safety Requirement 03

Technical Safety Requirement 03:

| ID | Technical Safety Requirement | ASIL | Fault  Tolerant  Time  Interval | Allocation to Architecture | Safe State |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|------|---------------------------------|----------------------------|----------------------------------|
| TechnicalSafetyRequirement03 | As soon as a failure is detected by the LDW function, it shall deactivate the LDW feature and the LDW_Torque_Request shall be set to zero | C | 50 ms | LDW Safety | LDW torque output is set to zero |
To solve the deactivation requirement, we are going to add an error detection block as an extra check on shutting down the lane keeping system. Each software block will output a signal as to whether or not an error has occurred. The signal will go to the "Final EPS Torque Generator" block alongside the actual torque request. 

Here are the new software safety requirements:

| ID | Technical Safety Requirement | ASIL | Allocation Software Elements | Safe State |
|--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|------------------------------|--------------------------------------------------|
| SoftwareSafetyRequirement03-01 | Each of the SW elements shall output a signal to indicate any error which is detected by the element.  Error signal = error_status_input(LDW_SAFETY_INPUT_PROCESSING), error_status_torque_limiter(TORQUE_LIMITER), error_status_output_gen(LDW_SAFETY_OUTPUT_GENERATOR) | C | All | N/A |
| SoftwareSafetyRequirement03-02 | A software element shall evaluate the error status of all the other software elements and in case any 1 of them indicates an error, it shall deactivate the LDW feature (“activation_status”=0) | C | LDW_SAFETY_ACTIVATION | Activation_status = 0 (LDW function deactivated) |
| SoftwareSafetyRequirement03-03 | In case of no errors from the software elements, the status of the LDW feature shall be set to activated (“activation_status”=1) | C | LDW_SAFETY_ACTIVATION | N/A |
| SoftwareSafetyRequirement03-04 | In case an error is detected by any of the software elements, it shall set the value of its corresponding torque to 0 so that “LDW_Torq_Req” is set to 0 | C | All | LDW_Torq_Req = 0 |
| SoftwareSafetyRequirement03-05 | Once the LDW functionality has been deactivated, it shall stay deactivated till the time the ignition is switched from off to on again.  | C | LDW_SAFETY_ACTIVATION | Activation_status = 0 (LDW function deactivated) |
### Software Safety Requirements Derived from Technical Safety Requirement 04

Our fourth technical safety requirement discusses sending an error signal to the car display ECU:

| ID | Technical Safety Requirement | ASIL | Fault  Tolerant  Time  Interval | Allocation to Architecture | Safe State |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|------|---------------------------------|----------------------------|----------------------------------|
| TechnicalSafetyRequirement04 | As soon as the LDW function deactivates the LDW feature, the LDW Safety software block shall send a signal to the car display ECU to turn on a warning light | C | 50 ms | LDW Safety | LDW torque output is set to zero |
And here is a software safety requirement for technical safety requirement number 04:
| ID | Technical Safety Requirement | ASIL | Allocation Software Elements | Safe State |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------|------|---------------------------------------|------------|
| SoftwareSafetyRequirement04-01 | When the LDW function is deactivated (activation_status set to 0), the activation_status shall be sent to the car displayECU. | C | LDW_SAFETY_ACTIVATION, CarDisplay ECU | N/A |
### Software Safety Requirements Derived from Technical Safety Requirement 05

And finally, technical safety requirement 05:

| ID | Technical Safety Requirement | ASIL | Fault  Tolerant  Time  Interval | Allocation to Architecture | Safe State |
|------------------------------|-------------------------------------------------------------------------------------------|------|---------------------------------|----------------------------|----------------------------------|
| TechnicalSafetyRequirement05 | Memory test shall be conducted at start up of the EPS ECU to check for any faults in memory | A | Ignition Cycle | Memory Test | LDW torque output is set to zero |
Here are typical software safety requests for memory tests:
| ID | Technical Safety Requirement | ASIL | Allocation Software Elements | Safe State |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|------------------------------|-----------------------|
| SoftwareSafetyRequirement05-01 | A CRC verification check over the software code in the Flash memory shall be done every time the ignition is switched from off to on to check for any corruption of content. | A | MEMORYTEST | Activation_status = 0 |
| SoftwareSafetyRequirement05-02 | Standard RAM tests to check the data bus, address bus and device integrity shall be done every time the ignition is switched from off to on (E.g.walking 1s test, RAM pattern test. Refer RAM and processor vendor recommendations ) | A | MEMORYTEST | Activation_status = 0 |
| SoftwareSafetyRequirement05-03 | The test result of the RAM or Flash memory shall be indicated to the LDW_Safety component via the “test_status” signal | A | MEMORYTEST | Activation_status = 0 |
| SoftwareSafetyRequirement05-04 | In case any fault is indicated via the “test_status” signal the INPUT_LDW_PROCESSING shall set an error on error_status_input (=1) so that the LDW functionality is deactivated and the LDWTorque is set to 0 | A | LDW_SAFETY_INPUT_PROCESSING | Activation_status = 0 |
### Final Project

In the final project, you will need to document the information presented on this page. The information will go into the "Software Safety Requirements and Architecture Lane Assistance" document.
