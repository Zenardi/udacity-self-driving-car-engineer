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

Welcome to my second class on Kalman filters.I want to take you on a little tour to where it all began--Stanford University.Behind me is Vale, Stanford's Research Center.Let's go inside.This is Junior, Standord's most recent self-driving car.It's the child of Stanley, whom you can findin the National Museum of American History in Washington, D.C.Let me tell you something about the equipment that's on this car that makes it self-driving.This rotating thing over here is a laser-range finderthat takes distance scans 10 times a second, about a million data points.It'll be really important for the Kalman filter class I'm teaching you today.It's major function is to spot other cars so you don't run into them.This is the data that comes from the laser.This is the car parked in the garage right now. We see the back wall.These are all range measurements that tell you how far things are away,and they are essential as the input to the Kalman filter that we're going to learn about today.
