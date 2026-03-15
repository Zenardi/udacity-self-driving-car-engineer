# Kalman Matrices

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ade97UKqSIc)

## Summary

**Multidimensional Kalman Filter Implementation**
=============================================

This project involves implementing a multidimensional Kalman filter using a provided matrix class. The goal is to estimate the position and velocity of an object based on noisy measurements.

**Key Concepts**
---------------

* **Kalman Filter**: A mathematical algorithm for estimating the state of a system from noisy measurements.
* **Matrix Class**: A class for manipulating matrices, including initialization, setting to zero, computing identity matrix, printing, addition, subtraction, multiplication, and transpose operations.
* **Cholesky Factorization**: An algorithm used by the matrix class to invert a matrix.
* **Kalman Gain (K)**: A matrix that represents the optimal estimate of the state given noisy measurements.
* **State Transition Matrix (F)**: A matrix that describes how the system's state evolves over time.
* **Measurement Update**: The process of updating the state estimate based on new measurements.
* **Prediction**: The process of predicting the next state of the system.

**Practical Notes**
------------------

The provided code implements a multidimensional Kalman filter using the measurement update and prediction steps. The matrix class is used to perform various operations, including matrix multiplication and inversion.

To implement the Kalman filter, you will need to:

1. Initialize the state and uncertainty matrices.
2. Define the state transition matrix (F) and measurement matrix (H).
3. Compute the Kalman gain (K) using the Cholesky factorization algorithm.
4. Perform the measurement update step.
5. Perform the prediction step.

The goal is to estimate the position and velocity of an object based on noisy measurements, and to demonstrate a working implementation of a multidimensional Kalman filter.

**Example Use Case**
-------------------

A Google self-driving car uses a Kalman filter to estimate the distance and velocity of other vehicles on the road. The car uses radar and laser data to make measurements, which are then used to update the state estimate. The Kalman filter is essential for building self-driving cars that can safely navigate complex environments.

**Implementation Details**
-------------------------

The implementation involves filling in the `filter` procedure with the measurement update and prediction steps. You will need to use the matrix class to perform various operations, including matrix multiplication and inversion. The goal is to produce a working implementation of a multidimensional Kalman filter that can estimate the position and velocity of an object based on noisy measurements.

Note: This summary is based on the provided transcript from the Udacity lesson video.

## Transcript

I have a new, challenging programming assignment for you that will take you a while, but I would like you to implement a multidimensional Kalman filter for the example I've just given you. The matrix class is a class for manipulating matrices that should make it really easy. It has a function that initializes matrices--I'll show you an example in a second. It can set them down to 0. It can compute an identity matrix. It can print out a matrix with show. It overloads operators like addition, subtraction, multiplication, and even computes the transpose of a matrix, and in some more extended code, it can actually invert a matrix using Cholesky factorization. There's a function here called inverse. This matrix class is available. It's a small version of what is found in typical libraries. I want to demonstrate it for you just for a second. You can make a matrix with a command like this with the argument in the parenthesis. It's a 2-dimensional matrix. In this case it's a vertical vector. With the show command, you can print out the result of the vertical vector. You can put the transpose as follows. If you run this, you'll find the horizontal vector. Say you wish to multiply a matrix by a vector, then we can make a 2 x 2 matrix with this initialization over here, a matrix of [12., 8.] and [6., 2.]. We can print this matrix. Here it is: 12, 8, 6, 2. These are these values over here. And we can multiply F and a. So here b = F x a. And if we show the result, we get the vector 280. That's obtained by 10 x 12 + 10 x 8 is 200. 10 x 6 + 10 x 2 is 80. So using my matrix libraries, I set an initial state. This is a tracking in 1D where the state is the position and the velocity. I initialized both with 0 because I don't know the actual location and the velocity. I get an uncertainty matrix where I have a really high uncertainty in the position and a really high uncertainty in the velocity, and they're both uncorrelated. That's the matrix of 1000, 0, 0, 1000. I specify an external motion, but it's 0, 0, so it has no effect, so just ignore this. I build the next state function, which is the one we just discussed, [1., 1] [0, 1.]. That assumes that the velocity is just being added to the position, and the velocity and expectation stays the same. I build a measurement function that extracts just the first of the 2 values, 1 and 0, so I can observe the location but not the velocity. I have a measurement uncertainty. It happens to be 1 in this example. And I have an identity matrix, [1., 0.] [0., 1.]. And then I run a filter with these 3 measurements over here, and what should come out is that by running the filter, I can estimate the velocity and therefore make better predictions. In the filter that I want you to program, I want the measurement update first and then the motion update. Every time we run the filter, I want you to update the measurement first, then the motion. Here is my empty procedure filter that we have to fill in where I go through our measurements, and it builds the measurement update and then the motion update, the prediction, and then I just print out the resulting estimates. I do this a number of times, 3 times in this case. Once we fill this in and I hit the Run button, I get the following output. After my first measurement update, I observed the location 1, which gets copied over essentially to .99 over here. I learn nothing about the velocity, so it's still 0, just the way I initialized it. And then there's an updated uncertainty matrix which now shows what happens to be a strong correlation, 1000, 1000, 1000, 1000. That differs from the initial one only that we filled in the off-diagonal elements. It happens to be exactly what the Kalman filter does. And then I'll observe again the 2. I want the output to now tell me that my next prediction is 3. It's the observation plus the prediction. But now I have a really good estimate on what the velocity is. It's essentially 1, and the reason is my Kalman filter was able to use the Kalman filter equations to find this value. There's a new covariance matrix, and for the third observation followed by the prediction, the prediction is correctly effectively 4, 3.999. The velocity estimate is correctly 1, which is .99999, and I have yet another uncertainty matrix which illustrates I high certainty in the velocity estimate. Notice a relatively high certainty in the position estimate compared to my initial uncertainties. So can you write the algorithm filter that outputs those exact values over here? This is an involved programming assignment. What you have to do is you have to essentially implement the equations I gave you. You have to familiarize yourself with the matrix class and then go and fill in the filter code in accordance to the things that I showed you for the multivariate Kalman filter.

