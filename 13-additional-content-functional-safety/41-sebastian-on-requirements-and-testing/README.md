# Sebastian On Requirements and Testing

> Part of: **Functional Safety: Functional Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=0L2DG60xWy8)

## Summary

**Summary of Unconventional Requirements Gathering and Testing Approach**

This lesson discusses an unconventional approach to building requirements for autonomous vehicles. The instructor shares their experience with a testing team that used a unique method to identify and fix software errors.

### Key Concepts

* **Redundant Systems**: A design approach where multiple systems or components are used to ensure reliability and fault tolerance.
* **Safety Assurance**: A process of ensuring that a system meets safety requirements through various methods, including testing and validation.
* **Software Failures vs. Computer Architecture Failures**: The instructor notes that software failures were more common in autonomous vehicles than computer architecture failures.
* **Testing Team Approach**: A team of testers is sent out to test the vehicle daily, with each tester recording voice notes when an issue occurs. The recordings are then reviewed by engineers to identify and fix problems.

### Practical Notes

The lesson highlights a practical approach to testing and fixing software errors in autonomous vehicles:

* **Prioritize Fixing the Biggest Problem**: By identifying and fixing the most critical problem first, the team was able to improve the vehicle's performance significantly.
* **Iterative Improvement**: The team used an iterative process to continuously identify and fix problems, leading to a tenfold improvement in the vehicle's performance over time.

## Transcript

<v English>So we had a very unusual way to building requirements.</v> <v English>We had the car build the requirements for us.</v> <v English>I'm very well aware that there's</v> <v English>a rich literature on redundant systems and on safety assurance.</v> <v English>But at the time,</v> <v English>I felt we could get in trouble with another peer system or</v> <v English>build a better software solution for driving over intersections, or other terrain.</v> <v English>And when I looked at where were the cars most important failures,</v> <v English>they were not in the computer architecture.</v> <v English>We never really had a computer failure.</v> <v English>We've had lots, and lots,</v> <v English>and lots, and lots, of software failures.</v> <v English>So what we end up doing is we started a testing team,</v> <v English>and testing team grew into like 10-15 people team very rapidly,</v> <v English>and we send them out every day and say, "Go and test".</v> <v English>They hit a button in the car and when something happen of interest,</v> <v English>they will just hit the button,</v> <v English>record the voice and say, "Here's what I saw".</v> <v English>That stream would automatically give back to the engineers,</v> <v English>and every night engineers would look over and say,</v> <v English>"There's a mapping error, or there's a localization error,</v> <v English>or there's a software error of this type.</v> <v English>Oh my God, there's a flying stroller coming from</v> <v English>a cliff and meeting a rotten tomato halfway, that's the problem."</v> <v English>And then we would, every week,</v> <v English>trial these problems into a long list.</v> <v English>And typically there was one problem has accounted for 80% of the problems.</v> <v English>The next taking of a problem was another 15% and then it percolates all the way down.</v> <v English>And we end up just fixing the biggest problem.</v> <v English>Every time we fixed the biggest problem the car got twice as good,</v> <v English>three- four times as good.</v> <v English>And as a result, it got about,</v> <v English>I would say ten times as good every year, roughly, every year.</v>

## Additional Content

### Requirements Engineering and Testing

Here, Sebastian talks about requirements and how his team tested the vehicle for the [DARPA challenge](https://cs.stanford.edu/group/roadrunner/stanley.html). 
### Quiz: Verification versus Validation
