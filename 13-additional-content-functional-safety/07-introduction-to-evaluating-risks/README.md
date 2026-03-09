# Introduction to Evaluating Risks

> Part of: **Introduction to Functional Safety**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=3N-6YK_pPzA)

## Summary

**Risk Evaluation in Functional Safety Analysis**
=====================================================

This lesson introduces the concept of evaluating risk associated with hazards, a crucial step in functional safety analysis. We will explore how to quantify risk using a numerical approach.

### Key Concepts
* **Risk**: A measure of the severity of harm times the probability of occurrence.
* **Severity of Harm**: Measures how badly a person could be injured when an accident occurs (scale: 1-4).
* **Probability of Occurrence**: The frequency with which typical drivers find themselves driving in a certain situation (scale: 1-4).
* **Risk Calculation Formula**: Risk = Severity of Harm × Probability of Occurrence.

### Practical Notes
To calculate risk, you need to assign a severity score and a probability score for each hazard. For example:

| Hazard | Severity Score | Probability Score |
| --- | --- | --- |
| Power steering malfunction on a snowy mountain pass | 4 (fatal injury) | 2 (unlikely scenario) |

Risk = 4 × 2 = 8

In functional safety analysis, risks are quantified to determine how much they need to be lowered. Vehicle systems with high risks require more analysis and testing to bring the risk down to acceptable levels.

Note: This lesson provides a basic understanding of risk evaluation in functional safety analysis. In real-world applications, you may need to consider additional factors and use more complex methods to quantify risk.

## Transcript

<v English>Now that we have an idea about how to identify hazards,</v> <v English>we need to evaluate the risk associated with each hazard.</v> <v English>Evaluating risk will be an important part of our more formal functional safety analysis.</v> <v English>Every hazard has a certain risk associated with it.</v> <v English>And since we are thinking like functional safety engineers,</v> <v English>we are going to define risk numerically.</v> <v English>Risk equals severity of harm times probability of occurrence.</v> <v English>Severity of harm measures how badly a person could be injured when an accident occurs.</v> <v English>Probability of occurrence has a specific definition for passenger car functional safety.</v> <v English>It is the frequency with which</v> <v English>typical drivers find themselves driving in a certain situation.</v> <v English>For example, driving on a city street has</v> <v English>a high probability of occurrence because people do it everyday.</v> <v English>Driving on a snowy mountainside has</v> <v English>a low probability because people hardly find themselves driving in those conditions.</v> <v English>Probability of occurrence only takes into</v> <v English>account how often you find yourself driving in a certain situation.</v> <v English>It does not take into account how likely a malfunction will occur,</v> <v English>like the probability of your brakes failing.</v> <v English>Failing brakes would lead to</v> <v English>high severity but would not affect probability of occurrence.</v> <v English>Let's go through an example of calculating risk.</v> <v English>We'll say that severity has a scale of one to four,</v> <v English>with one representing no injury and four representing fatal injury.</v> <v English>Probability of occurrence will also be on a scale from one to four,</v> <v English>one being an unlikely scenario like needing a jump start,</v> <v English>while four will be a likely scenario like driving on a highway.</v> <v English>Here's our scenario, you're driving on</v> <v English>a snowy mountain side pass and the power steering malfunctions.</v> <v English>I would say severity is a four because we could easily lose control of the vehicle,</v> <v English>driving off the mountainside and suffer a fatal injury.</v> <v English>Probability of occurrence could be a two</v> <v English>because you would not find yourself driving on a snowy mountainside very often.</v> <v English>Risk then is four times two equals eight.</v> <v English>In functional safety analysis,</v> <v English>we quantify risk to determine how much we need to lower the risk.</v> <v English>Vehicle systems with high risks require</v> <v English>more analysis and testing to bring the risk down to acceptable levels.</v>

## Additional Content

### ASIL (Automotive Safety Integrity Level)

The ISO 26262 standard defines a risk factor called ASIL - Automotive Safety Integrity Level. ASIL is a four point scale of ASIL A, ASIL B, ASIL C and ASIL D. 

ASIL D represents a hazardous situation with the highest risk whereas ASIL A represents lower risk. ASIL is a key term in automotive functional safety. The video introduced the basic ideas behind how to calculate ASIL, but we will leave the details for the Hazard Analysis and Risk Assessment Lesson.

There is one more level of risk below ASIL A called QM. QM stands for quality managed. QM means that  development according to accepted quality principles is sufficient to reduce risk.   You will learn more about ASIL and QM in the lesson on hazard analysis and risk assessment.

### Quiz

Let's measure probability of occurrence and severity on a scale from 1 to 4 with 4 representing highly probable and severe situations. Here are some guidelines for measuring probability of occurrence and severity:

**Probability of occurrence:**

1 - Vehicle jumpstart needed

2 - Driving in snow

3 - Driving at night with no street lamps

4 - Driving on the highway

**Severity:**

1 - No injury

2 - Light and moderate injury

3 - Severe and life threatening injuries with probable survival 

4 - Life threatening injuries, survival uncertain, or fatal injury

Remember that:
** risk = probability of occurrence x severity**



RANK THE FOLLOWING HAZARDOUS SITUATIONS FROM LEAST RISKY TO MOST RISKY

A While driving on the highway, brakes fail at high-speed.

B Your vehicle requires a jumpstart. The power steering is not working but the vehicle is parked on the side of the 
road and not moving. 

C While driving in the snow in the city, anti-lock brakes fail while driving at low speed.

D While driving at night on a street with no street lamps, the car headlamps fail.
