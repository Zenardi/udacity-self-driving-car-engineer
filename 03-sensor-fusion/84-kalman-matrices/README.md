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

<v English>I have a new, challenging programming assignment for you that will take you a while,</v> <v English>but I would like you to implement a multidimensional Kalman filter for the example</v> <v English>I've just given you.</v> <v English>The matrix class is a class for manipulating matrices that should make it really easy.</v> <v English>It has a function that initializes matrices--I'll show you an example in a second.</v> <v English>It can set them down to 0.</v> <v English>It can compute an identity matrix.</v> <v English>It can print out a matrix with show.</v> <v English>It overloads operators like addition, subtraction,</v> <v English>multiplication, and even computes the transpose of a matrix,</v> <v English>and in some more extended code, it can actually invert a matrix</v> <v English>using Cholesky factorization.</v> <v English>There's a function here called inverse.</v> <v English>This matrix class is available.</v> <v English>It's a small version of what is found in typical libraries.</v> <v English>I want to demonstrate it for you just for a second.</v> <v English>You can make a matrix with a command like this with the argument in the parenthesis.</v> <v English>It's a 2-dimensional matrix.</v> <v English>In this case it's a vertical vector.</v> <v English>With the show command, you can print out the result of the vertical vector.</v> <v English>You can put the transpose as follows.</v> <v English>If you run this, you'll find the horizontal vector.</v> <v English>Say you wish to multiply a matrix by a vector,</v> <v English>then we can make a 2 x 2 matrix with this initialization over here,</v> <v English>a matrix of [12., 8.] and [6., 2.].</v> <v English>We can print this matrix.</v> <v English>Here it is: 12, 8, 6, 2.</v> <v English>These are these values over here.</v> <v English>And we can multiply F and a.</v> <v English>So here b = F x a.</v> <v English>And if we show the result, we get the vector 280.</v> <v English>That's obtained by 10 x 12 + 10 x 8 is 200.</v> <v English>10 x 6 + 10 x 2 is 80.</v> <v English>So using my matrix libraries, I set an initial state.</v> <v English>This is a tracking in 1D where the state is the position</v> <v English>and the velocity.</v> <v English>I initialized both with 0 because I don't know the actual location and the velocity.</v> <v English>I get an uncertainty matrix</v> <v English>where I have a really high uncertainty in the position</v> <v English>and a really high uncertainty in the velocity,</v> <v English>and they're both uncorrelated.</v> <v English>That's the matrix of 1000, 0, 0, 1000.</v> <v English>I specify an external motion, but it's 0, 0, so it has no effect,</v> <v English>so just ignore this.</v> <v English>I build the next state function, which is the one we just discussed,</v> <v English>[1., 1] [0, 1.].</v> <v English>That assumes that the velocity is just being added to the position,</v> <v English>and the velocity and expectation stays the same.</v> <v English>I build a measurement function that extracts just the first</v> <v English>of the 2 values, 1 and 0,</v> <v English>so I can observe the location but not the velocity.</v> <v English>I have a measurement uncertainty.</v> <v English>It happens to be 1 in this example.</v> <v English>And I have an identity matrix, [1., 0.] [0., 1.].</v> <v English>And then I run a filter with these 3 measurements over here,</v> <v English>and what should come out is that by running the filter,</v> <v English>I can estimate the velocity</v> <v English>and therefore make better predictions.</v> <v English>In the filter that I want you to program,</v> <v English>I want the measurement update first and then the motion update.</v> <v English>Every time we run the filter,</v> <v English>I want you to update the measurement first, then the motion.</v> <v English>Here is my empty procedure filter that we have to fill in</v> <v English>where I go through our measurements,</v> <v English>and it builds the measurement update and then the motion update,</v> <v English>the prediction, and then I just print out the resulting estimates.</v> <v English>I do this a number of times, 3 times in this case.</v> <v English>Once we fill this in and I hit the Run button,</v> <v English>I get the following output.</v> <v English>After my first measurement update,</v> <v English>I observed the location 1, which gets copied over</v> <v English>essentially to .99 over here.</v> <v English>I learn nothing about the velocity, so it's still 0, just the way I initialized it.</v> <v English>And then there's an updated uncertainty matrix</v> <v English>which now shows what happens to be a strong correlation,</v> <v English>1000, 1000, 1000, 1000.</v> <v English>That differs from the initial one only that we filled in</v> <v English>the off-diagonal elements.</v> <v English>It happens to be exactly what the Kalman filter does.</v> <v English>And then I'll observe again the 2.</v> <v English>I want the output to now tell me that my next prediction is 3.</v> <v English>It's the observation plus the prediction.</v> <v English>But now I have a really good estimate</v> <v English>on what the velocity is.</v> <v English>It's essentially 1, and the reason is</v> <v English>my Kalman filter was able to use</v> <v English>the Kalman filter equations to find this value.</v> <v English>There's a new covariance matrix,</v> <v English>and for the third observation followed by the prediction,</v> <v English>the prediction is correctly effectively 4, 3.999.</v> <v English>The velocity estimate is correctly 1, which is .99999,</v> <v English>and I have yet another uncertainty matrix which illustrates</v> <v English>I high certainty in the velocity estimate.</v> <v English>Notice a relatively high certainty in the position estimate</v> <v English>compared to my initial uncertainties.</v> <v English>So can you write the algorithm filter</v> <v English>that outputs those exact values over here?</v> <v English>This is an involved programming assignment.</v> <v English>What you have to do is you have to essentially</v> <v English>implement the equations I gave you.</v> <v English>You have to familiarize yourself with the matrix class</v> <v English>and then go and fill in the filter code</v> <v English>in accordance to the things that I showed you</v> <v English>for the multivariate Kalman filter.</v>

