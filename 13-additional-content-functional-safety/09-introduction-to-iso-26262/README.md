# Introduction to ISO 26262

> Part of: **Introduction to Functional Safety**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=bjvpmBOG60Q)

## Summary

**International Functional Safety Standard: ISO 26262**
=====================================================

This project focuses on implementing the international functional safety standard, ISO 26262. The standard provides a framework for dealing with electronic system malfunctions in passenger vehicles.

### Key Concepts

* **Functional Safety**: Ensuring that vehicle systems behave as intended to prevent injury or harm to people's health.
* **ISO 26262**: An international standard that covers the entire vehicle safety lifecycle from planning, designing, testing, production, and post-production.
* **V Model**: A framework used in ISO 26262 to cover the entire vehicle safety lifecycle. The V model consists of:
	+ Left side: System planning and design
	+ Right side: System testing and integration
	+ Bottom: Subsystems
	+ Top: Integrated systems
* **Hardware Development vs Software Development**: Each has its own miniature V model within the larger model, with a clear distinction between hardware and software development.

### Practical Notes

The ISO 26262 standard uses the V model to ensure that vehicle systems are designed and developed with safety in mind. The standard covers all aspects of the vehicle safety lifecycle, from planning to post-production. In this project, we will focus on implementing the planning and design phase using the Lane Assistance System example.

**Code/Formula Note**

No specific code or formulas were mentioned in this lesson. However, the V model is a graphical representation that can be used as a reference for system planning and design.

**Next Steps**

In future lessons, we will delve deeper into the planning and design phase of ISO 26262 compliance using the Lane Assistance System example. We will cover the concept phase, product development at the system level, and product development at software and hardware levels.

## Transcript

<v English>You have now learned the basics of functional safety,</v> <v English>hazard identification, evaluating risk,</v> <v English>and using systems engineering to lower risk.</v> <v English>It's time to introduce the international functional safety standard, ISO 26262.</v> <v English>ISO 26262 provides a framework</v> <v English>for dealing with electronic system malfunctions in passenger vehicles.</v> <v English>In other words, the standard helps you ensure that if your vehicle systems do</v> <v English>not behave as intended the vehicle will not cause injury or harm to a person's health.</v> <v English>Remember the V model we have discussed previously.</v> <v English>ISO 26262 uses the V model to cover the entire vehicle safety lifecycle from planning,</v> <v English>designing, testing, production, and post-production.</v> <v English>Let's take a look at the V model.</v> <v English>It's a little bit more complex than the V model we looked at before,</v> <v English>but the principles are the same.</v> <v English>The left side represents system planning and design.</v> <v English>The right side shows system testing and integration.</v> <v English>The bottom of the V represents subsystems while the top integrated systems.</v> <v English>Note that the V model makes a clear distinction</v> <v English>between hardware development and software development.</v> <v English>Each one has its own miniature V model within the larger model.</v> <v English>Note also that you can connect to the left side of</v> <v English>the V and right side of the V with horizontal lines.</v> <v English>For every test and integration step.</v> <v English>You can go back and verify that the product being</v> <v English>developed actually matches the design specifications.</v> <v English>In the rest of the lessons,</v> <v English>we will go into the details about the planning and design phase.</v> <v English>We will be focusing on these specific parts of the V model.</v> <v English>We will use the Lane Assistance System example to study the concept phase,</v> <v English>product development at system level,</v> <v English>and product development at software and hardware level.</v> <v English>You will gain a basic understanding of what it takes to achieve</v> <v English>ISO 26262 compliance when designing an automotive system.</v>

## Additional Content

### What ISO 26262 Does and Does not Cover

ISO 26262 only covers electronic and electrical malfunctions in passenger vehicle systems. The standard provides a framework for reducing risks that could harm people's health.

The standard does not cover safety of mechanical, chemical  or hydraulic systems. 

