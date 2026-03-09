# Functional Safety Analysis

> Part of: **Functional Safety: Functional Safety Concept**

## Additional Content

### Functional Safety Analysis

Before we derive safety requirements, let's talk about malfunctions. We've said that the main purpose or function of the lane departure warning and lane keeping assistance is to provide vibrational steering feedback and torque to the driver as haptic feedback. And we had a safety goal to limit the oscillating torque.

What would be a malfunction for this? One approach is to use guide words.  ISO 26262 does not provide guidewords, however companies often use these as part of their guidelines. Some example guidewords for this case are:

* NO
* WRONG
* EARLY
* MORE
* LESS

So in the case of the lane departure warning, "MORE" seems like an appropriate guide word; the lane departure warning is giving MORE torque than what is safe. There would be two malfunctions. The oscillating amplitude is too high and the oscillating frequency is too high. Formally, the malfunctions would be:

"The lane departure warning function applies an oscillating torque with very high torque amplitude (above limit)"

"The lane departure warning function applies an oscillating torque with very high torque frequency (above limit)"

For the lane keeping assistance function, "NO" would be an appropriate guide word. The lane keeping assistance keeps the vehicle centered in the lane. The malfunction would be that the assistance has no time limit. The malfunction would be:

"The lane keeping assistance function is not limited in time duration which leads to misuse as an autonomous driving function."

Notice that the information in the functional safety analysis comes from the hazard analysis and risk assessment. While this exercise might seem trivial, imagine having hundreds of functions each with various malfunctions. The guide words help to analyze functions and malfunctions methodically. These malfunctions are then converted into functional safety requirements
