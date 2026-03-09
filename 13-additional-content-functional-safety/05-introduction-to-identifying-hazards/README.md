# Introduction to Identifying Hazards

> Part of: **Introduction to Functional Safety**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ZzgEw7WQgTs)

## Summary

**Functional Safety Analysis**
=====================================

This project focuses on the main goal of functional safety, which is to identify and mitigate potential hazards that could cause injury or harm to people's health. The first step in functional safety analysis is to identify these hazards before they can cause any harm.

**Key Concepts**
---------------

* **Hazard Identification**: The process of identifying potential hazards that could cause injury or harm to people's health.
* **Functional Safety Analysis**: A systematic approach to identifying and mitigating potential hazards in a system or product.
* **Brainstorming**: A collaborative technique used to generate ideas and identify potential hazards through group discussion and imagination.
* **Human Errors**: Mistakes made by humans that can lead to accidents, such as equipment misuse or incorrect procedures.
* **Technology Errors**: Failures of technology or systems that can lead to accidents, such as software bugs or hardware malfunctions.
* **Human-Technology Interaction Errors**: Accidents caused by the interaction between humans and technology, such as user interface design flaws.

**Practical Notes**
-------------------

As a functional safety engineer, you will need to work with cross-functional teams to identify potential hazards through brainstorming sessions. This involves imagining different scenarios and situations that could lead to accidents. In future lessons, we will provide a more formal framework for identifying hazards, including specific techniques and tools.

Note: The code or formulas mentioned in this transcript are not applicable as it is a text-based discussion on functional safety analysis concepts.

## Transcript

<v English>We have now discussed the main goal of functional safety,</v> <v English>identifying hazards and lowering risks to acceptable level.</v> <v English>So one of the first steps in functional safety analysis is to</v> <v English>identify hazards that could cause injury or harm a person's health.</v> <v English>Vehicles have a lot of safety features that we take for granted today.</v> <v English>But many safety features such as padded dashboards, headrests,</v> <v English>and windshield glass came about because vehicles were actually causing injuries.</v> <v English>In functional safety, we want to identify hazards before they ever cause injury.</v> <v English>We do not want to wait for an injury to happen and then identify the hazards after.</v> <v English>But how do you identify these potential hazards? It takes brainstorming.</v> <v English>As a functional safety engineer,</v> <v English>you will take a cross-section of personnel from</v> <v English>your company to help out with the brainstorming process.</v> <v English>You have to imagine a lot of</v> <v English>different scenarios and situations that could lead to accidents.</v> <v English>To help you identify hazards,</v> <v English>we are going to discuss three general causes of accidents: Errors caused by humans.</v> <v English>errors from technology and errors caused by human technology interaction.</v> <v English>This is just an introduction to hazard analysis.</v> <v English>In the following lesson,</v> <v English>we will give you a more formal framework for identifying hazards.</v>

## Additional Content

### Examples of human, technology, and human-technology interaction errors

Let's go through a real-world example of each type of error and see how they lead to accidents. 


#### Human Error

In February 2016, [two trains collided head-on](https://en.wikipedia.org/wiki/Bad_Aibling_rail_accident) near Munich, Germany. Although that stretch of track had an automatic signaling system that should have stopped the trains, a human controller switched off the system because one of the trains was running late. This is an accident due to human error. As an engineer, you would try to figure out why the train controller turned off the system and what could have been done to avoid the situation.

Human error is especially important in the auto industry. In the United States, the National Highway and Transportation Safety Administration estimates that [94% of car accidents](https://crashstats.nhtsa.dot.gov/Api/Public/ViewPublication/812115) involve human error. 


The European Union also estimates about

[90% of vehicular accidents](http://www.europarl.europa.eu/RegData/etudes/BRIE/2016/573902/EPRS_BRI(2016)573902_EN.pdf)

involve human error.

### Technology Error

For an example of technology causing accidents, consider the [European Space Agency's Ariane 5 rocket](https://en.wikipedia.org/wiki/Ariane_5). The rocket exploded during its first test flight on June 4th, 1996. Engineers had reused portions of the Ariane 4 software. The rocket exploded because the Ariane 5 required a 64-bit floating point value whereas the original software expected a 16-bit signed integer.

[Software bugs](https://en.wikipedia.org/wiki/List_of_software_bugs#Transportation) are a major source of technology error throughout many industries including the car industry. An internet search of *software bugs cars* will give you a sense of how serious the issue is.
### Human-Technology Interaction Error

And finally, let's discuss how human-technology interaction causes accidents. Back in 2013, [Asiana Flight 214](https://en.wikipedia.org/wiki/Asiana_Airlines_Flight_214) crashed when landing in San Francisco. A pilot selected an incorrect autopilot mode and inadvertently switched off the auto throttle function. The plane came in for landing at a very low speed and low altitude. 

The pilots' over-reliance and misunderstanding of the automatic system contributed to the crash. The autopilot system should have included a warning telling the pilot that the automatic throttle was not maintaining enough speed. 

Whenever a human and a machine share control of a system, extra care needs to be taken when evaluating safety; the boundary between what the human is supposed to do and what the machine is supposed to do needs to be clear.

As [advanced driver-assistance systems (ADAS)](https://en.wikipedia.org/wiki/Advanced_driver-assistance_systems) become ubiquitous, human-technology interaction errors might become more prevalent. We as drivers need to understand the warning signals coming from our lane keeping assistance and automatic cruise control systems. Interfaces need to make it clear when the vehicle expects us to take over. And these needs to be analyzed as safety issues. The Asiana Flight 214 example we mentioned shows the consequences of a flawed human-technology system design.

Part of your job as a safety engineer will be to anticipate what will go wrong with a vehicle when the vehicle is still in the design phase. You will think about situations and conditions where humans, technology, and human-technology interaction can lead to dangerous situations and cause accidents. In other words, you will identify hazards.
### Errors and Self-Driving Cars

One of the aims of self-driving cars is to take humans completely out of the equation. The trade-off is that autonomous vehicle could introduce more technology errors. 

Take a machine learning algorithm as an example. What happens if a pedestrian training set does not include pedestrians in wheelchairs? The system would not count a pedestrian in a wheelchair. How accurate do our results need to be on a validation set? Who determines what the training set needs to contain? 

Autonomous vehicle technology is so new that standards like ISO 26262 do not yet even consider certain issues related to self-driving cars such as machine learning algorithms. But the principles of functional safety, which uses systems engineering to identify and lower risks, apply to autonomous vehicles as well!

Please note that the example above addresses nominal performance, which is more related to Safety of the Intended Function (SOTIF) then FuSa. The ISO 26262 committee is authoring a sister specification, ISO 21448,  to address nominal performance.
### Quiz