Nor does the standard consider nominal performance as part of functional safety. Consider an automatic braking system as an example. The nominal performance could be that the brakes apply automatically when the vehicle detects an imminent collision. 

The standard does not require you to test nominal performance and prove that the brakes engage when a crash is imminent. Instead, the standard would require preventing malfunctions like if the automatic brakes engaged when there was no emergency.

However, there may be other standards or laws that cover nominal performance of automotive safety systems.
### Overview of the Concepts to be Covered

A big part of functional safety is documenting your work. Let's get an overview of what some of these documents are and how they relate to functional safety. The next few lessons will then go through each document in more detail.

##### Safety plan 

The safety plan gives an overview of how you are going to achieve a safe system. A few of the major elements include:
- what system is under consideration
- the goal of the project
- what steps will be taken to ensure safety
- the roles and personnel involved in the project
- the project timeline

##### Defining a system at the Item level

Specifies which vehicle system is being considered, the system boundaries and background information about the system.


##### Hazard Analysis and Risk Assessment 

This is where we brainstorm to imagine hazards where the system malfunctions and causes injury or harm. Then the risk is calculated for each hazardous scenario.


##### Functional Safety Concept

The functional safety concept provides a high level overview of the system. Based on the hazard analysis and risk assessment, you figure out what your system is required to do to stay safe. Then you identify what part of your system will need to be adjusted to take into account the new functionality.

##### Technical Safety Concept at the System Level

The functional safety concept and technical safety concept are similar. While the functional safety concept gives a high level overview of the system and what it needs to do, the technical safety concept gets into more detail. So whereas the functional safety concept might give a high level requirement like "the lane warning departure steering wheel vibration should be limited", the technical safety concept will discuss how electronic signals and control units need to behave in order to limit the steering wheel vibration.

Technical Safety Concepts are often divided into a System Level Technical Safety Concept and a SubSystem Level Technical Safety Concept. An electronic control unit, for example, might have its own technical safety concept.

To clarify the above concepts the functional safety concept is implementation independent considering only the functional level architecture. The technical safety concepts considers the implementation level of a system.
### Why Comply with ISO 26262?

ISO 26262 compliance is not legally required. But most if not all automotive companies and automotive parts suppliers strive to make their products compliant with the standard. The standard provides a methodical, state-of-the-art framework for ensuring a safe electrical/electronic system.

### What is ISO?

ISO stands for the [international Organization for Standardization](https://www.iso.org/home.html). ISO is a non-governmental organization that develops and provides product and system specifications for a variety of industries. Standards ensure that different manufacturers around the world use best practices.

### Vocabulary

The functional safety standard contains a lot of vocabulary.

One important set of words that come up often in functional safety is **fault, failure, hazard and risk**. If you can remember these four terms right from the start, the functional safety module will be easier to understand.

A

[fault](https://en.wikipedia.org/wiki/Fault_(technology))

is when something inappropriate happens to the system, such as a defect or unexpected behavior. 

A fault can lead to a **failure**, which is synonymous with a malfunction. Failure means that the system has stopped working properly. The system is no longer doing what it is supposed to do.

 A failure could lead to a **hazard**. A hazard is a situation that could cause injury to a person or harm a person's health. If a system fails, the situation is potentially hazardous. Not all failures are necessarily hazardous, which means hazards have different levels of **risk**. 

**Risk** measures the level of danger in a situation.  An example of a high risk situation is one that it is likely to happen and also cause serious injury. 

For example, if a resistor in your car radio hardware breaks, that could lead to a fault. The radio won't turn on, so the radio has failed. Does the failure lead to a hazardous situation? Probably not. You won't get to listen to music, but that won't cause you bodily injury or harm.

If a resistor in the power steering hardware breaks, the power steering could fail. If you were driving at high speed, then you might get injured quite badly. So this is a hazardous situation with high risk. 

Faults leads to failures. A failure leads to a hazard. A hazard has a certain a level of risk.
