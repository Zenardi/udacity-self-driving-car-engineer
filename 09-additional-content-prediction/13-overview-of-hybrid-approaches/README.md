# Overview of Hybrid Approaches

> Part of: **Prediction**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=yCRvxI5wJS0)

## Summary

**Hybrid Approach to Prediction**
=====================================

This project explores the concept of combining model-based and data-driven approaches for prediction. By leveraging the strengths of both methods, a hybrid approach can produce more accurate predictions tailored to specific situations.

### Key Concepts

* **Model-Based Approaches**: Incorporate knowledge of object motion dynamics with process models and handle uncertainty using multimodal estimators.
* **Data-Driven Approaches**: Extract subtle patterns from training data, producing well-tailored predictions for specific driving situations.
* **Hybrid Approach**: Combines strengths of both model-based and data-driven approaches for optimal prediction results.
* **Classifier**: A type of machine learning algorithm used to replace the multimodal estimator in a hybrid approach.

### Practical Notes

To implement a hybrid approach, you can replace the multimodal estimator with a classifier. Specifically, you will learn about the Naive Bayes Classifier, which is a type of classifier that works well for this purpose. This project provides a foundation for understanding how to combine different prediction methods and leverage machine learning algorithms to improve accuracy.

Note: No specific code or formulas are provided in this transcript, but it sets the stage for exploring more advanced topics in prediction and classification.

## Transcript

<v English>So far you have seen that prediction can be done</v> <v English>with model based or data driven approaches and you</v> <v English>learned that model based approaches incorporate</v> <v English>our knowledge of the objects motion dynamics with process models,</v> <v English>handle uncertainty on maneuvers using multimodal estimators,</v> <v English>and you have seen that there are many ways to implement model based approaches.</v> <v English>In learning about data driven approaches you saw that there are</v> <v English>many versions of data driven approaches and that these approaches</v> <v English>can extract subtle patterns from training data which means they can</v> <v English>produce predictions which are very well tailored to a specific driving situation.</v> <v English>In practice, the best way to do prediction is often by taking</v> <v English>a hybrid approach that takes advantage of the strengths of both types of approaches.</v> <v English>Remember earlier when we talked about how model based approaches</v> <v English>combine process models with a multimodal estimator?</v> <v English>Well, the multimodal estimator could be replaced with a machine learning approach.</v> <v English>To replace that component with a machine learning approach,</v> <v English>the type of algorithm we need is a classifier.</v> <v English>In the next few slides we will talk about</v> <v English>how one such classifier known as naive based classifier works.</v>
