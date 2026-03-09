# Framing the Problem

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=w0wl840bOUo)

## Summary

**Framing the Problem in Machine Learning**
====================================================

This lesson covers the first step in any machine learning workflow: framing the problem. This critical step is particularly important for business-oriented applications of machine learning.

### Key Concepts
* **Business Problem Identification**: Determine if a problem can be solved using hard-coded rules or if machine learning is necessary.
* **Key Stakeholders**: Identify who cares about solving the problem and their objectives.
* **Problem Constraints**: Understand any limitations or constraints on data availability, annotation costs, and other factors.
* **Relevant Metrics**: Choose metrics that align with business goals, such as precision, recall, accuracy, or other relevant indicators.

### Practical Notes
When framing a machine learning problem, consider the following:

* Evaluate whether hard-coded rules can solve the problem before investing in machine learning.
* Identify key stakeholders and their objectives to ensure alignment with business goals.
* Assess data availability, annotation costs, and other constraints that may impact model performance.
* Choose metrics that reflect business outcomes, rather than solely focusing on model performance.

## Transcript

Let's get started with the first step in any machine learning workflow, framing the problem. This step is especially critical for business-oriented machine learning application. First of all, do we even need machine learning? A lot of problems can be solved using a hard-coded set of rules. You then need to identify the key stakeholders.

Often, machine learning is solving a business problem. Who cares about the problem that we're trying to solve? What are the constraints and objectives? Data can be a bottleneck, and it's important to understand the data pipeline. Where is the data coming from?

How much data do I have access to? Is it expensive to obtain and annotate? Finally, you need to decide on which metrics are relevant to your problem. Machine learning engineers use precision, recall, or accuracy, but this might not transit directly in a good business metric. By following these steps, you will eventually gain a good understanding of the problem you're trying to solve.

As a machine learning engineer, it is easy to solely focus on model performances, but you may need to consider other factors as well.

## Additional Content

## Framing the Problem
Unless you are taking part in a Machine Learning competition, the model's performance is rarely the only thing you care about. For example, in a self-driving car system, the model's **inference time** (the time it takes to provide a prediction) is also an important factor. A model that can digest 5 images per seconds is better than a model that can only manage one image per second, even if the second one is performing better. In this case, the inference time is also a metric to choose our model.
Understanding your data pipeline is very important because it will drive your model development. In some cases, getting new data is relatively easy but annotating them (by associating a class name for example) may be expensive. In this case, you would want to create a model that requires less data or that can work with unlabeled data.
