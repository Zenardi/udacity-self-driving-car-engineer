# What is Functional Safety?

> Part of: **Introduction to Functional Safety**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=NeUXHSv5qz8)

## Summary

**Functional Safety Fundamentals**
=====================================

This project introduces the basics of functional safety, a critical aspect of ensuring the safety of people and vehicles. The goal is to identify high-risk situations that could cause harm and find ways to mitigate those risks.

**Key Concepts**
---------------

* **Hazards**: Potential problems that could injure people or damage their health.
* **Risk Evaluation**: Assessing the likelihood and potential impact of hazards on human safety.
* **Systems Engineering**: A systematic approach to designing safe systems, testing them, and documenting designs and tests.
* **Functional Safety**: Ensuring the absence of unreasonable risks by identifying hazards, evaluating risks, and using systems engineering to lower risks.

**Practical Notes**
------------------

While this lesson provides an overview of functional safety fundamentals, it does not include any specific code or practical steps. However, it sets the stage for more in-depth exploration of systems engineering and risk mitigation strategies in subsequent lessons.

## Transcript

<v English>Now you'll start to think like</v> <v English>a functional safety engineer and</v> <v English>consider how you can be more methodical about your analysis.</v> <v English>In functional safety, your goal is to identify high risk situations that could cause</v> <v English>harm and then you find ways to lower the risk to reasonable, acceptable levels.</v> <v English>Safety then is the absence of unreasonable risks.</v> <v English>Functional safety at its most basic level involves three main things.</v> <v English>Number one, identifying potential problems</v> <v English>that could injure people or damage people's health.</v> <v English>We will call these potential problems hazards.</v> <v English>Number two, evaluating the risks of these hazards.</v> <v English>Number three, using systems engineering to lower risks to acceptable levels.</v> <v English>You ensure that hazards do not lead to accidents.</v> <v English>Systems engineering helps you figure out what your vehicle needs to do and what</v> <v English>your vehicle design needs to look like in order to remain as safe as reasonably possible.</v> <v English>In practice the third part takes the most work</v> <v English>and will be the main focus of the functional safety module.</v> <v English>Lowering risks involves designing safe systems,</v> <v English>testing your systems and documenting all designs and tests.</v> <v English>In the first lesson we will give you an overview of these three basic building blocks.</v>

## Additional Content

### The Basics of Functional Safety: Review

1. **Identify hazards** in a passenger vehicle's electronic or electric system that could cause physical injury or damage to a person's health
2. **Evaluate the risk** of the hazardous situation so that we know how much we need to lower the risk
3. Via **systems engineering**, prevent accidents from occurring by lowering risk to reasonable levels. Systems engineering helps you figure out what your vehicle needs to do and what your vehicle design needs to look like in order to remain safe.
### What Level of Risk is Reasonable?

Who gets to decide what level of risk is reasonable?

While you can never eliminate risk entirely, you will reduce risk to levels acceptable by society as a whole.

The history of seat belts provides a great example of how society measures risks.  As an aside, remember that functional safety only looks at malfunctions related to electrical and electronic systems. Although seat belts are important safety features, they would not be considered part of automotive functional safety since seat belts are mechanical devices.  For our purposes we will consider seat belts to be mechanical.  Some modern seat belts, which are not purely mechanical, and contain electrical components, would be considered part of functional safety.  

Many people consider Karl Benz to have invented the automobile around 1885. Seat-belts didn't start appearing until the 1920s when doctors began installing them in their own vehicles. It wasn't until the 1950s that car companies offered seat belts as optional equipment. And then it took until the end of the 1950s for seat belts to become standard equipment. 

In 1968, the United States passed legislation requiring all vehicles to come with safety belts. Then in 1970, Australia became the first country to require seat belt use. In 1984, New York was the first state in the United States to pass similar legislation. So it took almost a century for countries to require seat belt use.

Today, can you imagine purchasing a car with no seat belts? By the measure of contemporary society, driving without a seatbelt is an unreasonable risk. But in the past, driving without a seatbelt was considered reasonable by society's standards.

Functional safety focuses on keeping risks below society's current threshold. 
### Eliminating Risk Completely

Why are you only trying to lower risk to reasonable levels rather than eliminating all risk? Eliminating all risks would paralyze engineering, product development and testing. Ensuring that people were never injured in a car accident would, unfortunately, probably be impossible. 

On the other hand, not eliminating enough risks could lead to failed products, recalls, lawsuits or even loss of life. In the end, every company has to decide for itself how much risk to eliminate from its products.

### What does "Functional" Mean? 

The term "functional" comes from a branch of systems engineering called requirements engineering. Systems engineering separates requirements into:

*Functional requirements* - what your system is supposed to do; in other words, the system's *functions*.

*Non-functional requirements* - how the system should behave: for example, how reliable is the system? 

Functional requirements generally have the form **X system shall do Y**. For example, "The turn signal system shall turn on an indicator light telling the driver that the system is active".

Non-functional requirements have the form **X system shall be Y**. As an example: "The turn signal system shall be available when the vehicle ignition switch is in the on position". 

Functional safety looks at what happens when the system does something that it was not supposed to do, which is called a malfunction. You will be adding new engineering requirements to the vehicle design in order to ensure safe systems. 

You might notice that the word *shall* comes up quite often in the functional safety module. This is because engineering requirements almost always contain the word "shall". If you see the word *shall*, then you are probably looking at an engineering requirement.
### Quiz
