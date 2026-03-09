# Introduction

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2zmbIjHpkRM)

## Summary

**Kalman Filters: A Tour of Self-Driving Cars**

This lesson takes a unique approach to introducing Kalman filters by showcasing their application in self-driving cars. The instructor visits Stanford University's Research Center, Vale, and explores the equipment used on Junior, a self-driving car developed at the university.

### Key Concepts

* **Kalman Filter**: A mathematical algorithm that uses noisy measurements to estimate the state of a system.
* **State Estimation**: The process of determining the current state of a system based on noisy or incomplete data.
* **Noisy Measurements**: Data points that contain errors or uncertainties, which can be used as input for the Kalman filter.
* **Laser-Range Finder**: A device that uses laser light to measure distances and detect objects in its surroundings.

### Practical Notes

The instructor highlights the importance of the laser-range finder's data in providing range measurements that are essential inputs for the Kalman filter. The car's ability to spot other cars and avoid collisions relies heavily on this data, demonstrating a real-world application of Kalman filters in self-driving cars.

## Transcript

<v English>Welcome to my second class on Kalman filters.</v> <v English>I want to take you on a little tour to where it all began--Stanford University.</v> <v English>Behind me is Vale, Stanford's Research Center.</v> <v English>Let's go inside.</v> <v English>This is Junior, Standord's most recent self-driving car.</v> <v English>It's the child of Stanley, whom you can find</v> <v English>in the National Museum of American History in Washington, D.C.</v> <v English>Let me tell you something about the equipment that's on this car that makes it self-driving.</v> <v English>This rotating thing over here is a laser-range finder</v> <v English>that takes distance scans 10 times a second, about a million data points.</v> <v English>It'll be really important for the Kalman filter class I'm teaching you today.</v> <v English>It's major function is to spot other cars so you don't run into them.</v> <v English>This is the data that comes from the laser.</v> <v English>This is the car parked in the garage right now. We see the back wall.</v> <v English>These are all range measurements that tell you how far things are away,</v> <v English>and they are essential as the input to the Kalman filter that we're going to learn about today.</v>
