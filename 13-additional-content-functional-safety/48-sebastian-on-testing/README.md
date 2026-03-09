# Sebastian on Testing

> Part of: **Functional Safety: Technical Safety Concept**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=30Ei-TLjYsk)

## Summary

**Regression Testing and Data Replay**

This lesson discusses the importance of regression testing in software development, specifically using historical data sets to validate changes made to the code. The instructor shares their experience with collecting and replaying data to ensure that changes do not introduce new problems.

**Key Concepts**

* **Regression testing**: a process of re-running tests on existing data after making changes to the code
* **Data replay**: the practice of re-running historical data sets through the system to validate changes
* **Historical data**: using past data sets to test and validate changes made to the software
* **Minimum exposure**: minimizing the risk of introducing new problems by testing changes on existing data

**Practical Notes**

The instructor emphasizes the importance of keeping old data sets around for testing purposes. This allows developers to re-run tests from scratch, ensuring that changes do not introduce new problems. By using historical data as a test bed, developers can minimize exposure to potential issues and make more informed decisions about code changes.

Example code or formulas are not provided in this lesson, but the concept of data replay can be applied to various programming languages and frameworks.

## Transcript

<v English>Yeah, we always collected lots of data.</v> <v English>And one of the things we did a lot was called regression testing.</v> <v English>At the time, we didn't know what the name was,</v> <v English>but it was very obvious what to do,</v> <v English>which is you collect data and we collect especially data sets if something goes wrong.</v> <v English>And then we fix what's wrong with that data,</v> <v English>we replay that data.</v> <v English>We build our software so every data set could just</v> <v English>be replayed as if the real car was running with the real processes.</v> <v English>And then we hope that the software fix would fix the problem.</v> <v English>But we wouldn't toss the data afterwards, we'd keep it.</v> <v English>And the reason is: we wanted to test,</v> <v English>not just on the most recent data,</v> <v English>but also on older data.</v> <v English>So, we would be able to say,</v> <v English>okay we fixed the problem over here,</v> <v English>but then the question would be,</v> <v English>have we maybe accidentally used a new problem?</v> <v English>And very often what happens if we fix the problem over here,</v> <v English>and then this old data set over here would completely break.</v> <v English>And it was really important to us to understand this.</v> <v English>We almost used the old data as old simulation.</v> <v English>We didn't really use simulation at the time,</v> <v English>but we wanted this old data around as a test overnight.</v> <v English>So, we would have to re-drive everything from scratch.</v> <v English>And in doing so we were able to change software carefully with</v> <v English>minimum exposure to what's working already because we're</v> <v English>always had the old data around to test of what you already built.</v>

## Additional Content

### Sebastian Talks about Using Data for Testing

Here, Sebastian discusses how the DARPA team used data to iterate and improve software.
