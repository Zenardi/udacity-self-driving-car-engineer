# Freedom from Interference - Spatial

> Part of: **Functional Safety at the Software and Hardware Levels**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=HraIGQSxsQ0)

## Summary

**README: Software Partitioning and Interference**

Software partitioning is a technique used to ensure that different software components do not interfere with each other. This is crucial in safety-critical systems where code and data corruption can have severe consequences.

### Key Concepts

* **Spatial Freedom from Interference**: The principle of separating memory and storage between software elements to prevent code and data corruption.
* **Read, Write, and Execution Permissions**: Understanding the permissions required for each software partition to interact with others.
* **Trust Relationship**: High-level software partitions (e.g., ASIL D) should not trust low-level partitions (e.g., QM), and vice versa.
* **ASIL Levels**: Software partitions are assigned a safety integrity level (ASIL) based on their criticality, e.g., ASIL C, ASIL D, QM (Qualification Mark).
* **Pointer Addressing**: Understanding how software bugs can create pointer addresses that lead to unintended interactions between partitions.

### Practical Notes

To implement spatial freedom from interference:

1. Ensure each software partition has its own memory and storage space.
2. Configure read, write, and execution permissions for each partition based on their trust relationship.
3. Use safety-critical coding practices to prevent bugs that can create pointer addresses leading to unintended interactions.

Note: This summary focuses on the key concepts introduced in the lesson, excluding the discussion of temporal freedom from interference, which is covered in the next section.

## Transcript

<v English>Freedom from spatial interference means one software partition</v> <v English>should not change the code or data of another software partition.</v> <v English>In other words memory and storage between software elements should be separated.</v> <v English>Otherwise, code and data can become corrupted.</v> <v English>In practical terms you'll need to be mindful of read,</v> <v English>write and execution permissions.</v> <v English>Think about the relationship between software partitions as being one of trust.</v> <v English>A high element mistrust any low level element.</v> <v English>So an ASIL D could read from a QM element.</v> <v English>The ASIL D element however should minimize reading from a QM element.</v> <v English>An ASIL D could also write to a QM element.</v> <v English>But the QM element should only be able to read from ASIL</v> <v English>D. A key element should not write to the higher ASIL element.</v> <v English>Likewise, if QM elements should be able to</v> <v English>execute functions provided by an ASIL D element,</v> <v English>but as an ASIL D element would</v> <v English>not trust QM functions and would not execute a QM function.</v> <v English>As a concrete example,</v> <v English>what happens if a software bug in a QM element</v> <v English>mistakenly creates a pointer address to an ASIL C partition?</v> <v English>The QM element might then write to an ASIL C element.</v> <v English>This could lead to a safety goal violation,</v> <v English>so we should either prevent or detect it.</v> <v English>Next, let's discuss temporal freedom from interference.</v>

## Additional Content

### Freedom from Spatial Interference
### Mechanisms for Ensuring Freedom From Spatial Interference

There are a few common mechanisms for ensuring freedom from spatial interference like memory protection units and dual storage of relevant data. 

MPU is a prevention method because it stops elements from accessing memory to which they should not have access. An MPU can be programmed to set up the proper read, write and execute permissions between software elements.

Dual storage of relevant data like with a 2's complement is a detection method. With a 2's complement, you can detect that the data has changed and is no longer valid. But you can no longer use the data.

Other mechanisms to protect against memory interference include:
* Redundancy checks such as CRC to make sure data does not inadvertently change.
* Micro-controllers with memory error detection and correction capabilities
* Operating systems that allow software units to have their own virtual memory space

One mechanism mentioned was to store a [2's complement](https://www.cs.cornell.edu/~tomf/notes/cps104/twoscomp.html) of safety relevant data. A 2's complement is a way of represent negative integers in binary.

A [CRC](https://en.wikipedia.org/wiki/Cyclic_redundancy_check) (cyclic redundancy check) is a way to check if data has changed during transmission. They work by adding appending a value to the data and then ensuring that the value hasn't changed over the transmission.
Please note that for addressing deadlocks, disabling OS interrupts that would stop process preemption, is inefficient and could compromise the overall response time and system latency.  An alternative is a feature that is provided by a Real Time Operating System (RTOS) is a [priority ceiling](https://en.wikipedia.org/wiki/Priority_ceiling_protocol).
