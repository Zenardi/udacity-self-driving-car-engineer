# More Kalman Filters

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=hUnTg5v4tDU)

## Summary

**Kalman Filter Fundamentals**
=====================================

This project explores the concept of Kalman filters and their application in estimating variables that cannot be directly observed. The goal is to understand how Kalman filters work by analyzing a simple example.

### Key Concepts

* **Gaussian distributions**: A mathematical representation of uncertainty, used to model probability distributions.
* **Tilted Gaussian**: A 2D Gaussian distribution where the location and velocity are correlated, illustrating the relationship between these two variables.
* **Prior and measurement probabilities**: The prior probability represents the initial estimate of a variable, while the measurement probability updates this estimate based on new observations.
* **Kalman filter equations**: A set of physical equations that propagate constraints from subsequent measurements back to unobservable variables, enabling estimation of hidden states.

### Practical Notes

* **Estimating velocity and location**: By combining prior estimates with measurement probabilities, Kalman filters can accurately estimate both observable (location) and hidden (velocity) variables.
* **Efficiency of Kalman filters**: Due to their efficient calculation, Kalman filters are often used in applications where multiple observations need to be processed quickly, such as in self-driving cars.

This project demonstrates the power of Kalman filters in estimating variables that cannot be directly observed. By understanding how these filters work, you can apply this knowledge to real-world problems in fields like robotics and computer vision.

## Transcript

When you put all this together, you find that all these possibilites on the Gaussian over here, link to a Gaussian that looks like this. This is a really interesting 2-dimensional Gaussian, which you should really think about. Clearly, if I were to project this Gaussian uncertainty into the space of possible locations, I can't predict a thing. It's impossible to predict where the object is. The reason is, I don't know the velocity.

Also, clearly if I project this Gaussian into the space of x dot, it is impossible to say what the velocity is. A single observation or single prediction is insufficient to make that observation. However, what we know is our location is correlated to the velocity. The faster I move, the further on the right is the location. This Gaussian expresses this.

If I, for example, figure out that my velocity was 2, then I was able, under this Gaussian, to really nail that my location is 3. That is really remarkable. You still haven't figured out where you are, and you haven't figured out how fast you're moving, but we've learned so much about the relation of these 2 things with this tilted Gaussian. To understand how powerful this is, let's now fold in the second observation at time t = 2. This observation tells us nothing about the velocity and only something about the location.

So if I were to draw this as a Gaussian--it's a Gaussian just like this, which says something about the location but not about the velocity. But if we multiply my prior from the prediction step with the measurement probability, then miraculously, I get a Gaussian that sits right over here. This Gaussian now has a really good estimate what my velocity is and a really good estimate where I am. If I take this Gaussian, and predict 1 step forward, then I find myself right over here. That's exactly the effect we have over here.

After that I get a Gaussian like this, I predict right over here. Think about this. This is a really deep insight about how Kalman filters work. In particular, we've only been able to observe 1 variable. We've been able to measure observation to infer this other variable, and the way we've been able to infer is that there's a set of physical equations which say that my location, after a times step, is my old location plus my velocity.

This set of equations has been able to propagate constraints from subsequent measurements back to this unobservable variable, velocity, so we are able to estimate the velocity as well. This is really key to understanding Kalman filter. It is key to understanding how a Google self-driving car, estimates the locations of other cars, and is able to make predictions even if it's unable to measure velocity directly. There's a big lesson here. The variables of a Kalman filter--they're often called states because they reflect states of the physical world like where the other car is and how fast it's moving.

They separate into 2 subsets--the observables, like the momentary location, and the hidden, which in our example is the velocity, which I can never directly observe. But because those 2 things interact, subsequent observations of the observable variables give us information about these hidden variables, so we can also estimate what these hidden variables are. So from multiple observations of the places of the object--the location-- we can estimate how fast it's moving. That is actually true for all of the different filters but because Kalman filters happen to be very efficient to calculate, when we have a problem like this, you tend to often use just a Kalman filter.

## Additional Content

## More Kalman Filters

There is an error in this video in the discussion between 1:52 and 2:10. The new predicted Gaussians should lie on the horizontal line x_dot = 1 instead of the diagonal line as they are drawn in the video. The reason for this is that we are assuming a model of constant velocity instead of acceleration.



In addition, the formula ```x' = x + ẋ``` shown a 2:30 should include a multiplication by time units: ```x' = x + Δtẋ'```
