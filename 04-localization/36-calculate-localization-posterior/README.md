# Calculate Localization Posterior

> Part of: **Markov Localization**

## Additional Content

To continue developing our intuition for this filter and prepare for later coding exercises, let's walk through calculations for determining posterior probabilities at several pseudo positions x, for a single time step.  We will start with a time step after the filter has already been initialized and run a few times.  We will cover initialization of the filter in an upcoming concept.
| pseudo_position (x) | P(location) | P(observation∣location) |Raw P(location∣observation) | Normalized P(location∣observation) |
|:------------:|:-----------------:|:--------------:|:------------:|:-----------------------:|
|       1      |      1.67E-02     |    0.00E+00    |   0.00E+00   |         0.00E+00        |
|       2      |      3.86E-02     |    6.99E-03    |   ?   |         2.59E-02        |
|       3      |      4.90E-02     |    8.52E-02    |   4.18E-03   |         4.01E-01        |
|       4      |      3.86E-02     |    ?   |   5.42E-03   |         5.21E-01        |
|       5      |      1.69E-02     |    3.13E-02    |   5.31E-04   |         5.10E-02        |
|       6      |      6.51E-03     |    9.46E-04    |   6.16E-06   |         ?        |
|       7      |      ?     |    3.87E-06    |   6.55E-08   |         6.29E-06        |
|       8      |      3.86E-02     |    0.00E+00    |   0.00E+00   |         0.00E+00        |

**Normalized P(location_observation) vs. Raw P(location|observation):** The **Raw P(location|observation)** is the result prior to dividing by the total probability of P(observation), the P(b) term (denominator) of the generalized Bayes`rule. The **normalized P(location|observation)** is the result of  after dividing by P(observation).

Remember the general form for Bayes' Rule:

$$P(a|b) = \frac{P(b|a) \, P(a)}{P(b)}$$

With respect to localization, these terms are:

1. $P(location|observation)$: This is P(a|b), the **normalized** probability of a position given an observation (posterior)  
- $P(observation|location)$: This is P(b|a), the probability of an observation given a position (likelihood)
- $P(location)$:  This is P(a), the prior probability of a position 
- $P(observation)$: This is P(b), the total probability of an observation

To determine the observation probability divide the P(posterior) by P(position):

**5.42E-3/3.86E-2 = 1.40E-1**

Show Solution

To determine the raw posterior probability multiply the P(observation|location) by P(location):

**6.99E-3 * 3.86E-2 = 2.70E-4**

Show Solution

To determine the normalized posterior probability, first sum the raw P(Posterior) to get the total:

**0.00E+00 + 2.70E-04 + 4.18E-03 + 5.42E-03 + 5.31E-04 + 6.16E-06 + 6.55E-08 + 0.00E+00 = 1.04E-02**

Next, divide the P(Posterior) by the sum:

**6.16E-06/1.04E-02 = 5.92E-4**

Show Solution

To determine the position probability  divide P(posterior) by P(observation): **3.87E-06 * 6.55E-08 = 1.69E-2**

Show Solution
