# System Architecture Safety Design Patterns

> Part of: **Functional Safety at the Software and Hardware Levels**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=9q8WAW-g8jE)

## Summary

**Design Patterns for Software Architecture**
=============================================

This project explores the concept of design patterns in software architecture, specifically the E-Gas pattern used in the automotive industry. The E-Gas pattern defines three levels of software to ensure system safety and reliability.

### Key Concepts
* **E-Gas Pattern**: A proven architecture for software systems that ensures safety and reliability.
* **Three Levels of Software**:
	+ **Level 1: Functional Level**: Contains the intended functionality of the system, such as turning the wheel towards center and vibrating the steering wheel based on camera data.
	+ **Level 2: Functional Monitoring**: Monitors level 1 for any safety goal violations, such as monitoring lane assistant time and torque requests.
	+ **Level 3: Processor Monitoring**: Monitors major hardware components, including RAM, ROM, and control flow.
* **Safety Goal Violations**: If level 2 or 3 software detects an error, output from level 1 is disabled, and the system is led to a safe state.

### Practical Notes
When implementing the E-Gas pattern in your own project, consider the following:

* Define three levels of software: functional, monitoring (functional), and processor monitoring.
* Ensure that each level is designed to detect safety goal violations and lead the system to a safe state if an error occurs.
* Use the E-Gas pattern as a starting point for designing reliable and safe software systems.

Note: The code examples and formulas used in this project are not included in this summary.

## Transcript

<v English>Design Patterns are proven, well established architectures.</v> <v English>One of the most common software patterns in the automotive industry is called E-Gas.</v> <v English>An E-Gas pattern, defines three levels of software.</v> <v English>Level one is a functional level which contains the intended functionality of the system.</v> <v English>For the lane assistants example used in previous lessons,</v> <v English>the intended functionality would be,</v> <v English>to turn the wheel towards center and vibrate the steering wheel based on camera data.</v> <v English>Levels two and three of the E-Gas pattern, are for monitoring.</v> <v English>Level two refers to</v> <v English>functional monitoring which monitors level one for any safety goal violations.</v> <v English>For example, level two software,</v> <v English>would monitor the lane assistants time and</v> <v English>torque request as discussed in the previous lessons.</v> <v English>Level three is for processor monitoring of major hardware components.</v> <v English>Level three software boot, for example,</v> <v English>monitor RAM, ROM and control flow.</v> <v English>In our lane assistants example,</v> <v English>the level one software would send torque requests to the steering wheel motor.</v> <v English>If the level two or three software detects an error,</v> <v English>then output from level one is disabled and the level two or three software,</v> <v English>leads the system to a safe state.</v> <v English>In this case, we determined that the safe state would send a torque output of zero.</v>

## Additional Content

### Where does the Name E-gas Come from?

The E-gas design pattern originally comes from an acceleration drive-by-wire system. Originally the gas pedal on a car had a direct mechanical connection to the throttle valve on an engine. The throttle valve regulates how much air enters into the engine. 

In modern cars, the accelerator pedal is an electronic sensor. When you push down on the accelerator pedal, software interprets how much you want to accelerate. And then the software opens or closes the throttle valve. The E-gas software pattern was developed to monitor faults in drive-by-wire acceleration systems. In the case of a gasoline engine system failure, the level 2 or level 3 monitoring functions could lower the throttle.
### Software Partitioning and Safety Monitoring

Safety monitoring and software partitions are  software mechanisms commonly solved with design patterns. 

For safety monitoring, there are specific patterns like the E-GAS concept which was explained. In the case of software partitions, one pattern is to use a hardware feature called MPU along with dual data storage.