Here's my code: If you've got this correct, then I'm mightily impressed with what you've done because you've taken something that often takes many, many classes to explain to students, and within a single class, you understood the gist of it and you wrote a piece of code that is really non-trivial, that you can reuse many times, and that's the core of the Google self-driving cars' ability to check other vehicles. Here is the line by line implementation of what I've shown you before for the measurement update and the prediction, and you'll find using my matrix class that it implements step after step exactly what I've shown you. A little non-triviality. We have to make a measurement matrix of the nth measurement. If you solve the problem, you have probably something like this.

The error calculation, the matrix S with a transpose, the Kalman gain K with the inverse, back to my next prediction and my measurement update, and this is the prediction step. You can see it implements exactly what I showed you in these two equations over here. Now I know programming with this is involved, and I'm really impressed if you were able to do this. If you've done this, you've achieved something really, really major. You now understand Kalman filters, and you've implemented a multidimensional Kalman filter all on your own using a fairly mechanical matrix class that I wrote for you.

You ran it, and it's gotten really good results in which a sequence of position estimates: 1, 2, 3, led you to make a prediction and understand the velocity of the moving object. These are the equations you just implemented. Congratulations. You really understood something fundamental here that I believe is really essential to artificial intelligence and to building self-driving cars. You implemented effectively our method for finding other cars.

Let me put this in context. Here's a Google self-driving car. Here's another car. Our Google self-driving car uses radar on the front bumper that measures the distance to vehicles and also gives a noisy estimate of the velocity. And it also uses its lasers, and again, it measures the distance to other cars but no velocities.

If you take the same situation from above, here is the Google car. It is localized on a map. Here is another vehicle, and another one. Using radars and lasers, the Google car estimates the distance and the velocity of all these vehicles, and it does so using a Kalman filter. Where it feeds in range data from the laser, and it uses state spaces like this one of the relative distance in x and y and the relative velocity in x and y to get state transition matrices of the type I've just shown you to find out where these other cars are, and this is exactly what you've just learned and programmed yourself.

I didn't tell you how to extract the location of other cars from radar and laser. There's something called a correspondence problem. Sometimes you don't know which one each car is, and I won't talk in much depth about it. But you understand the gist of the solution now, and you've been able to program it. If you were in a situation like this, you can use range data like laser data and radar data and come up with a rational algorithm that takes momentary measurements of other cars and not just estimates where they are but also how fast they're moving.

That's really a tremendous feat. Congratulations on getting this far. If you got this far in my class, I promise you you've just digested the most difficult thing I have to teach you in this entire class. Congratulations.


