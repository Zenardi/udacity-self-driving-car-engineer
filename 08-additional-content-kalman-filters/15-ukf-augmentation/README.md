# UKF Augmentation

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=G-kdutCM1RQ)

## Summary

**README: Sigma Point Generation and Augmentation in UKF**

This project implements the sigma point generation algorithm for Unscented Kalman Filter (UKF) in C++. The main topic of this project is to represent the uncertainty of the posterior state estimation with sigma points, considering both process noise and measurement noise.

**Key Concepts**

* **Sigma Points**: A set of weighted sample points used to approximate a probability distribution.
* **Process Noise Vector**: A vector that represents the influence of process noise on the state between two time steps. It can be either a vector listing individual independent noise processes or a vector describing the effect of these noise processes on the state vector.
* **Covariance Matrix Q**: The covariance matrix of the process noise, which is used to calculate the variances and co-variances of the noise processes.
* **Augmentation**: A technique used to represent the uncertainty of the covariance matrix Q with sigma points. It involves building an augmented state by adding the noise vector to the state vector and generating additional sigma points to represent the uncertainty caused by the process noise.

**Practical Notes**

To implement the sigma point generation algorithm for UKF, you need to:

* Define the process noise vector and its covariance matrix Q.
* Build the augmented state by adding the noise vector to the state vector.
* Generate 15 sigma points using the augmented elements as input. The additional four sigma points will represent the uncertainty caused by the process noise.

Note: This project assumes that you have already implemented the sigma point generation algorithm for UKF without considering Q. You will need to adapt your existing function to generate sigma points with augmentation.

## Transcript

<v English>You implemented the sigma point generation in C plus plus.</v> <v English>That's very good, because it's</v> <v English>a great preparation for the project at the end of this module.</v> <v English>Now you know how to represent the uncertainty of</v> <v English>the posterior state estimation with sigma points,</v> <v English>and we can put the sigma points into the process function.</v> <v English>But wait a second, the process function also considers the process noise vector mu k,</v> <v English>and this also has a nonlinear effect.</v> <v English>Fortunately, the UKF provides a super easy way,</v> <v English>to handle nonlinear process noise effects,</v> <v English>and this is what I want to show you in this video.</v> <v English>Let's look into this process noise again.</v> <v English>This is the complete process model,</v> <v English>considering the process noise vector.</v> <v English>Looking at this, some of you might think,</v> <v English>wait a second didn't we say this type of vector is the process vector mu k?</v> <v English>Yes, you're absolutely right.</v> <v English>In the last lesson about the common filter,</v> <v English>this was what we called mu k,</v> <v English>and that made a big difference because,</v> <v English>you had to calculate this big process noise covariance matrix Q.</v> <v English>The thing is, if you look into literature and you find this process noise vector mu k,</v> <v English>you really have to be careful what the author's mean.</v> <v English>Sometimes, they mean this vector.</v> <v English>Each row of this vector,</v> <v English>tells the influence of the process noise,</v> <v English>on a specific state between k and k plus one.</v> <v English>So, it has the same dimension as the state vector,</v> <v English>and it depends on delta t. Mostly,</v> <v English>this is the case when you read about the standard linear common filter.</v> <v English>But sometimes the author's mean this vector.</v> <v English>This is something much simpler because this vector just</v> <v English>lists the individual independent noise processes.</v> <v English>This vector doesn't say anything about</v> <v English>the effect of these noise processes on the state vector,</v> <v English>and it does not depend on delta t. Usually,</v> <v English>this is what authors mean when they write about the unscented common filter.</v> <v English>This is you confuse me a lot when I started getting into common filters.</v> <v English>So, in this lesson about the UKF,</v> <v English>when I mentioned UK,</v> <v English>I'm always talking about this process noise vector,</v> <v English>and this is a good thing because,</v> <v English>the covariance matrix Q of this process noise,</v> <v English>is much simpler in this case.</v> <v English>To write down this matrix,</v> <v English>you just need to know the stochastic properties of</v> <v English>these noise processes which we already defined.</v> <v English>Then Q is given by this matrix.</v> <v English>This matrix contains the variances of the noise processes.</v> <v English>The co-variances here is zero,</v> <v English>because the longitudinal acceleration noise</v> <v English>and the yaw acceleration noise are considered independent.</v> <v English>Now, we clarified what this process noise vector is,</v> <v English>and what its covariance matrix Q looks like.</v> <v English>What I want to show you now,</v> <v English>is how you can represent the uncertainty of the covariance matrix Q, with sigma points.</v> <v English>The solution is called augmentation.</v> <v English>This is an overview on how we generated sigma points without considering Q.</v> <v English>What we will do now is,</v> <v English>build the augmented state,</v> <v English>where we add the noise vector to the state vector,</v> <v English>I call this state XA.</v> <v English>The augmented state dimension in our case is seven.</v> <v English>This also means we need 15 sigma points now.</v> <v English>The additional four sigma points will be</v> <v English>representing the uncertainty caused by the process noise.</v> <v English>We also build the augmented covariance matrix PA.</v> <v English>This matrix has seven rows, and seven columns.</v> <v English>You just add the matrix Q as a lower right block,</v> <v English>and fill up the remaining fields with a zero.</v> <v English>Finally, the way to generate the 15 sigma points is exactly the same as before.</v> <v English>Just use the augmented elements as input.</v> <v English>In the next quiz,</v> <v English>you will adapt your sigma point generation function,</v> <v English>to the augmented state.</v>
