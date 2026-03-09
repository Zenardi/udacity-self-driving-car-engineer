# Introduction

> Part of: **Utilizing Scan Matching**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=7on778wy_As)

## Summary

**Aligning Point Clouds with ICP and NDT**

This README file provides an overview of the key concepts and practical steps involved in aligning point clouds using Iterative Closest Point (ICP) and Normal Distributions Transform (NDT) algorithms.

### Key Concepts

* **Iterative Closest Point (ICP)**: a registration algorithm that iteratively finds the best transformation between two 3D point sets by minimizing the distance between corresponding points.
	+ Formula for calculating the transformation matrix: `H = argmin ||S(R * P - T)||^2`
* **Normal Distributions Transform (NDT)**: a registration algorithm that represents the scene as a set of Gaussian distributions and finds the best transformation by maximizing the likelihood of the observed data.
	+ Key concept: NDT uses a octree to efficiently represent the scene and reduce computational complexity.
* **Point Cloud Registration**: the process of aligning two or more 3D point clouds in space, often used in computer vision and robotics applications.

### Practical Notes

* To work with point clouds and align them using ICP and NDT algorithms, you will need to use a programming library such as PCL (Point Cloud Library) or Open3D.
* You will also need to create your own point clouds using tools like the CARLA simulator, which is used for autonomous driving simulations.

## Transcript

Welcome back. Now that you can build out the ICP and NDT algorithms yourself, we're going to start using them to align point clouds. You'll work hands-on to align point clouds with both ICP and NDT first. Then you'll even get to create some of your own point clouds and get familiar with the CARLA simulator. Let's dive in.

## Additional Content

## Introduction
Now that you can build out the ICP and NDT algorithms yourself, we’re going to start using them to align point clouds. You’ll work hands on to align point clouds with both ICP and NDT first, and then you’ll even get to create some of your own point clouds and get familiar with the CARLA simulator.
