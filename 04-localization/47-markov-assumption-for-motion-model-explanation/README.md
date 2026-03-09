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

<v English>Before we go back to our motion model and how we can simplify</v> <v English>the relations between the states and to give them values,</v> <v English>I want to introduce the first order Markov Assumption.</v> <v English>Assume you want to estimate the posterior distribution</v> <v English>of p x_t given our previous states,</v> <v English>and you have no observations or controls.</v> <v English>So this is a pretty simple example but it works fine to explain the Markov Assumption.</v> <v English>You can write this distribution as</v> <v English>the following: This relation can be represented as a chain.</v> <v English>For example, to estimate or predict x_1,</v> <v English>we only use x_0.</v> <v English>To estimate x_2, we use x_1 and x_0.</v> <v English>And finally, for x_3,</v> <v English>we use x_2, x_1, and x_0.</v> <v English>In this example, the Markov Assumption postulates that x_2 is the best predictor for x_3.</v> <v English>This means, that the other states, x_1 and x_0,</v> <v English>arts or future states, carry</v> <v English>no additional information to predict x_3 in a better way far more accurately.</v> <v English>We also say the state x_2 is complete.</v> <v English>We remove the links or connectors between x_1 and x_3,</v> <v English>and x_0 and x_3,</v> <v English>which means x_3 is independent of x_0 and x_1,</v> <v English>it only depends on x_2.</v> <v English>And of course, for x_2, it is the same.</v> <v English>This means, you can also remove this guy over here.</v> <v English>Since we now assume,</v> <v English>that x_t only depends on the previous state,</v> <v English>we can rewrite the posterior in this way.</v> <v English>So, if we want to continue this chain,</v> <v English>which means to predict the future,</v> <v English>we only take x_3 into consideration.</v> <v English>An example could be a weather forecaster,</v> <v English>the weather of tomorrow only depends on today and</v> <v English>today includes our previous information and is uncertain, of course.</v> <v English>As an important fact,</v> <v English>we have to assume that we have an initial guess for x_0.</v> <v English>So, x_0 must be initialized correctly.</v> <v English>Let's go back to our motion model and I will show</v> <v English>you how we can benefit from the Markov Assumption.</v> <v English>Before I talked about the Markov assumption,</v> <v English>I stopped here and ask you,</v> <v English>how we can simplify the structure?</v> <v English>Now, I will show you how the Markov Assumption can help us here.</v> <v English>First, I split the control vector into the current control,</v> <v English>u_t, and our previous controls.</v> <v English>Now, let's take a look to the first term,</v> <v English>the probability distribution of p x_t is conditioned by x_t minus one,</v> <v English>all previous observations or controls, and the map.</v> <v English>Here, we apply the Markov Assumption the first time,</v> <v English>since you already know x_t minus one,</v> <v English>set one_to_t minus one,</v> <v English>and u 1_to_t minus one will not carry</v> <v English>additional information to predict x_t in a better way.</v> <v English>These values were already used to estimate x_t minus one.</v> <v English>This means, x_t is independent of these values.</v> <v English>Because of this fact,</v> <v English>we can remove these two conditions in the graph.</v> <v English>This will result in the following,</v> <v English>and the posterior distribution of x_t only depends on x_t minus one,</v> <v English>u_t, and the map.</v> <v English>This term is called,</v> <v English>the transition or system model,</v> <v English>which predicts or which moves the previous state in the new one.</v> <v English>And as you can see,</v> <v English>we do not need the whole observation or control history.</v> <v English>Here, you can also consider that the map,</v> <v English>m, does not influence x_t.</v> <v English>It is common practice to neglect m,</v> <v English>but here, we keep it.</v> <v English>The second term describes a posterior distribution of x_t minus one,</v> <v English>given all previous observations or controls, and the map.</v> <v English>Here, we use a Markov Assumption again.</v> <v English>We assume that u_t tells us nothing about x_t minus one,</v> <v English>because u_t is in the future.</v> <v English>We ignore u_t to estimate the state,</v> <v English>x_t minus one, and we move this condition over here.</v> <v English>Based on this assumption,</v> <v English>we rewrite the motion model again.</v> <v English>After these two steps,</v> <v English>we achieved a really, really important step.</v> <v English>I ask you, do you know why?</v>

## Additional Content

### Markov Assumption

A Markov process is one in which the conditional probability distribution of future states (ie the next state) is dependent only upon
the current state and not on other preceding states.  This can be expressed mathematically as:

$$P(x_t|x_{1-t},....,x_{t-i},...., x_0) = P(x_t|x_{t-1})$$

It is important to note that the current state may contain all information from preceding states. That is the case discussed in this lesson.
