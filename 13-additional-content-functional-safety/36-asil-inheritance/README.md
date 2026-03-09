# ASIL Inheritance

> Part of: **Functional Safety: Functional Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=oeKSXaP7Lxg)

## Summary

**Functional Safety Analysis with ASIL Labels**
====================================================

This project involves adding ASIL (Automotive Safety Integrity Level) labels to a refined architectural diagram. The goal is to identify which subsystems and elements require analysis under ISO 26262, a standard for functional safety in the automotive industry.

### Key Concepts

* **ASIL**: A classification system used to determine the level of risk associated with a particular system or component.
	+ ASIL C: The highest level of risk, indicating that a failure could result in serious injury or death.
	+ QM (Quality Management): A rating assigned to components where the risk is already at acceptable levels and further analysis is not required.
* **Functional Safety Requirements**: Derived from safety goals, these requirements specify how a system must behave to ensure safe operation.
* **Hazard Analysis and Risk Assessment**: A process used to identify potential hazards and assess the risks associated with them.
* **ISO 26262**: An international standard for functional safety in the automotive industry.

### Practical Notes

To apply this knowledge, you will need to:

1. Identify the ASIL classification of each subsystem based on its allocated functional safety requirements.
2. Determine which components can be assigned a QM rating if their risk levels are already at acceptable levels.
3. Refine your architectural diagram to include ASIL labels for each subsystem and component.

Note: This lesson assumes prior knowledge of ISO 26262 and functional safety analysis. If you are new to this topic, it is recommended that you review the relevant standards and guidelines before proceeding.

## Transcript

<v English>We need to add ASIL labels to the refined architectural diagram.</v> <v English>Otherwise, we won't know which subsystems and elements require analysis under ISO 26262.</v> <v English>The general rule is that</v> <v English>functional safety requirements inherit the ASIL directly from the safety goal.</v> <v English>From the hazard analysis and risk assessment,</v> <v English>the lane departure warning safety goal was that the torque had to be limited.</v> <v English>We determined that the safety goal had ASIL</v> <v English>C. The two functional safety requirements for the lane departure warning</v> <v English>would then inherit the ASIL C. Because we allocated</v> <v English>these two functional safety requirements to electronic power steering,</v> <v English>the entire subsystem inherits the ASIL C classification.</v> <v English>But what about the ASIL of the camera in the car display subsystems?</v> <v English>We said earlier that the only relevant subsystem from</v> <v English>the functional safety standpoint was the electronic power steering.</v> <v English>We do not have any functional safety requirements for these two subsystems.</v> <v English>Therefore, we can mark the camera in the car display as QM.</v> <v English>As a reminder, a QM rating stands for quality management.</v> <v English>Any part of the architecture where the QM rating is no longer relevant to</v> <v English>a functional safety analysis because the risk is already at acceptable levels.</v> <v English>Here's a quick review of what we have accomplished so far.</v> <v English>We derived functional safety requirements from the safety goals,</v> <v English>refined the architecture and allocated the functional safety requirements to</v> <v English>the architecture and we determine the risk levels for the three subsystems.</v> <v English>Next, we'll see if there are any ways to lower the ASIL for any of our system elements.</v>

## Additional Content

### ASIL Inheritance
As noted in a note to a previous video, the "QM" rating does not mean functional safety is irrelevant - QM approaches need to be applied to ensure lower level risks are mitigated, but they are not directly covered under ISO 26262.

### Electronic Power Steering SubSystem ASIL

We didn't directly talk about the driver steering sensor or the motor that turns the steering wheel. We simplified things marking both as ASIL C even though the functional safety requirements only pertained to the power steering ECU. 

The motor to turn the steering wheel would also be marked ASIL C since it is an integral part to ensuring the lane assistance torque does not create unsafe conditions. You can consider that the entire lane keeping item has the highest ASIL identified from the hazard and risk analysis unless you can justify otherwise.

Remember that our example is a simplification of a real system.  By virtue of safety requirements that comprise the safety goal design parameters,  there would be functional safety requirements directly associated with  to the steering wheel motor as well as the driver torque steering wheel sensor. In fact, most auto manufacturers would label an entire electronic power steering system ASIL D based on a hazard analysis and risk assessment.
### Quiz


For the lane keeping assistance function, recall that the safety goal was that the "Lane keeping assistance function shall be time limited and the additional steering torque shall end after a given timer interval so that the driver can not misuse the system for autonomous driving".

The functional safety requirement was that "the electronic power steering ECU shall ensure that the lane keeping assistance torque is applied for only Max_Duration". 

What is the ASIL of the functional safety requirement?
