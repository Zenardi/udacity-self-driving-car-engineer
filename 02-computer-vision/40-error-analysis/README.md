# Error Analysis

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=j2a0oHLPMk0)

## Summary

**Model Evaluation and Error Analysis**
=====================================

This lesson focuses on the importance of evaluating your machine learning model's performance, also known as error analysis. By understanding the limitations of your model, you can use this knowledge to improve its accuracy.

### Key Concepts

* **Loss function**: a measure of how well your model is performing, with lower values indicating better performance.
* **Accuracy metrics**: measures such as accuracy, precision, and recall that help evaluate your model's performance.
* **Error analysis**: the process of identifying patterns in data points that are not being predicted correctly by your model.
* **Human baseline**: a measure of how well a human would perform on a particular task, used for comparison with your model's performance.
* **Random guessing baseline**: a measure of chance performance, used as a reference point to evaluate your model's performance.

### Practical Notes

When performing error analysis, you can use various tools and techniques:

* Sort data points by loss value to identify patterns in the worst-performing examples.
* Compare your model's performance to human and random guessing baselines to understand its limitations.
* Use images or visualizations to analyze your model's predictions and identify areas for improvement.

For example, if you're building a car detection model, you can use error analysis to:

* Identify patterns in blurry images that are not being detected correctly
* Infer potential issues with detecting smaller objects in the background

By applying these techniques, you can gain valuable insights into your model's limitations and make targeted improvements to increase its accuracy.

## Transcript

We're going to focus on the model evaluation step, also called error analysis. In this step, we will understand the limitation of our model and use these limitations to improve it. Luckily, we have multiple tools to help us. The value of the loss function and the accuracy, or whatever metrics we decided on, are great indicators of our model performances. By sorting the observation based on the loss value, we can extract patterns in the worst performing data points.

For example, we may realize that all the roundabout traffic signs have a very high loss. It is also important to keep in mind the baseline we mentioned previously. How does our model compare to the human baseline and the random guessing baseline? Let's look at the following images. We have built a car detection model and we are displaying the model's detections.

What do we learn from looking at these images? Well, first of all, it seems that our model is correctly detecting some cars but not all of them. On the left image, we can see that the cars in the blurry part of the image are not detected. This is probably because the model was not trained on blurry images and therefore never learned to recognize cars in such conditions. This is something we can fix relatively easily by adding blurry data in the training set.

Moreover, we also notice on the right image that cars in the backgrounds are not detected. We can infer that maybe our algorithm is not good at detecting smaller objects and we may need to consider a different model. Performing such error analysis gives us a great amount of information about our model's limitations.

## Additional Content

## Error Analysis
Validation set metrics are a good indicator of **global performances** of the model but we often need a finer understanding. A metric like accuracy won't tell you if a certain class of objects is always misclassified, for example. For these reasons, one must perform an in-depth error analysis before iterating on the model. 

Sorting predictions based on the metric or loss values is always a useful way to identify error patterns.
