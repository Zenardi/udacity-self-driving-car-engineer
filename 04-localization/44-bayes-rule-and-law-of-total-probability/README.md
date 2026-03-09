# Bayes Rule and Law of Total Probability

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=p2qfHa9G7_k)

## Summary

**Bayes' Rule for Localization Posterior**
=============================================

This project explores the application of Bayes' rule to localization posterior in robotics. The goal is to understand how to estimate the beliefs about a robot's location given observations and controls.

### Key Concepts

* **Bayes' Rule**: A mathematical formula used to update the probability of a hypothesis based on new evidence.
* **Likelihood Term**: Describes the probability distribution of an observation vector, assuming a state and previous observations are known.
* **Prior (Motion Model)**: A probability distribution of a state given all previous observations, controls, and math.
* **Normalizer (Ether)**: A term used to simplify normalization, defined as the sum of products of observation and motion model over all possible states.

### Practical Notes

The lesson discusses how to apply Bayes' rule to localization posterior in robotics. The key idea is to condition the likelihood term on previous observations and controls, and use the prior (motion model) to estimate the beliefs about a robot's location. The normalizer (Ether) is used to simplify normalization.

**Example Code**
```python
# Define observation model
def observation_model(x_t, z_t):
    # Calculate probability distribution of observation vector
    return ...

# Define motion model
def motion_model(x_t_minus_1, u_t):
    # Calculate probability distribution of state given previous observations and controls
    return ...
```
Note: This code snippet is a simplified example and not actual implementation. The goal is to illustrate the concepts discussed in the lesson.

## Transcript

<v English>Here, you can see as a result of applying Bayes' rule for the localization posterior.</v> <v English>To define the likelihood term,</v> <v English>we swapped the state and the observation at t,</v> <v English>and also take into account all other conditions.</v> <v English>The prior and the normalizer are also</v> <v English>conditioned by the previous observations or controls and the math.</v> <v English>It is totally fine here to condition</v> <v English>base rule on arbitrary random variables like the controls,</v> <v English>like our observations, and the map.</v> <v English>And please, take a look at this.</v> <v English>If you remove the additional conditions in the posterior,</v> <v English>you would end up exactly with the general Bayes' formula.</v> <v English>Recall the likelihood terms observation model,</v> <v English>which describes the probability distribution of the observation vector,</v> <v English>t. Another assumption that a state x_t are previous observations,</v> <v English>are controlled, and the map are given.</v> <v English>The prior is called a motion model.</v> <v English>It is a probability distribution of x_t given all observations from one to t minus one.</v> <v English>All controls and the math take into account that</v> <v English>no current observations are included in the motion model.</v> <v English>To simplify the normalization part,</v> <v English>we define the normalizer as Ether.</v> <v English>Ether is one of the original normalization term and this term is a sum of</v> <v English>the product of the observation and the motion model over all possible states, x_t_i.</v> <v English>This also means you only have to define</v> <v English>the observation and motion model to estimate the beliefs.</v> <v English>So, let's discuss these two terms more in detail.</v> <v English>What you see here is again the definition of the motion model.The problem here</v> <v English>is that we have no information where the car was before at time T minus one.</v> <v English>This means, no information about the previous state, x_t minus one.</v> <v English>Now, my question is,</v> <v English>what kind of rule or law can we use which will help us here?</v>
