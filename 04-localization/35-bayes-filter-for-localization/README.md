# Bayes' Filter For Localization

> Part of: **Markov Localization**

## Additional Content

We can apply Bayes' Rule to vehicle localization by passing variables through Bayes' Rule for each time step, as our vehicle moves.  This is known as a Bayes' Filter for Localization.  We will cover the specific as the lesson continues, but the generalized form Bayes' Filter for Localization is shown below.  You may recognize this as being similar to a Kalman filter.  In fact, many localization filters, including the Kalman filter are special cases of Bayes' Filter.

Remember the general form for Bayes' Rule:

$$P(a|b) = \frac{P(b|a) \, P(a)}{P(b)}$$

With respect to localization, these terms are:

1.

$P(location|observation)$

: This is P(a|b), the **normalized** probability of a position given an observation (posterior). 
-

$P(observation|location)$

: This is P(b|a), the probability of an observation given a position (likelihood)
-

$P(location)$

:  This is P(a), the prior probability of a position 
-

$P(observation)$

: This is P(b), the total probability of an observation

Without going into detail yet, be aware that

$P(location)$

is determined by the motion model.  The probability returned by the motion model is the product of the transition model probability (the probability of moving from

$x_{t-1}$

-->

$x_t$

)  and the probability of the state

$x_{t-1}$

. 


Over the course of this lesson, you’ll build your own Bayes’ filter. In the next few quizzes, you’ll write code to:
1. Compute Bayes’ rule
2. Calculate Bayes' posterior for localization
3. Initialize a prior belief state
4. Create a function to initialize a prior belief state given landmarks and assumptions
