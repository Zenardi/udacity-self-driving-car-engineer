# Safety Goals

> Part of: **Functional Safety: Hazard Analysis and Risk Assessment**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lMT1EB5cZR8)

## Summary

**Deriving Safety Goals from Requirements Engineering**
======================================================

This lesson covers the process of deriving safety goals from requirements engineering, a crucial step in ensuring the safe operation of complex systems. By identifying hazardous situations and defining what the system must do to avoid them, we can create effective safety goals that guide the design and development process.

**Key Concepts**
---------------

* **Safety Goal**: A type of requirement that defines what the item does to avoid hazardous situations.
* **Hazardous Event Description**: A description of a potential hazardous situation that could occur if the system fails or operates incorrectly.
* **ASIL C**: A level of Automotive Safety Integrity Level (ASIL) assigned to safety goals, indicating a moderate risk level.
* **Risk Reduction**: The process of identifying and mitigating risks by defining safety goals and requirements.

**Practical Notes**
------------------

When deriving safety goals from requirements engineering:

1. Identify the hazardous event description for each potential failure mode or malfunction.
2. Define what the system must do to avoid the hazardous situation, resulting in a clear safety goal statement.
3. Assign an ASIL level (such as ASIL C) to indicate the risk level associated with the safety goal.

Example:
```markdown
**Safety Goal:** The oscillating steering torque from the lane departure warning function shall be limited.

**Hazardous Event Description:** The lane departure warning function applies too high an oscillating torque to the steering wheel, which could lead to a crash.
```
By following this process and creating clear safety goals, we can ensure that our systems are designed with safety in mind and operate within acceptable risk levels.

## Transcript

<v English>The last step is to derive safety goals,</v> <v English>which brings us back to requirements engineering.</v> <v English>A safety goal defines what the item does to avoid hazardous situations.</v> <v English>So a safety goal is a type of requirement.</v> <v English>For the lane departure warning function,</v> <v English>the hazardous event description was that</v> <v English>the lane departure warning function applies</v> <v English>too high an oscillating torque to the steering wheel,</v> <v English>which could lead to a crash.</v> <v English>What would the lane departure warning function need to do to avoid the situation?</v> <v English>Limit the amount of vibration.</v> <v English>So the safety goal would be the oscillating steering torque</v> <v English>from the lane departure warning function shall be limited.</v> <v English>So the safety goal has ASIL C. Limiting</v> <v English>the vibrational steering torque would help lower the risk to an acceptable.</v>

## Additional Content

### Lane Keeping Assistance Safety Goals


What about the lane keeping assistance function? In this case, the hazardous situation involved the driver taking both hands off the wheel. Because the functionality was always on, the driver could misuse the lane keeping assistant as if it were meant for autonomous driving. What would the safety goal be for this second case?
### Safety Goals and Requirements Engineering


In the first lesson, we mentioned that requirements engineering was a sub-discipline of systems engineering. Requirements generally start with the phrase "X system shall [do something]". 

Safety goals are a specific type of engineering requirement. Safety goals specifically define what the vehicle needs to do in order to remain safe.
