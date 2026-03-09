# Derivation Outline

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=coHodx-I56U)

## Summary

**Summary for Real-Time Localization System**

This project aims to develop a real-time localization system that can efficiently process and update location data. The system must handle large amounts of data while maintaining a high processing rate, making it suitable for applications requiring at least 10 Hz updates.

### Key Concepts

* **Posterior Estimation**: The goal is to estimate the posterior distribution of the system's state given the input data.
* **Data Processing Overhead**: The current approach has two major issues: (1) processing a large amount of data on each cycle, and (2) an increasing amount of data over time, which makes it unsuitable for real-time applications.
* **Localizer Requirements**: A real-time localizer should be able to process updates at least 10 times per second.

### Practical Notes

The lesson will present a mathematical proof that demonstrates how to optimize the system's processing requirements. The goal is to reduce the amount of data processed on each update, making it possible for the system to handle the same amount of data regardless of drive time. This optimization will be crucial in achieving real-time localization capabilities.

Note: Unfortunately, there is no code or mathematical formulas provided in this transcript snippet. If you provide more context or a complete transcript, I can assist with adding code blocks and formulas as needed.

## Transcript

<v English>After you learn the</v>
<v English>structure of the input data,</v> <v English>I will talk more about the</v>
<v English>motivation for the following</v> <v English>videos.</v> <v English>Up to here, there</v>
<v English>are two problems</v> <v English>if we want to estimate</v>
<v English>the posterior directly.</v> <v English>The first one is the localizer</v>
<v English>must process on each cycle</v> <v English>a lot of data.</v> <v English>The second is the amount of</v>
<v English>data increases over time.</v> <v English>This won't work for</v>
<v English>real time localizer,</v> <v English>which should run with at least</v>
<v English>10 hertz in our [INAUDIBLE].</v> <v English>In the following, I will present</v>
<v English>a mathematical proof showing</v> <v English>that we can change this</v>
<v English>so our localizer, first,</v> <v English>only needs to handle a</v>
<v English>few bytes on each update,</v> <v English>and handles the same</v>
<v English>amount of data per update</v> <v English>regardless of drive time.</v> <v English>So let's start with an overview</v>
<v English>of what we want to achieve.</v>
