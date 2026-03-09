# Motion Models

> Part of: **Introduction to Localization**

## Additional Content

## Motion Models

Over the next few pages, Tiffany will take you through a review of vehicle movement and motion models so that you can predict where your self-driving car will be at some future time.

Predicting motion is a big step for making a mobile robot drive itself, and as such, motion models are an important part of many localization algorithms.

For example, in Bayesian methods, motion models are used in the predictive step you'll see in the Markov Localization lesson.

After the next few pages, you'll be able to apply a bicycle model to estimate the position of the car given sensor data, such as the number of wheel turns, velocity and/or the yaw rate.

Now let's get started with some physics. In order to predict the location of a car, you need to take into account the way cars move, and for that, we have the bicycle motion model.
