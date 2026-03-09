# Parameters and Consistency

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=S4fX3X_9oik)

## Summary

**Choosing Noise Parameters and Evaluating Their Choice**

This lesson discusses how to choose noise parameters for Bayesian filters, such as the unscented Kalman filter, and how to evaluate their choice. Choosing the right noise parameters is crucial for accurate state estimation.

**Key Concepts**

* **Noise**: Random fluctuations in measurements or process models that affect the accuracy of state estimates.
* **Process noise**: Uncertainty in the system's dynamics, represented by the variance of the acceleration noise (`nu_k`).
* **Measurement noise**: Uncertainty in sensor readings, represented by the variances of distance measurement (`sigma_rho_squared`), angle measurement (`sigma_phi_squared`), and radial velocity measurement (`sigma_rho_dot_squared`).
* **Noise covariance matrices**: Matrices that quantify the variances of process and measurement noise.
* **Consistency check**: A method to evaluate if the filter is providing realistic estimation uncertainty by comparing predicted measurements with actual measurements.
* **Normalized Innovation Squared (NIS)**: A scalar value calculated from the difference between predicted and actual measurements, normalized by the covariance matrix `S`.
* **Chi-squared distribution**: The statistical distribution of NIS values.

**Practical Notes**

When choosing noise parameters:

1. Estimate the maximum acceleration expected in your environment.
2. Choose half of this value as process noise (`nu_k`).
3. Consider the importance of reacting fast to changes or providing smooth estimations when adjusting `nu_k`.
4. Run a consistency check on the filter, including NIS calculations and plotting.

To evaluate the choice of noise parameters:

1. Calculate and plot NIS values for each time step.
2. Compare with the 95% line (e.g., 7.8) to determine if the uncertainty is underestimated or overestimated.
3. Use this feedback to adjust process noise settings in the project.

## Transcript

