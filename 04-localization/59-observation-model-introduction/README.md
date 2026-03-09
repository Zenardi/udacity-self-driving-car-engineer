# Observation Model Introduction

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=SDM1aVqRBCk)

## Summary

**Observation Model in Motion Estimation**
=============================================

The observation model is a crucial component in motion estimation, describing the probability distribution of observations given the state and other factors. This lesson builds on the previous one, where we implemented the motion model in C++. We will now delve deeper into the observation model and explore ways to simplify it.

**Key Concepts**
---------------

* **Observation Model**: Describes the probability distribution of observations (`T`) given the state (`x_t`), previous observations or controls, and the map.
* **State-Transition Model**: The relationship between the current state (`x_t`) and its unknown value can be represented as a diagram or graph, where `x_t` points to `z_t`, along with other values like controls, map, and previous observations.
* **Simplifying the Observation Model**: We discuss strategies for simplifying the observation model using assumptions from previous lessons.

**Practical Notes**
-------------------

While this lesson focuses on theoretical concepts, it's essential to remember that practical applications of the observation model involve implementing it in code. In a real-world scenario, you would need to translate these ideas into executable C++ code, taking into account factors like state transitions and observation probabilities.

## Transcript

<v English>In the previous lesson, you learned about</v> <v English>the motion model and how to implement it in C++.</v> <v English>Now I go back to the math and I will finalize the base filter.</v> <v English>As a reminder, you see here again the target function with the motion model,</v> <v English>the observation model, and our normalizer.</v> <v English>We now learn more about the observation model.</v> <v English>The observation model describes the probability distribution of the observations set, T,</v> <v English>given the state, x_t,</v> <v English>our previous observations or controls, and the map.</v> <v English>You can also represent a relationship as a diagram or graph,</v> <v English>x_t is unknown and points to z_t,</v> <v English>as well as all other values like the controls,</v> <v English>the map, and the previous observations.</v> <v English>Now my question is,</v> <v English>could you simplify the observation model using</v> <v English>one of the previous mentioned strategies or assumptions?</v>

## Additional Content

### Observation Model

$$p(z_t|x_t,z_{1:t-1},u_{1:t},m)$$

### Motion Model

$$p(x_t|z_{1:t-1},u_{1:t},m)$$

#### Quiz: Simplifying the Observation Model
