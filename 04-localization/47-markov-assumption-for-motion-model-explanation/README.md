# Markov Assumption for Motion Model: Explanation

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=YFLAFptKU5E)

## Summary

**Markov Assumption and Simplifying Motion Models**
=====================================================

This README file summarizes the key concepts and practical notes from the Udacity lesson on the Markov Assumption and its application in simplifying motion models.

### Key Concepts

* **First-Order Markov Assumption**: The assumption that a state only depends on the previous state, not on any other states or observations.
	+ Example: Weather forecasting, where tomorrow's weather depends only on today's weather and past information.
* **Markov Chain**: A chain of states where each state is dependent only on the previous state.
* **Posterior Distribution**: The probability distribution of a state given all previous states and observations.
* **Transition Model**: A model that predicts the next state based on the current state.

### Practical Notes

* To apply the Markov Assumption, split the control vector into the current control and previous controls.
* Remove unnecessary conditions in the graph to simplify the motion model.
* The posterior distribution of a state only depends on the previous state, current control, and map (if used).
* The transition model predicts the next state based on the current state.

**Code Example**
```python
# Simplified motion model using Markov Assumption
def motion_model(x_t_minus_one, u_t, m):
    # Transition model
    x_t = predict_next_state(x_t_minus_one, u_t)
    
    return x_t
```
Note: This code example is a simplified representation of the concepts discussed in the lesson and is not intended to be used as-is.

## Transcript

Before we go back to our motion model and how we can simplify the relations between the states and to give them values, I want to introduce the first order Markov Assumption. Assume you want to estimate the posterior distribution of p x_t given our previous states, and you have no observations or controls. So this is a pretty simple example but it works fine to explain the Markov Assumption. You can write this distribution as the following: This relation can be represented as a chain. For example, to estimate or predict x_1, we only use x_0. To estimate x_2, we use x_1 and x_0. And finally, for x_3, we use x_2, x_1, and x_0. In this example, the Markov Assumption postulates that x_2 is the best predictor for x_3. This means, that the other states, x_1 and x_0, arts or future states, carry no additional information to predict x_3 in a better way far more accurately. We also say the state x_2 is complete. We remove the links or connectors between x_1 and x_3, and x_0 and x_3, which means x_3 is independent of x_0 and x_1, it only depends on x_2. And of course, for x_2, it is the same. This means, you can also remove this guy over here. Since we now assume, that x_t only depends on the previous state, we can rewrite the posterior in this way. So, if we want to continue this chain, which means to predict the future, we only take x_3 into consideration. An example could be a weather forecaster, the weather of tomorrow only depends on today and today includes our previous information and is uncertain, of course. As an important fact, we have to assume that we have an initial guess for x_0. So, x_0 must be initialized correctly. Let's go back to our motion model and I will show you how we can benefit from the Markov Assumption. Before I talked about the Markov assumption, I stopped here and ask you, how we can simplify the structure? Now, I will show you how the Markov Assumption can help us here. First, I split the control vector into the current control, u_t, and our previous controls. Now, let's take a look to the first term, the probability distribution of p x_t is conditioned by x_t minus one, all previous observations or controls, and the map. Here, we apply the Markov Assumption the first time, since you already know x_t minus one, set one_to_t minus one, and u 1_to_t minus one will not carry additional information to predict x_t in a better way. These values were already used to estimate x_t minus one. This means, x_t is independent of these values. Because of this fact, we can remove these two conditions in the graph. This will result in the following, and the posterior distribution of x_t only depends on x_t minus one, u_t, and the map. This term is called, the transition or system model, which predicts or which moves the previous state in the new one. And as you can see, we do not need the whole observation or control history. Here, you can also consider that the map, m, does not influence x_t. It is common practice to neglect m, but here, we keep it. The second term describes a posterior distribution of x_t minus one, given all previous observations or controls, and the map. Here, we use a Markov Assumption again. We assume that u_t tells us nothing about x_t minus one, because u_t is in the future. We ignore u_t to estimate the state, x_t minus one, and we move this condition over here. Based on this assumption, we rewrite the motion model again. After these two steps, we achieved a really, really important step. I ask you, do you know why?

## Additional Content

### Markov Assumption

A Markov process is one in which the conditional probability distribution of future states (ie the next state) is dependent only upon
the current state and not on other preceding states.  This can be expressed mathematically as:

$$P(x_t|x_{1-t},....,x_{t-i},...., x_0) = P(x_t|x_{t-1})$$

It is important to note that the current state may contain all information from preceding states. That is the case discussed in this lesson.
