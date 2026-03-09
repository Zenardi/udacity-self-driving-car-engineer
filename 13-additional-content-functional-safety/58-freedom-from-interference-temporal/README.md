# Freedom from Interference - Temporal

> Part of: **Functional Safety at the Software and Hardware Levels**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ChGZCPXko7M)

## Summary

**Temporal Interference in Software Systems**
=============================================

Temporal interference refers to the blocking of one software element's execution by another over time. This can occur when multiple elements share resources, leading to delays or even crashes.

**Key Concepts**
---------------

* **Temporal Interference**: Blocking of one software element's execution by another over time.
* **Deadlocks**: Occur when two threads need each other's resources, creating a cycle where neither thread can proceed.
	+ Example: Thread 1 needs resource B but has resource A, while Thread 2 needs resource A but has resource B.
* **Livelocks**: Similar to deadlocks, but both threads have the courtesy to let the other go first, only to try and grab the resource simultaneously.
* **Incorrect Synchronization**: Failure to synchronize clocks or resources between software elements can lead to issues like sensor fusion problems in autonomous vehicles.
	+ Example: Radar system and camera system need synchronized clocks for accurate signal compression.

**Practical Notes**
------------------

When dealing with temporal interference, it's essential to implement safety mechanisms that take action when time-related faults occur. This may involve:

* Degraded functionality to prevent further damage
* Transitioning to a safe state to avoid safety goal violations

To mitigate temporal interference, ensure proper synchronization of clocks and resources between software elements. Use master clocks or other synchronization techniques to prevent issues like deadlocks and livelocks.

## Transcript

<v English>Temporal interference refers to one element</v> <v English>blocking the execution of another element over time.</v> <v English>For example, if two software elements share data,</v> <v English>a higher priority thread could continuously get access to</v> <v English>the data and the low priority thread would always be waiting.</v> <v English>This is called blocking of execution.</v> <v English>There are many other cases of temporal interference,</v> <v English>and we will discuss a few couple of months.</v> <v English>Deadlocks occur when two executed threads need each others resources;</v> <v English>though thread one needs resource B,</v> <v English>but has to resource A. Thread two needs resource A,</v> <v English>but has resource B.</v> <v English>A similar interference is called Livelocks.</v> <v English>Where two threads wants the same resource.</v> <v English>In this case both threads have the courtesy to let the other thread go first,</v> <v English>but they keep stepping aside and then trying to grab the resource simultaneously.</v> <v English>Another example of temporal interference</v> <v English>is incorrect synchronization between software elements.</v> <v English>For example, consider an autonomous vehicle that has</v> <v English>both a radar system and camera system for vehicle detection.</v> <v English>Each system will have its own issue.</v> <v English>But what if the clocks on the issues are not synchronized properly,</v> <v English>then sensor fusion could not be done</v> <v English>since there would be no way to compress signals over time.</v> <v English>Hence, clocks need to be synchronized or</v> <v English>all software elements need to use the same master clock.</v> <v English>When any time or executioner related fault occurs,</v> <v English>safety mechanisms need to take action.</v> <v English>This can be a degraded functionality and</v> <v English>eventual transition to a safe state to avoid safety goal violations.</v>

## Additional Content

### Solving Deadlocks

There are various algorithms for avoiding deadlocks including a measure called disabling interrupts. When interrupts are enabled, one process can interrupt another process. So in our example, thread one needs resource B and is trying to grab A. But thread two keeps interrupting thread one to grab A back. Disabling interrupts would allow thread one to grab A.


### Mechanisms for Freedom from Temporal Interference

Mechanisms to avoid temporal interference include cyclic execution scheduling, fixed priority based scheduling, time triggered scheduling, monitoring of processor execution time, program sequence monitoring, and arrival rate monitoring.
