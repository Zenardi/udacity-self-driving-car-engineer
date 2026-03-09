# Sebastian and Technology Errors

> Part of: **Introduction to Functional Safety**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lw3O5Me6FRw)

## Summary

**Complexity of Bugs: A Real-World Example**
====================================================

This lesson discusses a real-world example of the complexity of bugs in software development. The instructor shares a personal anecdote about building a computing infrastructure for a car's electrical system and encountering a mysterious bug that caused alternator failures.

**Key Concepts**
---------------

* **Voltage thresholds**: Understanding how voltage levels can affect system behavior, such as when the car is running but the voltage drops below 12.5 volts.
* **Power switching**: Recognizing how systems can switch between full load and zero load rapidly, causing stress on components like alternators.
* **Digital vs. analog measurements**: Appreciating how digital instruments may smooth out rapid changes in voltage or current, making it harder to detect issues like the one described.

**Practical Notes**
------------------

* When debugging complex systems, consider using analog instruments to capture rapid changes that may be missed by digital tools.
* Be aware of how system behavior can change under different conditions, such as when the car is running but voltage levels are near a threshold.
* Don't underestimate the importance of thorough testing and measurement in identifying and resolving bugs.

## Transcript

<v English>So talk about the complexity of bugs.</v> <v English>My students built the computing infrastructure</v> <v English>for standee and computers and power systems.</v> <v English>And we had a backup battery in case</v> <v English>our main battery failed and all these wonderful things,</v> <v English>and everything worked fine.</v> <v English>For months, we would go out every day and drive the car until summer hit.</v> <v English>Summer hit, and we broke an alternator. It just was fried.</v> <v English>So we took the engine out,</v> <v English>put an alternator in,</v> <v English>kept driving. We broke another alternator.</v> <v English>We took the engine out, engine back in,</v> <v English>and it invokes on tour it gets an expensive procedure to replace alternator,</v> <v English>and to cap off another half week, alternator problem.</v> <v English>No clue what's happening.</v> <v English>Now, we measured everything.</v> <v English>We went into the system,</v> <v English>try to understand anything more about the- but the load of the alternator was just fine.</v> <v English>We couldn't find anything. And then,</v> <v English>it turned out to be one of this really bizarre bugs.</v> <v English>The students had tried to make a distinction,</v> <v English>is the car running or not,</v> <v English>and normally the car is running,</v> <v English>it supplies enough voltage that the voltage of our system exceeds 12.5 volts.</v> <v English>So they would say, if the car is running,</v> <v English>we take the power from our main car source,</v> <v English>turn it off but it is not running,</v> <v English>we take it from the spare battery, okay?</v> <v English>So the car was running.</v> <v English>It was warm, the air conditioned was full blast,</v> <v English>and even though it's running the voltage drops just</v> <v English>below 12.5 volt which told our system,</v> <v English>oh cars off, sure it's off,</v> <v English>cars off, reserve battery.</v> <v English>So our power system would go from full draw of power from the cause alternator,</v> <v English>to zero at all within a tenth of a second.</v> <v English>Now of course the moment it took the power away from the main car,</v> <v English>it recovers, and the voltage goes above 12.5 volt.</v> <v English>In which case our passes went back with the car.</v> <v English>So we effectively were switching between full load</v> <v English>and zero load 10 times a second for the alternator.</v> <v English>Now when we use digital volt meters,</v> <v English>we couldn't see it, because it will smooth it out.</v> <v English>We had to take an analog altimeter to see all these bumps and realize,</v> <v English>oh my God on average we're doing fine but in reality,</v> <v English>we're drawing 100 and 0 amp, a 100 and 0 amp,</v> <v English>a 100 and 0 amp within like,</v> <v English>10th of seconds to each other,</v> <v English>and that cause the alternators to break.</v> <v English>Again it took us forever to find this bug,</v> <v English>and I'm so glad we found it.</v>

## Additional Content

### Sebastian Thrun and Technology Errors

In the video below, Sebastian Thrun discusses a technology error he encountered when building [Stanley for the DARPA challenge](https://cs.stanford.edu/group/roadrunner/stanley.html).
