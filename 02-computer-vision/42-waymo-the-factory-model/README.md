# Waymo: The Factory Model

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=LpNARtdfOEU)

## Summary

**Factory Model of Machine Learning**
=====================================

The factory model of machine learning is a framework that describes how to build high-performance systems using data. It's a cyclical process that involves collecting and labeling data, creating models, evaluating their performance, and refining the process over time.

### Key Concepts
* **Data Set**: A collection of data used to train and evaluate machine learning models.
* **Outcome Model**: The desired result or goal of the model, which is achieved through a mapping between the data set and the outcome.
* **Cyclical Process**: The iterative process of collecting and labeling data, creating models, evaluating their performance, and refining the process over time.
* **Infrastructure Pipeline**: A system that automates the machine learning process, allowing for continuous improvement and model development.

### Practical Notes
To implement the factory model of machine learning, you'll need to:

* Collect a data set on a specific task or problem
* Send part of the data set for labeling
* Create a model using the labeled data
* Evaluate the model's performance and identify shortcomings
* Refine the process by collecting additional data or labels as needed

Note that setting up this infrastructure requires an initial investment, but it can lead to significant improvements in model performance over time.

## Transcript

The factory model of machine learning is an allegory or a framework that I think describes well how to bootstrap a system into high-performance with data. The factory really is a mapping between data set and outcome a model you want that does your job. But it's usually not quite so simple. Typically, the process is cyclical. You start by collecting a data set on a task you want, send part of it for labeling.

Take these labels and create a model. Evaluate this model, find shortcomings, and decide potentially what other data needs to be collected or labeled. Perform that, collect this version 2 of the data set and repeat. This is a environment and infrastructure in a pipeline that once established, can keep churning models for you and close this virtuous loop. In typical industry we see over many generations, your models keep getting better and better and better.

Even though it takes a non-trivial investment in setting up all this infrastructure, that it does a lot of work for you.

## Additional Content

## Waymo: The Factory Model

Waymo refers to the Machine Learning Workflow as "The Factory Model". Hear from Dragomir, Distinguished Scientist at Waymo, on their approach.
