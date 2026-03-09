# Introduction

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2o_PbJMvdZY)

## Summary

**Scan Matching Algorithms with Single Lidar Sensor**
======================================================

This README file provides a summary of the key concepts introduced in the lesson on creating scan matching algorithms using a single Lidar sensor.

**Key Concepts**
---------------

* **Iterative Closest Point (ICP)**: an algorithm that iteratively finds the closest points between two point clouds to estimate the transformation between them.
* **Normal Distributions Transform (NDT)**: a technique for registering point clouds by representing the data as a set of normal distributions and finding the optimal registration using a cost function.
* **Lidar Sensor**: a type of sensor that uses laser light to detect distances and create 3D point clouds.

**Practical Notes**
------------------

This lesson focuses on building ICP and NDT algorithms in C++ code. The exercises will guide you through implementing these algorithms from scratch, allowing you to gain hands-on experience with scan matching techniques using a single Lidar sensor.

## Transcript

Welcome back. In this lesson on creating scan matching algorithms, we'll focus on two effective algorithms that can operate with just a single Lidar sensor. Iterative Closest Point, ICP and normal distributions transform, NDT. For both, we'll first introduce the concepts behind the algorithms and then the exercises will focus on actually building these out in C plus plus code. Let's get started.

## Additional Content

## Introduction
In this lesson, you'll learn about Iterative Closest Point (ICP) and Normal Distributions Transform (NDT), two powerful scan matching algorithms. For each, we'll go through them at a conceptual level first, and then you'll get to build each algorithm from scratch in C++ code.