<v English>In this video I would</v>
<v English>like to discuss with you</v> <v English>how to choose noise parameters and</v>
<v English>how to evaluate this choice.</v> <v English>This is not only related to</v>
<v English>the unscented Kalman filter,</v> <v English>but it can be applied</v>
<v English>to any Bayesian filter.</v> <v English>When we talked about our process and</v>
<v English>our measurement models,</v> <v English>we introduced several</v>
<v English>sources of uncertainty.</v> <v English>In the process model,</v>
<v English>we introduced the process noise nu k.</v> <v English>And in the measurement model,</v> <v English>we introduced the measurement</v>
<v English>noise omega k.</v> <v English>In case of a radar measurement, this was</v>
<v English>the noise of the distance measurement</v> <v English>rho, the angle measurement phi,</v>
<v English>and the radial velocity rho dot.</v> <v English>We also quantified the noise with</v>
<v English>the process noise covariance matrix and</v> <v English>the measurement noise covariance matrix.</v> <v English>So these are the variances of the noise.</v> <v English>And they quantify how</v>
<v English>strong the noise is.</v> <v English>But we haven't discussed where</v>
<v English>we get these values from.</v> <v English>Let's start with the measurement noise.</v> <v English>This noise describes how</v>
<v English>precise the sensor can measure.</v> <v English>It means we have to look</v>
<v English>into the sensor manual and</v> <v English>see how precise the sensor is.</v> <v English>For example, we might read the radar</v>
<v English>can measure the distance rho</v> <v English>with the standard</v>
<v English>deviation of 0.3 meters.</v> <v English>This means we know the value for</v>
<v English>the variance sigma rho squared,</v> <v English>which is 0.09 meters squared.</v> <v English>We also have to assume the noise</v>
<v English>is white and normally distributed.</v> <v English>Which is of course not true for</v>
<v English>some sensors.</v> <v English>It is a little more difficult to</v>
<v English>choose an appropriate process noise.</v> <v English>In reality,</v> <v English>objects in a traffic environment don't</v>
<v English>move with wide acceleration noise.</v> <v English>This would mean a driver constantly</v>
<v English>switches between gas and brake.</v> <v English>So we really apply a strong</v>
<v English>approximation here.</v> <v English>But assuming a wide process noise.</v> <v English>A rule of thumb for</v>
<v English>getting useful values is the following.</v> <v English>Try to estimate what</v>
<v English>the maximum acceleration is you</v> <v English>expect in your environment.</v> <v English>Let's say we want to track</v>
<v English>cars in an urban environment.</v> <v English>Then these cars usually</v>
<v English>don't accelerate or</v> <v English>brake stronger than 6</v>
<v English>meters per second squared.</v> <v English>Now, the rule of thumb says,</v> <v English>choose half of the maximum acceleration</v>
<v English>you expect as process noise.</v> <v English>In this case, we would choose 9 meters</v>
<v English>squared over seconds to the power 4 as</v> <v English>variance for the acceleration noise.</v> <v English>If this is a good value for</v>
<v English>you really depends on your application.</v> <v English>Is it important for your application</v>
<v English>to react fast on changes?</v> <v English>Then you choose the process</v>
<v English>noise a little higher.</v> <v English>Is it important to provide</v>
<v English>smooth estimations?</v> <v English>Then you choose the process</v>
<v English>noise a little lower.</v> <v English>Usually, you want to know of course</v>
<v English>if you set up the noise parameters</v> <v English>correctly.</v> <v English>For that purpose, you can run</v>
<v English>a consistency check on the filter.</v> <v English>What does consistency mean?</v> <v English>At every time cycle, we calculate the</v>
<v English>measurement prediction zk + 1 pipe k and</v> <v English>the covariance matrix</v>
<v English>S of this prediction.</v> <v English>Then we receive the actual measurement</v>
<v English>zk + 1 for that time step.</v> <v English>In this example, everything looks okay.</v> <v English>The actual measurement occurred</v>
<v English>somewhere inside the error ellipse.</v> <v English>But this might look differently.</v> <v English>Imagine you set up a filter, and</v>
<v English>your measurement looks like this.</v> <v English>Here, something is wrong.</v> <v English>You constantly underestimate</v>
<v English>the uncertainty of</v> <v English>the predicted measurement.</v> <v English>This means your filter</v>
<v English>is not consistent.</v> <v English>Of course,</v>
<v English>these are all stochastic processes.</v> <v English>And it might just be</v>
<v English>a natural coincidence.</v> <v English>But if the results</v>
<v English>keep looking like this,</v> <v English>this explanation is extremely unlikely.</v> <v English>This result tells you that you</v>
<v English>underestimate the uncertainty</v> <v English>in your system.</v> <v English>Your estimate is less</v>
<v English>precise than you think.</v> <v English>The same can happen in</v>
<v English>the other direction.</v> <v English>Look at this example.</v> <v English>Here you overestimate</v>
<v English>the uncertainty of your system.</v> <v English>It means your estimate is actually</v>
<v English>more precise than you think.</v> <v English>So this filter is also inconsistent.</v> <v English>A filter is consistent if it provides</v>
<v English>a realistic estimation uncertainty.</v> <v English>It is very easy to check</v>
<v English>the consistency of your filter, and</v> <v English>I recommend to always do that</v>
<v English>when you design a filter.</v> <v English>An important consistency</v>
<v English>check is called NIS,</v> <v English>it means Normalized Innovation Squared.</v> <v English>This is how the NIS is calculated.</v> <v English>Its meaning is very intuitive.</v> <v English>The innovation is the difference</v>
<v English>between the predicted measurement and</v> <v English>the actual measurement.</v> <v English>And normalized means you put it into</v>
<v English>relation to the covariance matrix S.</v> <v English>That's why you have the inverse</v>
<v English>of the matrix S here.</v> <v English>The NIS is just a scalar number and</v>
<v English>super easy to calculate.</v> <v English>But you need to know</v>
<v English>what number to expect.</v> <v English>For that, you need to know something</v>
<v English>about the statistics of this NIS.</v> <v English>The NIS value follows a distribution</v>
<v English>which is called chi-squared</v> <v English>distribution.</v> <v English>If you Google chi-squared distribution,</v>
<v English>you will find a table like this.</v> <v English>And this table tells you the number</v>
<v English>you should expect for your NIS.</v> <v English>Let's find the right number for</v>
<v English>our example.</v> <v English>DF means degrees of freedom.</v> <v English>That's the dimension of</v>
<v English>our measurement space.</v> <v English>We have a three-dimensional</v>
<v English>radar measurement.</v> <v English>So we have three degrees of freedom.</v> <v English>So what do all these numbers mean?</v> <v English>0.95 says statistically,</v>
<v English>in 95% of all cases,</v> <v English>your NIS will be higher than 0.352.</v> <v English>And this column says in 5% of all cases</v>
<v English>your NIS will be higher than 7.815.</v> <v English>Let's remember this number, 7.8.</v> <v English>What you can always do when you</v>
<v English>design a filter is plot the 95% line.</v> <v English>In our case, that's 7.8.</v> <v English>And then for every time step k,</v>
<v English>calculate and plot also the NIS value.</v> <v English>If you see something like this,</v>
<v English>then everything looks great.</v> <v English>Sometimes you are over the 95% line,</v>
<v English>but that's what we expect.</v> <v English>If you see something like this, it means</v>
<v English>you underestimate the uncertainty in</v> <v English>your system,</v>
<v English>like in the example we saw before.</v> <v English>If you see something like this,</v> <v English>it means you overestimate</v>
<v English>the uncertainty in your system.</v> <v English>Your estimations are actually</v>
<v English>more precise than you think.</v> <v English>Unfortunately, the NIS test does not</v>
<v English>tell you where the mistake comes from,</v> <v English>but it gives you at least some feedback.</v> <v English>In this case, for example, it might be</v>
<v English>a good idea to reduce the process noise</v> <v English>a little bit and try again.</v> <v English>In the project, at the end of this</v>
<v English>lesson, take a look at your NIS and</v> <v English>use it to check your</v>
<v English>process noise settings.</v>

