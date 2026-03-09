# Data Acquisition and Visualization

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=LdzReg-2zrc)

## Summary

**Machine Learning Workflow: Understanding Data**
=====================================================

The data step in the machine learning workflow is a crucial component that requires a deep understanding of where the data comes from and how it's collected. A machine learning engineer must be familiar with the sensor, labeling process, and have a solid grasp of the dataset to make informed decisions.

**Key Concepts**
---------------

* **Data-centric approach**: Machine learning engineers spend most of their time working with data, making it essential to understand its origin, collection methods, and characteristics.
* **Data pipelines**: Engineers build data pipelines to manage and process large datasets efficiently.
* **Data visualization**: Creating visual representations of the dataset helps engineers identify patterns, trends, and correlations.
* **Dataset understanding**: Familiarity with the dataset is critical for making informed decisions about model development and deployment.

**Practical Notes**
------------------

While this lesson provides an overview of the importance of data in machine learning, it does not include specific practical steps or code examples. However, engineers can apply the concepts learned here to their own projects by:

* Building a data pipeline using tools like Apache Beam or Spark
* Creating visualizations with libraries such as Matplotlib or Seaborn
* Analyzing dataset characteristics and identifying potential issues

## Transcript

We can now dive into the next step of our workflow, data. This is a critical step of any machine learning workflow. This is where a machine learning engineer will spend most of their time. We often say that the engineer must become one with the data. The engineer must understand where the data comes from, know the sensor, and be familiar with the labeling process.

Here is one secret about the job of machine learning engineer. Everything is about data. You will spend your time building data pipelines, creating data visualization, and trying to understand as much as possible about your dataset. The next sections, we'll give you a good overview of this process.

## Additional Content

## Data Acquisition and Visualization
In many cases, you will need to gather your own data but in some, you will be able to leverage Open Source datasets, such as the [Google Open Image Dataset](https://storage.googleapis.com/openimages/web/index.html). However, keep in mind the end goal and where your algorithm will be deployed or used. 

Because of something called **domain gap**, an algorithm trained on a specific dataset may not perform well on another. For example, a pedestrian detection algorithm trained on data gathered with a specific camera may not be able to accurately detect pedestrians on images captured with another camera.