[Thrun] Here's my code: If you've got this correct, then I'm mightily impressed with what you've done because you've taken something that often takes many, many classes to explain to students, and within a single class, you understood the gist of it and you wrote a piece of code that is really non-trivial, that you can reuse many times, and that's the core of the Google self-driving cars' ability to check other vehicles. Here is the line by line implementation of what I've shown you before for the measurement update and the prediction, and you'll find using my matrix class that it implements step after step exactly what I've shown you. A little non-triviality. We have to make a measurement matrix of the nth measurement. If you solve the problem, you have probably something like this.

The error calculation, the matrix S with a transpose, the Kalman gain K with the inverse, back to my next prediction and my measurement update, and this is the prediction step. You can see it implements exactly what I showed you in these two equations over here. Now I know programming with this is involved, and I'm really impressed if you were able to do this. If you've done this, you've achieved something really, really major. You now understand Kalman filters, and you've implemented a multidimensional Kalman filter all on your own using a fairly mechanical matrix class that I wrote for you.

You ran it, and it's gotten really good results in which a sequence of position estimates: 1, 2, 3, led you to make a prediction and understand the velocity of the moving object. These are the equations you just implemented. Congratulations. You really understood something fundamental here that I believe is really essential to artificial intelligence and to building self-driving cars. You implemented effectively our method for finding other cars.

Let me put this in context. Here's a Google self-driving car. Here's another car. Our Google self-driving car uses radar on the front bumper that measures the distance to vehicles and also gives a noisy estimate of the velocity. And it also uses its lasers, and again, it measures the distance to other cars but no velocities.

If you take the same situation from above, here is the Google car. It is localized on a map. Here is another vehicle, and another one. Using radars and lasers, the Google car estimates the distance and the velocity of all these vehicles, and it does so using a Kalman filter. Where it feeds in range data from the laser, and it uses state spaces like this one of the relative distance in x and y and the relative velocity in x and y to get state transition matrices of the type I've just shown you to find out where these other cars are, and this is exactly what you've just learned and programmed yourself.

I didn't tell you how to extract the location of other cars from radar and laser. There's something called a correspondence problem. Sometimes you don't know which one each car is, and I won't talk in much depth about it. But you understand the gist of the solution now, and you've been able to program it. If you were in a situation like this, you can use range data like laser data and radar data and come up with a rational algorithm that takes momentary measurements of other cars and not just estimates where they are but also how fast they're moving.

That's really a tremendous feat. Congratulations on getting this far. If you got this far in my class, I promise you you've just digested the most difficult thing I have to teach you in this entire class. Congratulations.

## Additional Content

## Kalman Matrices

### Solution
