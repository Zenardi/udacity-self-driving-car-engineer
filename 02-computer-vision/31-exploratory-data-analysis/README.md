# Exploratory Data Analysis

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=QCJeOVQq8BM)

## Summary

**Vision-Based Machine Learning Exploratory Data Analysis (EDA)**

This README file provides an overview of the importance of exploratory data analysis (EDA) in vision-based machine learning problems. EDA is a critical step in understanding the characteristics of a dataset, which can significantly impact the performance of machine learning models.

### Key Concepts

* **Exploratory Data Analysis (EDA)**: A process of visually assessing and understanding the characteristics of a dataset.
* **Visual Assessment**: The process of examining images in a dataset to identify patterns, variability, and anomalies.
* **Mean Pixel Values**: Numerical information that can be extracted from images, such as average brightness or color values.
* **Data Quality**: The importance of having diverse and representative data for machine learning models to perform well.

### Practical Notes

When working on vision-based machine learning problems, it's essential to spend a significant amount of time visually assessing the dataset. This involves examining images to identify patterns, variability, and anomalies in factors such as:

* Lighting conditions
* Environmental settings
* Object density

Failing to properly assess the data can lead to poor model performance. For example, training a model on daytime images only may result in underperformance in nighttime conditions.

## Transcript

When working on vision-based machine learning problem, the machine learning engineer often spend hours just looking at the images in the data set. This is a critical part of the exploratory data analysis or EDA. Whereas some information can be extracted from the data numerically, such as mean pixel values. We should spend a significant amount of time visually assessing a data set. On this slide, we can see a few characteristic of the data set.

Such as the variability in whether light, environment, and object density. Why is this step so important? Well, machine learning models are only as good as the data they are being fed. For example, a machine learning model that has been trained on day light images only will absolutely under perform in night conditions.

## Additional Content

## Exploratory Data Analysis
Machine Learning algorithms may be very sensitive to **domain shift**. This domain shift can happen at different levels:
* **weather / light conditions:** for example, an algorithm trained only on sunny images is not going to perform well when shown rainy or night-time data. 
* **sensor:** a sensor change or different processing methods will create a domain shift.
* **environment:** an algorithm trained on low intensity traffic data will not perform well on high intensity traffic data for example.
An extensive **Exploratory Data Analysis (EDA)** is critical to the success of any ML project. Why? Because during this phase, the ML engineer gets acquainted with the dataset and discovers any potential challenges with the data. The EDA is such an important part of the project that ML engineers spend a few days on it alone. For a vision problem, it requires looking at 1,000s of images in your dataset!
