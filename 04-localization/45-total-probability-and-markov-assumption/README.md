# Total Probability and Markov Assumption

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=9hGU7s5m8c0)

## Summary

**Law of Total Probability**
==========================

The Law of Total Probability is a fundamental concept in probability theory that helps us calculate the probability of an event occurring given multiple possible causes. In this lesson, we'll explore how to apply this rule to estimate the state of a system at a future time step.

**Key Concepts**
---------------

* **Law of Total Probability**: A formula for calculating the probability of an event given multiple possible causes.
* **Conditional Probability**: The probability of an event occurring given that another event has already occurred.
* **Motion Model**: A mathematical representation of how a system changes over time, used to predict future states.

**Practical Notes**
------------------

The Law of Total Probability can be applied to real-world problems by breaking down complex systems into smaller components and modeling their relationships. In the context of robotics or autonomous vehicles, this might involve predicting the state of a vehicle at a future time step based on its current state, motion model, and observations.

Here's an example code snippet in Python that demonstrates how to apply the Law of Total Probability:
```python
import numpy as np

def law_of_total_probability(prior_state, motion_model, observations):
    # Calculate conditional probabilities
    p_xt_given_xt_minus_1 = motion_model.predict(prior_state)
    p_obs_given_xt = observations.calculate_likelihood(prior_state)

    # Apply Law of Total Probability
    p_xt = np.sum(p_xt_given_xt_minus_1 * p_obs_given_xt)

    return p_xt
```
Note that this is a simplified example and in practice, you would need to consider many more factors when applying the Law of Total Probability.

## Transcript

<v English>In this case, the law of total probability will help you a lot,</v> <v English>so this has nothing to do with Bayes Rule.</v> <v English>You already heard about this important rule from Sebastian.</v> <v English>Do you remember? And here,</v> <v English>we can see as a result,</v> <v English>we introduce a state xt minus one and assume the state is given.</v> <v English>Then, the probability distribution of our motion model can be expressed as the</v> <v English>integral of pxt given the previous states,</v> <v English>the previous observations are controls,</v> <v English>the map multiplied by the probability distribution of</v> <v English>the previous state itself over the whole state space xt minus one.</v> <v English>For better understanding, assume you are only half p of xt and you introduce pxt minus 1.</v> <v English>Then, you would have inside the integral pxt,</v> <v English>given xt minus one and the probability distribution of pxt minus one itself.</v> <v English>And this is exactly the same as the example over here.</v> <v English>But since we have conditions in our target distribution,</v> <v English>you also have to consider them in the first and second tab.</v> <v English>So, let us represent this situation as</v> <v English>a graph to visualize the dependencies between the road blocks,</v> <v English>because of introducing xt minus one.</v> <v English>You are looking at all possible states of the previous time step</v> <v English>and then predict where the car would be in the next time step.</v> <v English>Since we also have all the other given values over here,</v> <v English>we also use this information to estimate xt.</v> <v English>The same information is also use to estimate xt minus one itself.</v> <v English>And of course, xt minus one is unknown.</v> <v English>Now, my question is,</v> <v English>could we simplify this relation by using meaningful assumptions?</v>

## Additional Content

### Law of Total Probability

$$P(B) = \sum\limits_{i-1}^{\infty} P(B|A_i)P(A_i)$$
