# Markov Assumption for Observation Model

> Part of: **Markov Localization**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=dyDjINdrIz0)

## Summary

**Markov Assumption and Observation Model**

This project focuses on implementing a localization system using a Markov assumption and an observation model. The goal is to estimate the position of a vehicle based on sensor measurements.

### Key Concepts

* **Markov Assumption**: The assumption that the current state of the system (vehicle position) depends only on its previous state, not on any earlier states.
	+ This allows us to simplify the posterior distribution and focus on the current state.
* **Observation Model**: A mathematical representation of how sensor measurements are related to the vehicle's position.
	+ The observation model is a product of individual probability distributions for each range measurement.
* **Gaussian Distribution**: Used to model the noise behavior of individual range values.
	+ The standard deviation of the Gaussian distribution represents the uncertainty in the measurement.
* **Pseudo Ranges**: Estimated true range values based on the vehicle's position and the map.

### Practical Notes

To implement the observation model, you will need to:

* Use a given `x_t` (vehicle position) and the map to estimate pseudo ranges.
* Model the noise behavior of individual range values using a Gaussian distribution with a standard deviation of one meter.
* Define the observation model as a probability distribution over normal distributions for each single range measurement.

Example code in C++ may be used to implement the observation model, but this is not provided in the transcript.

## Transcript

Here, the Markov Assumption will help us again. Since you assume you're now this tagged x_t, it doesn't really matter what the car observes and how it moves before x_t. These values were already used to estimate x_t, and that t will not benefit from these values. This means, we assume that that t is independent of all previous observations and the controls. Again, this is an example of the use of the Markov Assumption. And I can simplify our posterior distribution to p of z_t, only depends on x_t and the map. Let's take a closer look to the observation model. Do you remember that that t is or could be a vector of multiple observations? This means, we rewrite the observation model in this way. Now we assume that the noise behavior of the individual range values z_t_1 to z_t_K is independent. This also means that all observations are independent. And it allows us to represent a observation model as a product of the individual probability distributions of each single range measurement. Now the question is, how we should define the observation model forcing a range measurement? In general, there are a lot of different observation models, because we have a lot of different sensors like lidars, cameras, radars, or ultransonic sensors. And each sensor has a specific noise behavior and performance. The observation model also depends on the type of the map. You can have dense 2D or 3D grid maps or sparse feature-based maps. In our 1D example, we assume that our sensor measures that range to the n closest objects in driving direction. As shown on the right side, the car measures 90 meters to the first and 37 meters to the second object. As stated before, the objects represents the landmarks in our map. Here, we assume the observation noise can be modeled as a Gaussian with a standard deviation of one meter. We also assume that our sensor can measure in a range between zero and 100 meters. To implement observation model, you use a given x_t and the given map to estimate so called pseudo ranges. These pseudo ranges represent a true range values and as assumption, your car would stand at the specific position, x_t, and the map. For example, assume your car is standing here at position 20, and would observe five meters to the first, 11 meters to the second, 39 metres to the third, and 57 meters to the last landmark. Compared to the real observations, this position seems very unlikely, right? So observation would rather fit to a position around 40. Based on this example, the observation model for a single range measurement is defined by the probability of the following normal distribution, defined by the mean z-star_t_K and our sigma. These insights allows you to implement observation model in C++. But before you go back to the coding part, I would like to finalize the theory of the base localization further.


## Additional Content


![image](images/20-i-markov-assumption-for-observation-model-first-try_00-00-22-16_still001.png)

The Markov assumption can help us simplify the observation model.  Recall that the Markov Assumption is that the next state is dependent only upon the preceding states and that preceding state information has already been used in our state estimation.  As such, we can ignore terms in our observation model prior to $x_t$ since these values have already been accounted for in our current state and assume that t is independent of previous observations and controls.

![image](images/20-i-markov-assumption-for-observation-model-first-try_00-00-36-11_still002.png)


With these assumptions we simplify our posterior distribution such that the observations at t are dependent only on x at time t and the map.
Since $z_t$ can be a vector of multiple observations we rewrite our observation model to account for the observation models for each single range measurement.  We assume that the noise behavior of the individual range values $z_t^1$ to $z_t^k$ is independent and that our observations are independent, allowing us to represent the observation model as a product over the individual probability distributions of each single range measurement.  Now we must determine how to define the observation model for a single range measurement. 

![image](images/20-i-markov-assumption-for-observation-model-first-try_00-01-18-09_still003.png)

In general there exists a variety of observation models due to different sensor, sensor specific noise behavior and performance, and map types.  For our 1D example we assume that our sensor measures to the n closest objects in the driving direction, which represent the landmarks on our map.  We also assume that observation noise can be modeled as a Gaussian with a standard deviation of 1 meter and that our sensor can measure in a range of 0 – 100 meters. To implement the observation model we use the given state $x_t$ ,  and the given map to estimate pseudo ranges, which represent the true range values under the assumption that your car would stand at a specific position $x_t$ , on the map.   For example, if our car is standing at position 20 it would make use $x_t$ ,  and m to make pseudo range ( $z_t^*$ ) observations in the order of the first landmark to the last landmark or 5, 11, 39, and 57 meters.  Compared to our real observations ( $z_t$ = [19, 37]) the position $x_t$ ,  = 20 seems unlikely and our observation would rather fit to a position around 40.  


![image](images/20-i-markov-assumption-for-observation-model-first-try_00-03-23-08_still004.png)


Based on this example the observation model for a single range measurement is defined by the probability of the following normal distribution $p(z_t^k|x_t )\tilde\ N(z_t^k,z_t^{*k},\sigma z_t)$ where $z_t^{*k}$ is the mean.  This insight will ultimately allow us to implement the observation model in c++.
