# Programming Languages

> Part of: **Functional Safety at the Software and Hardware Levels**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=KpAhkXNan7Y)

## Summary

**Choosing a Programming Language or Modeling Framework for Functional Safety**

When developing software, selecting the right programming language or modeling framework is crucial. Some languages are better suited for functional safety than others. This summary highlights key concepts related to choosing a suitable language or framework.

### Key Concepts

* **Functional Safety**: Ensures that a system operates as intended and does not pose a risk to people or the environment.
* **Programming Languages**: C, C++, and MATLAB/SIMULINK are good choices for functional safety due to their characteristics:
	+ **Unambiguous Definition of Syntax and Semantics**: Prevents errors caused by unclear language rules.
	+ **Real-Time Operating Systems**: Enables predictable and reliable system behavior.
	+ **Runtime Error Handling**: Allows for detection and recovery from errors during execution.
	+ **Modularity, Abstraction, and Object-Oriented Design**: Facilitates maintainable and scalable code.
* **Software Development Guidelines**: MISRA C and MISRA C++ are widely used guidelines that define subsets of the C and C++ languages suitable for safety-critical applications.
* **MISRA (Motor Industry Software Reliability Association)**: A set of guidelines that discuss defensive implementation techniques, language subsets, style guides, and naming conventions.

### Practical Notes

When choosing a programming language or framework, consider the characteristics mentioned above. Familiarize yourself with MISRA C and MISRA C++ guidelines to ensure your code meets safety-critical standards.

## Transcript

<v English>One of the first considerations in</v> <v English>software development is choosing a programming language or modeling framework.</v> <v English>Some are more suitable for functional safety than others.</v> <v English>C, C++, and MATLAB/SIMULINK are all good choices.</v> <v English>All of these share certain characteristics that</v> <v English>makes them appropriate for function and safety applications.</v> <v English>First, they all have an unambiguous definition of syntax and semantics.</v> <v English>Second, they all run on real time operating systems.</v> <v English>Third they all support runtime error handling.</v> <v English>Finally they support modularity,</v> <v English>abstraction, and object oriented design.</v> <v English>Function safety also requires the use of a software development guideline.</v> <v English>Two of the most common guidelines are MISRA C and MISRA C++.</v> <v English>MISRA stands for Motor Industry Software Reliability Association.</v> <v English>These guidelines define a subset of</v> <v English>the C and C++ programming languages</v> <v English>that are appropriate for safety critical applications.</v> <v English>They discuss defensive implementation techniques,</v> <v English>language subsets, style guides and naming conventions.</v>

## Additional Content

### Notes about Programming Languages

Any programming language will have both strong points and weaknesses. A strongpoint for C++ is the ability to write high-speed software with many input-output operations. On the other hand, C++ will allow you to store a floating-point number in a boolean variable. And C++ does not provide much in terms of run-time error checking.

The MISRA C++ standard discusses a subset of C++ that is appropriate to safety critical applications. The standard contains a set of rules for how to use the C++ language in automotive applications. 

### Software Tools & Software Tool Confidence Level


Automotive software engineers use a variety of tools to help develop software.

Compilers are one example of software tools. Other examples include version control software, testing tools, graphical modeling tools that automatically generate code, and tools to help ensure MISRA compliance.

The functional safety standard requires that you qualify software tools to make sure they are appropriate for safety critical applications; it is becoming more common to use software tools that automate code generation and code testing. If a testing tool has a problem, for example, then code errors could go undetected.

ISO 26262 describes a metric for measuring your confidence in your tools. The metric is called tool confidence level or TCL. 

Evaluating confidence levels takes into account two things:
* Tool Impact (TI) - Whether the tool itself could malfunction and violate a safety goal
* Tool Error Detection Capability (TD) - If the tool malfunctions, is the malfunction detected or stopped

You can then use the TI and TD metrics to calculate a tool's confidence level.Software blocks with higher ASIL require TCL1, which is the highest confidence. TCL3 is the lowest confidence rating.

Lower confidence tools with TCL2 and 3 ratings need to be qualified. Qualifying involves running the tool through rigorous testing to prove that it does not cause any errors. Software tool vendors provide qualification kits that help you test their tools in your own environment.
