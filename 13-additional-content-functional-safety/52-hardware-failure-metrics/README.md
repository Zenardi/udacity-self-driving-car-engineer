# Hardware Failure Metrics

> Part of: **Functional Safety at the Software and Hardware Levels**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=wlCVuAJj1xk)

## Summary

**Hardware Failure and Architectural Safety Metrics**

This summary covers the concepts of hardware failure, ASIL (Automotive Safety Integrity Level) requirements, and architectural safety metrics. It's essential to understand these topics when designing safe and reliable systems.

### Key Concepts

* **Random Hardware Failures**: These occur due to various reasons such as silicon wear-out, connection breakage, cosmic radiation, and magnetic fields.
* **ASIL (Automotive Safety Integrity Level)**: This defines the number of failures permitted within a given period of time. For example, an ASIL D element should have fewer than one failure every 100 million hours.
* **Architectural Safety Metrics**: These are metrics used to evaluate random hardware failures and include:
	+ **Single Point Fault Metric**: Measures the probability of a single fault causing a system failure.
	+ **Latent Fault Metric**: Evaluates the likelihood of a latent fault (a fault that is not immediately apparent) causing a system failure.
	+ **Probabilistic Metric for Random Hardware Failures**: Estimates the probability of random hardware failures occurring within a given time period.

### Practical Notes

* To calculate architectural safety metrics, refer to section five of the Functional Safety Standard.

## Transcript

<v English>Random hardware failures will happen. There's no way around it.</v> <v English>For example, silicon can wear out or connections can break due to thermal expansion.</v> <v English>Cosmic radiation and magnetic fields also cause hardware to fail as well.</v> <v English>The number of failures permitted within a given period of time,</v> <v English>will depend on the ASIL.</v> <v English>For example, an ASIL D element should have</v> <v English>fewer than one failure every 100 million hours.</v> <v English>Besides these hardware failure target values,</v> <v English>the function safety standard defines</v> <v English>a few random hardware metrics called architectural Safety Metrics.</v> <v English>These metrics are: the single point fault metric,</v> <v English>the latent fault metric and the probabilistic metric for random hardware failures.</v> <v English>Each ASIL has different allowable thresholds for these three metrics.</v> <v English>We won't go into the details of how to calculate them.</v> <v English>You can find more information in section five of the Functional Safety Standard.</v>

## Additional Content

Note that architectural metrics have values independent of implementation and are expressed as rates. Probabilistic Metric for Hardware Failures (PMHF) has absolute units expressed in failures per 10^9 hours.  As such PMHF is not itself an architectural metric, but is relevant to a discussion of hardware failure metrics.

It's also arguable that silicon wear-out is a systematic failure rather than random hardware failure, so it may not be considered as part of random hardware failure metrics.
### More Details about Hardware Failure Metrics

Essentially, these metrics look at the percentage of hardware failures that are covered by a safety mechanism. A safety mechanism is some functionality that either keeps the vehicle safe if a failure occurs or detects that a failure has occurred. The implication is that in a safe system, most hardware failures would be detected.

Here is an example. If the RAM fails because UV radiation causes a bit flip, a safety mechanism would either need to fix the bit flip, take the system to a safe state, and/or warn the driver of the malfunction. 

The standard considers hardware failures to be inevitable. But if they are going to happen, then ideally they should not lead to safety issues. The single point fault metric for ASIL D is greater than 99% whereas ASIL B is only greater than 90%. In other words, for ASIL D, 99% of single point faults should either be detected or be safe for a specific safety goal.

To calculate these metrics, you have to figure out which hardware failures lead to hazardous situations and which failures do not. The standard actually divides hardware failures into six different categories.

### Categories of Faults

To calculate hardware failure metrics, you need to categorize the failures into one of six categories. We will list them here for reference although we won't actually be calculating hardware failure metrics in this lesson. 

Single point fault - a fault in an element that has no safety mechanism to detect faults. The fault also leads to a violation of a safety goal. For example, a RAM fault with no safety mechanisms to correct the fault would violate a safety goal.

Residual fault -  the element has a safety mechanism to detect certain kinds of faults; however, a fault occurs that the mechanism was not designed to detect, and the fault also leads to a violation of a safety goal. For example, RAM might have an ECC (error correction code) mechanism to fix a bit flip; however, a different fault occurs because of a short circuit and the RAM has no safety mechanism for short circuits.

Latent multiple point fault- multiple point fault that goes undetected by a safety mechanism and by the driver. 

Perceived multiple point fault - multiple point fault that the driver detects because the fault causes limited vehicle functionality. Examples include a driver noticing reduced break response, or activating the headlights with no response (they don't turn on).

Detected multiple point fault - multiple point fault that a safety mechanism detects and takes the vehicle to a safe state

Safe faults - faults that do not lead to safety goal violations

An example of a multiple point fault could involve RAM and an ECC (error correction code) mechanism. ECC corrects bit flips. If the RAM contains a fault because of a bit flip, the ECC would correct the flip. If the ECC fails because of a software bug, RAM would still work correctly. If there's a bit flip and the ECC fails, then there is a multiple point fault because the bit flip will not be corrected. Both the RAM and the ECC will fail.

A cyclic redundancy check (CRC) would detect a fault in the ECC mechanism. Without a CRC, the fault would go undetected and hence be latent. With the CRC, the fault would become a detected multiple point fault. If the driver is informed about the fault like with a warning light, then this is a perceived multiple-point fault.

### Measuring Faults

How would you actually measure faults and failure rates? You can either: 
* do field tests to measure the number of failures in a given amount of time
* use pre-existing data from an equivalent or similar system
* vendors should supply data for calculating these metrics as well. 

Please note that ISO 26262 does not specify a target for random hardware failures. There is a Probabilistic Metric for Hardware Failures (PMHF) which focuses on dangerous, undetected hardware failures per safety goal. ISO 26262 suggests that PMHF values be used only in the absence of data to support targets.  [This](http://publications.lib.chalmers.se/records/fulltext/218280/218280.pdf) is an interesting paper regarding PMHF and random hardware failures.

### Sources and Types of Failures

Resistors aren't the only hardware components that can fail. Entire processing units need to be considered as well.

[Hardware registers](https://en.wikipedia.org/wiki/Hardware_register), internal RAM, controller logic as well as other components can fail. All of these failures need to be covered by safety requirements, and then allocated to an architecture and documented in a safety concept. The safety concept would discuss how these failures would be detected or avoided.
