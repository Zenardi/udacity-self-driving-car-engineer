# Intro

> Part of: **Model Predictive Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6z8A-1kNdz8)

## Summary

**Model Predictive Control (MPC)**
=====================================

Model Predictive Control reframes the task of following a trajectory as an optimization problem. The solution to this optimization problem is the optimal trajectory.

**Key Concepts**
---------------

* **Optimization Problem**: MPC formulates the task of following a trajectory as an optimization problem, where the goal is to find the optimal actuator inputs that minimize the cost of the predicted trajectory.
* **Model Predictive Control (MPC)**: MPC involves simulating different actuator inputs, predicting the resulting trajectory, and selecting the trajectory with a minimum cost.
* **Receding Horizon Control**: This approach constantly calculates inputs over a future horizon, discarding previous predictions to adapt to changing conditions.
* **Approximate Model**: The model used in MPC is only approximate, meaning it won't match the real world exactly. Therefore, constant re-evaluation of optimal actuations is necessary.

**Practical Notes**
------------------

When implementing MPC:

* Optimize actuator inputs at each step in time to minimize the cost of the predicted trajectory.
* Implement the first set of actuation commands and discard the rest of the predicted trajectory.
* Continuously calculate a new optimal trajectory based on the updated state, rather than using the old predicted trajectory.

Note: This summary focuses on the key concepts and practical steps introduced in the lesson. For more detailed information or code examples, please refer to the original Udacity lesson video.

## Transcript

<v English>Model Predictive Control reframes the task of</v> <v English>following a trajectory as an optimization problem.</v> <v English>The solution to the optimization problem is the optimal trajectory.</v> <v English>Model Predictive Control involves simulating different actuator inputs,</v> <v English>predicting the resulting trajectory and selecting that trajectory with a minimum cost.</v> <v English>Let's look at one step in the process.</v> <v English>Imagine that we know our current state and the reference trajectory we want to follow.</v> <v English>We optimize our actuator inputs at each step in time</v> <v English>in order to minimize the cost of our predicted trajectory.</v> <v English>Once we found the lowest cost trajectory,</v> <v English>we implement the very first set of actuation commands.</v> <v English>Then, we throw away the rest of the trajectory we calculated.</v> <v English>Instead of using the old trajectory we predicted,</v> <v English>we take our new state and use that to calculate a new optimal trajectory.</v> <v English>In that sense, we are constantly calculating inputs over a future horizon.</v> <v English>That's why this approach is sometimes called Receding Horizon Control.</v> <v English>You might be wondering why we don't just carry out</v> <v English>the entire trajectory we calculated during the first pass.</v> <v English>The reason is that, our model is only approximate.</v> <v English>Despite our best efforts,</v> <v English>it won't match the real world exactly.</v> <v English>Once we perform our actuation commands,</v> <v English>our trajectory might not be exactly the same as the trajectory we predicted.</v> <v English>So, it's crucial that we constantly re-evaluate to find the optimal actuations.</v>
