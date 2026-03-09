# What Problem Does the UKF Solve?

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=OFb47Lu9JfM)

## Summary

**Summary of Nonlinear Functions and Unscented Transformation**

This project deals with nonlinear functions in the context of process models or measurement models. The main topic is to understand how to predict the mean and covariance of a state vector at time step k+1, given the current state vector mean x and covariance P at time step k.

**Key Concepts**

* **Nonlinear Process Models**: A process model that cannot be represented by a linear function.
* **Unscented Transformation (UT)**: A method used to approximate the predicted distribution of a nonlinear function.
* **Normal Distribution**: A probability distribution where data points are normally distributed around a mean value, often represented as an ellipse.
* **Error Ellipse**: A visualization of the covariance matrix P, representing the uncertainty of the state vector.
* **A Priori Estimation**: The estimation of the state at time step k+1, before incorporating new measurements.
* **Posterior Estimation**: The estimation of the state at time step k+1, after incorporating new measurements.

**Practical Notes**

The lesson discusses the challenges of dealing with nonlinear functions in process models or measurement models. When a process model is linear, the prediction problem can be solved using the Kalman filter. However, when the process model is nonlinear, the prediction is defined by a nonlinear function, which provides a distribution that is not normally distributed anymore. The Unscented Transformation (UT) method is introduced as an approximation to find the normal distribution that represents the real predicted distribution as close as possible.

Note: This summary focuses on the key concepts and practical notes relevant to the topic, while omitting some minor details mentioned in the transcript.

## Transcript

<v English>To deal with nonlinear functions, the</v>
<v English>UKF uses the unscented transformation.</v> <v English>Let's quickly summarize again</v>
<v English>what the problem is with</v> <v English>nonlinear process models or</v>
<v English>nonlinear measurement models.</v> <v English>Let's start again from the point where</v>
<v English>we have the state vector mean x and</v> <v English>the state covariance P a time step k.</v> <v English>What we want to do is predict the mean</v>
<v English>and the covariance to time step k+1.</v> <v English>So we have X k + 1 pipe k,</v>
<v English>and P k + 1 pipe k.</v> <v English>You haven't seen this</v>
<v English>notation system yet.</v> <v English>I want to introduce it here because</v>
<v English>it is often used in the literature or</v> <v English>on Wikipedia.</v> <v English>k pipe k means the estimation is for</v>
<v English>time step k, and</v> <v English>the measurement at time k has</v>
<v English>already been taken into account.</v> <v English>The is also called</v>
<v English>the posterior estimation.</v> <v English>k +1 pipe k means the estimation is for</v>
<v English>time k+1 but</v> <v English>the last measurement that has been</v>
<v English>taken into account was from k.</v> <v English>This is exactly what we</v>
<v English>have after the prediction.</v> <v English>And this is also called</v>
<v English>the a priori estimation.</v> <v English>Now, what do these ellipses mean?</v> <v English>They visualize the distribution</v>
<v English>of our uncertainty.</v> <v English>All points on this line have</v>
<v English>the same probability density.</v> <v English>If the uncertainty is</v>
<v English>normally distributed,</v> <v English>these points have</v>
<v English>the shape of a ellipse.</v> <v English>It is often called error ellipse.</v> <v English>It can be seen as the visualization</v>
<v English>of the covariance matrix P.</v> <v English>If the process model is linear,</v>
<v English>the prediction problem looks like this.</v> <v English>Here, Q is the covariance</v>
<v English>matrix of the process noise.</v> <v English>We can use the Kalman filter to solve</v>
<v English>this linear prediction problem.</v> <v English>How does this case look like if</v>
<v English>the process model is nonlinear?</v> <v English>Then the prediction is defined</v>
<v English>by a nonlinear function, f,</v> <v English>as we've just derived it for</v>
<v English>the CTR remodel.</v> <v English>Predicting with a nonlinear function</v>
<v English>provides a distribution which is</v> <v English>generally not normally</v>
<v English>distributed anymore.</v> <v English>Actually it's not so easy to calculate</v>
<v English>this predicted distribution.</v> <v English>Generally, it can only be</v>
<v English>calculated numerically.</v> <v English>Let's say we use some fancy</v>
<v English>algorithm which can do that, and</v> <v English>let it run for a while.</v> <v English>Then result might look like this.</v> <v English>By the way, later in the localization</v>
<v English>course you will implement an algorithm</v> <v English>that does this kind of</v>
<v English>numerical calculation.</v> <v English>It's called a fitter.</v> <v English>As you can see, this is not</v>
<v English>a normal distribution anymore.</v> <v English>Otherwise, it would be an ellipse again.</v> <v English>So the predicted state distribution</v>
<v English>is not normally distributed anymore.</v> <v English>But what the UKF does is keep going</v> <v English>as if the prediction was</v>
<v English>still normally distributed.</v> <v English>This is not an analytical path anymore.</v> <v English>Of course, it is an approximation.</v> <v English>What we want to find now</v>
<v English>is the normal distribution</v> <v English>that represents the real predicted</v>
<v English>distribution as close as possible.</v> <v English>So what we are looking for is the normal</v>
<v English>distribution that has the same mean</v> <v English>value and the same covariance matrix</v>
<v English>as the real predicted distribution.</v> <v English>And this mean value and the covariance</v>
<v English>matrix might look like this.</v> <v English>The question is, how do we find this</v>
<v English>mean vector and this covariance matrix?</v> <v English>And this is what the unscented</v>
<v English>transformation does for</v> <v English>us, as I will show you</v>
<v English>in the next video.</v>
