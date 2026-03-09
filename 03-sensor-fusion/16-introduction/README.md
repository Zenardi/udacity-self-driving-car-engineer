# Introduction

> Part of: **The Lidar Sensor**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Dz-zOwhUsQo)

## Summary

**LiDAR Technology for Autonomous Driving**
=====================================

This lesson introduces LiDAR technology, a crucial component for autonomous driving. Without LiDAR sensors, fully self-driving cars may not be possible on city streets.

**Key Concepts**
---------------

* **Levels of Autonomous Driving**: Understanding the different levels of autonomy, from Level 0 (no automation) to Level 5 (full autonomy).
* **Sensor Technologies**: Familiarity with camera, LiDAR, and radar sensor technologies used in autonomous driving.
* **LiDAR Working Principle**: Understanding how LiDAR sensors work, including the **LiDAR Equation**.
* **Multiple Signal Returns**: Learning about the concept of multiple signal returns and their significance in LiDAR technology.
* **Range Images**: Understanding the structure and transformation of range images into 3D-point clouds.

**Practical Notes**
-----------------

* **Waymo Open Dataset**: Familiarity with the Waymo open dataset, including its structure and usage.
* **Course Starter Code**: Introduction to Python code for working with LiDAR data and creating 3D-point clouds.
* **LiDAR Sensor Selection Criteria**: Understanding the key factors to consider when selecting a LiDAR sensor for a project.

This lesson provides a comprehensive introduction to LiDAR technology, its applications in autonomous driving, and practical steps for working with LiDAR data.

## Transcript

Hello and welcome to this lesson on LiDAR technology. It's my pleasure to share with you some of the amazing capabilities of one of the most important enabler technologies for autonomous driving. It's my belief that without LiDAR sensors, we will most probably not see fully self-driving cars on our city streets. To get you up and running as quickly as possible so you're able to use this great sensor technology, I have prepared a selection of chapters for you, which you will encounter in this lesson. We will start with the general role of LiDAR in autonomous driving first, and in this chapter, you will learn about the various levels of autonomous driving.

You will get a brief introduction to the most important sensor technologies such as the camera, the LiDAR, and also the radar sensor, and we will also discuss some of the most important criteria which you need to consider when selecting sensors. In the second chapter, we will look at the LiDAR sensors used in Waymo vehicles. We will briefly look into the most important aspects. We will discuss the structure of the Waymo open dataset, and I will introduce you to the course starter code so that you can get started quickly with developing your own actual examples in Python. Then in the third chapter, you will deep-dive into LiDAR technology.

This is one of the more challenging chapters of this lesson in which you will learn about the LiDAR working principle, the famous LiDAR equation, and also the meaning of multiple signal returns. Also, you will get an overview of currently available LiDAR sensors in the market, and also the major differences between them. Lastly, we will go through a list of criteria which you need to consider when selecting a LiDAR sensor for a project you might be working on in your future job role. Once you know what LiDAR is all about, we will look at the concept of range images, which is a common storage format for LiDAR measurements and it's also used by Waymo in their dataset. I will show you how range images are structured and how you can transform them into the well-known colored 3D-point clouds you will surely have seen before.

Once you are able to create 3D-point clouds from raw LiDAR range measurements, you are well-prepared for the next lesson, which is about object detection in LiDAR point hot. Now that you know what's waiting for you and how the knowledge inside this lesson paves the way towards the actual midterm project. I wish you all the best and lots of fun with the coding examples and also with the exercises. See you soon in the first chapter.

## Additional Content

## Introduction
Welcome to this lesson on LiDAR technology. Without LiDAR sensors, we will most probably not see fully self-driving cars become a reality. 

In the first chapter, we will start with the general role of LiDAR in autonomous driving first. You will learn about the various levels of autonomous driving, get a brief introduction to camera, LiDAR and radar and we will discuss criteria you need to consider for sensor selection.

In the second chapter, we will look at the LiDAR sensors used in Waymo vehicles. We will briefly look into the most important technical specifications, discuss the structure of the Waymo Open Dataset and I will introduce you to the course starter code for many of the exercises. 

In the third chapter, you will focus on LiDAR technology. You will learn about the LiDAR working principle, the LiDAR equation and the meaning of multiple signal returns. Also, you will get an overview of currently available LiDAR types and the major differences between them.

We will also look at the concept of range images used in the Waymo dataset. You will learn how range images are structured and how you can transform them into 3d point-clouds.
