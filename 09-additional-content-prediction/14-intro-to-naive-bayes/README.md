# Intro to Naive Bayes

> Part of: **Prediction**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=AkrC_WP1MWk)

## Summary

**README: Naive Bayes Classifier for Behavior Classification**

This project introduces a simple behavior classifier called Naive Bayes, which combines a classifier with a filter to classify behaviors. The goal is to predict the probability of a person being male or female given their height and weight.

### Key Concepts

* **Naive Bayes**: A probabilistic classifier that assumes all features contribute independently.
* **Gaussian Naive Bayes**: An extension of Naive Bayes that assumes feature variables follow a Gaussian distribution.
* **Normalization factor**: A term used to normalize probabilities to ensure they sum to 1.
* **Feature selection**: The process of selecting relevant feature variables for the classification problem.
* **Prior probability**: The probability of being male or female in the overall population.

### Practical Notes

To implement a good Naive Bayes classifier, you need to:

* Select the correct feature variables for the classification problem using human intuition and feature selection algorithms.
* Identify good means and variances for different classes by either guessing them or learning from data.
* Use Naive Bayes to compute the probability of each behavior at each time step.

Example use case: predicting driver behavior at intersections using features such as speed, acceleration, and braking distance. You can use one of the models discussed earlier (not specified in this transcript) for trajectory prediction.

```python
# Example code snippet (not provided in the transcript)
import numpy as np

def naive_bayes_classifier(features):
    # Compute probabilities using Naive Bayes formula
    prob_male = ...
    prob_female = ...

    return prob_male, prob_female
```

Note: The example code snippet is not provided in the transcript and is only included for illustration purposes.

## Transcript

<v English>One strategy that is often used in hybrid approaches for</v> <v English>behavior classification is to combine a classifier with a filter.</v> <v English>We will show why.</v> <v English>For now we will introduce a simple behavior classifier, Naive Bayes.</v> <v English>Let&#39;s walk through how Naive Bayes works by using an example.</v> <v English>We are going to reason on gender using</v> <v English>statistics of two feature variables; height and weight.</v> <v English>As an output we want the probability that</v> <v English>a person is male or female given their height or weight.</v> <v English>In a Naive Bayes classifier,</v> <v English>the probability of being male given height and weight is</v> <v English>just the probability of the height given male times the probability of</v> <v English>that weight given male multiplied by the prior probability of being male something</v> <v English>close to point five divided by</v> <v English>the probability of the height and weight in the overall population.</v> <v English>The reason why this algorithm is called Naive Bayes is</v> <v English>that it assumes that all features contribute independently.</v> <v English>And while in reality there is correlation between height and weight in people.</v> <v English>In practice the independence assumption often winds up working.</v> <v English>The equation about can be simplified.</v> <v English>This term will affect both probabilities male and female in the same way.</v> <v English>It is just a normalization factor.</v> <v English>This means we can first compute this part of the equation</v> <v English>both for male and female and then compute the final probability</v> <v English>of male given height and rate and probability of female</v> <v English>given height male by normalizing them to make them sum to one.</v> <v English>The problem is all about finding these terms.</v> <v English>Often, we can assume it goes in distribution for the feature variables.</v> <v English>If you make this assumption the algorithm is then called Gaussian Naive Bayes.</v> <v English>So in practice, implementing a good Gaussian Naive Bayes classifier is all about one,</v> <v English>selecting the correct feature variables for the classification problem.</v> <v English>This is vary can use some human intuition combined with</v> <v English>feature selection algorithms to anticipate what</v> <v English>factors are relevant for a given classification situation.</v> <v English>I call her for example would not be very useful in predicting gender.</v> <v English>And two identifying some good means and variances for different classes.</v> <v English>And we can either guess these numbers or we can look at lots of data to learn them.</v> <v English>For example, if you have access to lots of data</v> <v English>about how drivers handle intersections and if you define</v> <v English>some good features which indicating tension&#39;s of drivers you could use</v> <v English>Naive Bayes to compute the probability of each behavior at each time step.</v> <v English>For the trajectory prediction part.</v> <v English>You could use one of the following models we talked about earlier.</v>
