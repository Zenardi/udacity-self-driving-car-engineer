# Freedom from Interference - Temporal Part 2

> Part of: **Functional Safety at the Software and Hardware Levels**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=wRbGk0SwWNQ)

## Summary

**Temporal Interference and Fault Tolerance**

This project focuses on addressing temporal interference in software systems, which occurs when execution time or sequence is compromised. Temporal interference can lead to faults that violate safety goals.

### Key Concepts

* **Temporal Interference**: Occurs when software elements execute early, late, out of order, or take too long to execute.
* **Execution Time and Sequence Faults**: Can be caused by temporal interference and must be addressed to ensure system safety.
* **Fault Tolerance Mechanisms**:
	+ **Alive Supervision**: Limits the number of times a software element can execute within a given time span.
	+ **Deadline Monitoring**: Monitors execution time and triggers an error if an element takes too long.
	+ **Control Flow Monitoring**: Ensures correct order of software progress by analyzing checkpoints.

### Practical Notes

To implement fault tolerance, separate software blocks are included in the system architecture to analyze checkpoints. These blocks monitor the number of executions, execution time, and sequence order. If a fault occurs that violates safety goals, the system should transition to a safe state. This can be achieved through the use of mechanisms like alive supervision, deadline monitoring, and control flow monitoring.

**Example Code**
```markdown
// Example of alive supervision in Python
import time

def execute_element(element):
    # Monitor execution count within a given time span (e.g., 10 seconds)
    start_time = time.time()
    while True:
        if time.time() - start_time > 10:
            break
        element.execute()
```
Note: This code snippet is a simplified example and may not be production-ready.

## Transcript

<v English>Now let's discuss incorrect allocation of</v> <v English>execution time and incorrect execution sequence.</v> <v English>These types of temporal interference occur when software elements execute early,</v> <v English>late, out of order,</v> <v English>or that take too long to execute.</v> <v English>The function safety standard recommends three different mechanisms</v> <v English>for dealing with execution time and execution sequence faults.</v> <v English>They are alive supervision,</v> <v English>deadline monitoring and control flow monitoring.</v> <v English>All three of these mechanisms work with checkpoints.</v> <v English>There are software element reports its status at the beginning and end of execution.</v> <v English>A live supervision limits the number of times</v> <v English>a software element can execute within a given time span.</v> <v English>When a checkpoint is reached,</v> <v English>the system would analyze the number of times the element was executed.</v> <v English>Deadline monitoring looks at how long it takes to execute a software element.</v> <v English>If an element takes too long, an error has occurred.</v> <v English>And lastly, control flow monitoring ensures</v> <v English>that software progress is in the correct order.</v> <v English>For example, the execution sequence might be out of order or</v> <v English>a software element gets executed in</v> <v English>the middle of the sequence instead of at the beginning.</v> <v English>Separate software blocks would be included in</v> <v English>the system architecture to analyze the checkpoint.</v> <v English>If a fault occurred that violated the safety goal,</v> <v English>then the system should transition to a safe state.</v>

## Additional Content

### More Examples of Temporal Interference
