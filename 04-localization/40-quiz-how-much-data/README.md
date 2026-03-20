# Quiz: How Much Data?

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=wzcFHAf-9lo)

## Summary

**Understanding Data Representation and Performance Consequences**
===========================================================

This lesson focuses on understanding the amount of data represented by `Z1:t` and its performance implications. The instructor uses a hypothetical scenario to illustrate the concept.

### Key Concepts
* **Observation vectors**: Each observation vector contains 100,000 data points or observations.
* **Data point size**: Each data point takes up four bytes of memory.
* **Sensor update rate**: The sensor updates at a rate of 10 Hz (hertz) for six hours.
* **Total data size**: To calculate the total amount of data contained in `Z1:t`, we need to consider the number of observations, data points per observation, and data point size.

### Practical Notes
To estimate the performance consequences of working with large datasets like `Z1:t`, consider the following:

* Calculate the total amount of data stored in memory or storage devices.
* Consider the impact on system resources (e.g., memory, processing power) when handling large datasets.
* Think about how to optimize data storage and retrieval for efficient performance.

Note: This lesson does not provide specific code examples or formulas. It focuses on conceptual understanding and practical implications of working with large datasets.

## Transcript

Before we go back to math, I want to make sure you understand how much data Z1:t represents, so you can consider what the performance consequences would be. So let's pretend that each observation vector contains 100000 data points or observations. Each of those observations may have five data points which take four bytes each. If we have been driving a car for six hours with our sensor updating at ten hertz, how much data is contained in this Z1:t?

## Additional Content

### Quiz

About how much data is in

$z_{1:t}$

?
