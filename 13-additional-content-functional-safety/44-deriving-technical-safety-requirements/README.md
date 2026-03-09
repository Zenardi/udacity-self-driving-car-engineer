# Deriving Technical Safety Requirements

> Part of: **Functional Safety: Technical Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=fVLsG83a-So)

## Summary

**Technical Safety Requirements**
=====================================

This summary outlines the key concepts and practical notes from a lesson on deriving technical safety requirements.

### Key Concepts

* **Functional Safety Requirement**: A requirement that defines what a system is supposed to do when a malfunction violates a safety goal.
* **Technical Safety Requirement**: A requirement that indicates the signal flow and describes which components are in charge of a functionality.
* **Signal Flow**: The path that signals take through a system, including how they are processed and transmitted between components.
* **LDW (Lane Departure Warning)**: A safety software component that sends torque requests to the EPS (Electronic Power Steering) component.
* **EPS (Electronic Power Steering)**: A component that receives torque requests from the LDW component and applies them to the vehicle's steering system.

### Practical Notes

When deriving technical safety requirements, consider the following:

* Use acronyms to make requirements easier to read and understand. For example, use "LDW" instead of "Lane Departure Warning".
* Identify the signal flow between components and describe which components are responsible for each functionality.
* Compare functional safety requirements with technical safety requirements: functional safety requirements provide a general idea of what a system is supposed to do, while technical safety requirements indicate the specific signal flow and component interactions.

Example code or formulas:

```markdown
LDW Torque Request:
- Amplitude should be below max torque amplitude

EPS Response:
- Receive LDW torque request
- Apply torque to steering system
```

Note: This summary is a plain English explanation of the key concepts and practical notes from the lesson. It does not include any code or formulas that were presented in the lesson.

## Transcript

<v English>Technical safety requirements describe what a system</v> <v English>will do when a malfunction violates a safety goal.</v> <v English>Let's derive an example from the lane departure warning safety goal.</v> <v English>Recall from the safety goal,</v> <v English>we derived a functional safety requirement that</v> <v English>the electronic power steering ECU needed to</v> <v English>keep the torque amplitude below a maximum threshold.</v> <v English>Now, we will go one step further and derive a technical safety requirement.</v> <v English>When the lane departure warning safety software component sends a torque request,</v> <v English>the request amplitude should be below the maximum allowed threshold.</v> <v English>Using the system architecture diagram,</v> <v English>the requirement is formally that</v> <v English>the LDW safety component shall ensure that the amplitude of</v> <v English>the LDW torque request sent to</v> <v English>the final electronic power steering torque component is below max torque amplitude.</v> <v English>We'll start using acronyms to make the requirements easier to read.</v> <v English>LDW is lane departure warning.</v> <v English>While EPS is electronic power steering.</v> <v English>Notice the difference between</v> <v English>a functional safety requirement and the technical safety requirement.</v> <v English>The functional safety requirement gives</v> <v English>a general idea of what a system is supposed to do.</v> <v English>The technical safety requirement indicates the signal flow</v> <v English>and describes which components are in charge of the functionality.</v>

## Additional Content

While the video states that latent faults only need to be addressed for ASIL C and ASIL D, the hardware latent fault metric also has ASIL B targets.
### Quiz - Vocabulary Check
