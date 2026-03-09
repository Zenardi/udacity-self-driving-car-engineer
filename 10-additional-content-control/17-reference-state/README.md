# Reference State

> Part of: **Model Predictive Control**

## Additional Content

A good start to the cost function is to think of the error that you would like to minimize. For example, measuring the offset from the center of the lane, where the center of the lane can be called the reference, or desired, state. 

We previously captured two errors in our state vector:

$cte$

and

$e\psi$

. 

Ideally, both of these errors would be 0 - there would be no difference from the actual vehicle position and heading to the desired position and heading.

Our cost should be a function of how far these errors are from 0.

Here’s one such example of how to increment our cost at each timestep,

$t$

, over our desired time horizon (represented by total number of desired timesteps,

$N$

, below) - we want to minimize the total error accumulated over this time horizon:

```cpp
double cost = 0;
for (int t = 0; t < N; ++t) {
  cost += pow(cte[t], 2);
  cost += pow(epsi[t], 2);
}
```

This is a great start, but it’s quite not enough.
