# Overview

> Part of: **Markov Localization**

## Additional Content

## Markov Localization

Markov Localization, or Bayes Filter for Localization, is a generalized filter for localization and all other localization approaches are realizations of this approach, as we'll discuss later on. By learning how to derive and implement (coding exercises) this filter we develop intuition and methods that will help us solve any vehicle localization task, including implementation of a particle filter.  We don't know exactly where our vehicle is at any given time, but can approximate it' location.  As such, we generally think of our vehicle location as a probability distribution, each time we move, our distribution becomes more diffuse (wider).  We pass our variables (map data, observation data, and control data) into the filter to concentrate (narrow) this distribution, at each time step.  Each state prior to applying the filter represents our prior and the narrowed distribution represents our Bayes' posterior.
### Bayes' Rule

You may have learned of [Bayes' Rule](https://en.wikipedia.org/wiki/Bayes%27_theorem) before in a lesson taught by Sebastian Thrun or in statistics courses, but if not, have no fear! We will come back to it in-depth in just a short while in this lesson.