## Additional Content

### Process Noise and the UKF Project

For the CTRV model, two parameters define the process noise:
*

$\large \sigma^2_a$

representing longitudinal acceleration noise (you might see this referred to as linear acceleration)
*

$\large \sigma^2_{\ddot\psi}$

representing yaw acceleration noise (this is also called angular acceleration)

In the project, both of these values will need to be tuned. You will have to test different values in order to get a working solution. In the video, Dominik mentions using

$\large \sigma^2_a = 9 \frac{m^2}{s^4}$

as a starting point when tracking a vehicle. In the UKF project, you will be tracking a bicycle rather than a vehicle. So 9 might not be an appropriate acceleration noise parameter. Tuning will involve:
-  guessing appropriate parameter values
-  running the UKF filter
- deciding if the results are good enough
- tweaking the parameters and repeating the process

### Linear Acceleration Noise Parameter Intuition

Let's get some intuition for these noise parameters. The units for the acceleration noise parameter

$\large \sigma^2_a$

are

$\Large\frac{m^2}{s^4}$

. Taking the square root, we get

$\large \sigma_a$

with units

$\large \frac{m}{s^2}$

. So the square root of the acceleration noise parameter has the same units as acceleration:

$\large \frac{m}{s^2}$

The parameter

$\large \sigma_a$

is the standard deviation of linear acceleration! Remember from the "CTRV Process Noise Vector" lecture that the linear acceleration is being modeled as a Gaussian distribution with mean zero and standard deviation

$\large \sigma_a$

. In a Gaussian distribution, about 95% of your values are within 2

$\large \sigma_a$

. 

So if you choose

$\large \sigma^2_a = 9 \frac{m^2}{s^4}$

, then you expect the acceleration to be between

$\large -6 \frac{m}{s^2}$

and

$\large +6 \frac{m}{s^2}$

about 95% of the time.

Tuning parameters involves some trial and error. Using your intuition can help you find reasonable initial values.
### Yaw Acceleration Noise Parameter Intuition

If yaw acceleration has units of

$radians/s^2$

, what are the units of the yaw acceleration noise parameter

$\large \sigma^2_{\ddot\psi}$

?

(A)

$rad/s^2$

(B)

$rad^2/s^2$

(C)

$rad/s^4$

(D)

$rad^2/s^4$

Let's think about what values might be reasonable for the yaw acceleration noise parameter.

Imagine the bicycle is traveling in a circle with a constant yaw rate (angular velocity) of

$\Large \frac{\pi}{8} \frac{rad}{s}$

. That means the bicycle would complete a full circle in 16 seconds:

$\Large\frac{\pi}{8} \frac{rad}{s} \cdot$

$16 s = 2\pi$

. 

That seems reasonable for an average bike rider traveling in a circle with a radius of maybe 16 meters. 

The bike rider would have also have a tangential velocity of 6.28 meters per second because

$\Large\frac{\pi}{8} \frac{rad}{s} \cdot$

$16 \text{ meters}$

$= 6.28 \text{ meters per second}$

.

What if the angular acceleration were now

$\large -2\pi \frac{rad}{s^2}$

instead of zero? In just one second, the angular velocity would go from

$\Large \frac{\pi}{8} \frac{rad}{s}$

to

$\Large -\frac{15\pi}{8} \frac{rad}{s}$

. This comes from

$\Large \frac{\pi}{8} \frac{rad}{s}$

$- 2\pi$

$\Large \frac{rad}{s^2} \cdot$

$1 s = -$

$\Large \frac{15\pi}{8} \frac{rad}{s}$

.

The bicycle has been completing a complete circle in 16 seconds. But with such a high angular acceleration, then all of a sudden the bicycle is going around the circle in the opposite direction and only takes about 1.1 second to complete the circle. 

From a bicycle, a setting in the range of

$\large \sigma_{\ddot\psi} = 2\pi \frac{rad}{s^2}$

seems too high. In the project, you'll have to experiment with different values to see what works well.
### Measurement Noise Parameters

Measurement noise parameters represent uncertainty in sensor measurements. In general, the manufacturer will provide these values in the sensor manual. In the UKF project, you will not need to tune these parameters.
