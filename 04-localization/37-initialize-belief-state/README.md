# Initialize Belief State

> Part of: **Markov Localization**

## Additional Content

To help develop an intuition for this filter and prepare for later coding exercises, let's walk through the process of initializing our prior belief state.  That is, what values should our initial belief state take for each possible position?  Let's say we have a 1D map extending from 0  to 25 meters.  We have landmarks at x = 5.0, 10.0, and 20.0 meters, with position standard deviation of 1.0 meter.  If we know that our car's initial position is at one of these three landmarks, how should we define our initial belief state?

Since we know that we are parked next to a landmark, we can set our probability of being next to a landmark as 1.0.  Accounting for a position precision of +/- 1.0 meters, this places our car at an initial position in the range **[4, 6]** (5 +/- 1),  **[9, 11]** (10 +/- 1), or **[19, 21]** (20 +/- 1).  All other positions, not within 1.0 meter of a landmark, are initialized to 0.  We normalize these values to a total probability of 1.0 by dividing by the total number of positions that are potentially occupied.   In this case, that is 9 positions, 3 for each landmark (the landmark position and one position on either side). This gives us a value of 1.11E-01 for positions +/- 1 from our landmarks (1.0/9).  So, our initial belief state is:

```
{0, 0, 0, 1.11E-01, 1.11E-01, 1.11E-01, 0, 0, 1.11E-01, 1.11E-01, 1.11E-01, 0, 0, 0, 0, 0, 0, 0, 1.11E-01, 1.11E-01, 1.11E-01, 0, 0, 0, 0}
```

To reinforce this concept, let's practice with a quiz.

- **map size:** 100 meters
- **landmark positions:** {8, 15, 30, 70, 80}
- **position standard deviation:** 2 meters

Assuming we are parked next to a landmark, answer the following questions about our initial belief state.

To determine the initial probability we will divide 1.0 by the total number of positions within 2 meters of a landmark.  In this case we have 5 landmarks and a position standard deviation of 2.0 meters.  This gives us 5 potentially occupied positions per landmark (the landmark position and 2 each side), yielding 25 potentially occupied positions (5 landmarks * 5 positions/landmark).

**1.0/25 = 4.00E-02** - remember to enter two decimal places!

Show Solution

In the next concept, we will implement belief state initialization in C++.
