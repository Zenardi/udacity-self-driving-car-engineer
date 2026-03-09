# What to Expect from the Project

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=WAt_g6HgYvs)

## Summary

**UKF in Self-Driving Cars: Key Concepts and Practical Notes**

**Key Concepts**

* **UKF (Unscented Kalman Filter)**: A tool for estimating the state of dynamic objects, such as position, velocity, orientation, and yaw rate.
* **Consistency Check**: A method to verify if the UKF is providing realistic covariance metrics by comparing NIS (Normalized Innovation Squared) values with a threshold.
* **NIS Values**: A measure of how well the UKF is performing, indicating whether it's consistent or not.
* **Covariance Matrix**: A matrix that provides information on the uncertainty of the estimation result.

**Practical Notes**

The lesson demonstrates the use of the UKF in self-driving cars to estimate the state of dynamic objects. The instructor highlights the importance of consistency checks and NIS values in verifying the performance of the UKF. Practical steps include:

* Playing around with process noise values to make the estimation smoother or more responsive.
* Checking the consistency of the filter by monitoring NIS values.
* Using radar and laser measurements together to improve velocity estimate convergence.

The instructor also emphasizes the importance of covariance matrices in providing information on the uncertainty of the estimation result, which is crucial for self-driving cars.

## Transcript

<v English>It's really great to see you made it all</v>
<v English>the way through this challenging lesson.</v> <v English>In the project description, you will</v>
<v English>find everything you need to know to</v> <v English>successfully complete the project.</v> <v English>In this video,</v> <v English>I would like to point out some things</v>
<v English>about the UKR I find quite remarkable.</v> <v English>And I also want to explain why</v>
<v English>a common filter in general</v> <v English>is such an important tool for</v>
<v English>self driving cars.</v> <v English>Let's have a look at</v>
<v English>the scenario on the project.</v> <v English>You have seen a similar plot</v>
<v English>before in the EKF project.</v> <v English>We see here a bicycle that is</v>
<v English>first driving straight and</v> <v English>then turning into a circle.</v> <v English>The path of the bicycle</v>
<v English>is shown in blue.</v> <v English>The green line is the sequence of all</v>
<v English>measurements we receive both from LiDAR</v> <v English>and radar.</v> <v English>As before,</v>
<v English>these measurements are quite noisy.</v> <v English>The orange dots are the estimation</v>
<v English>resource of the UKF fusing laser and</v> <v English>radar measurements.</v> <v English>Remember, the linear process</v>
<v English>model in the last project</v> <v English>had problems following the turn.</v> <v English>The CTR model we're using this time</v>
<v English>follows the turn quite nicely, and</v> <v English>still provides a smooth</v>
<v English>position estimate.</v> <v English>You can play around with</v>
<v English>the process noise values, and</v> <v English>make the estimation even smoother.</v> <v English>Or force it to follow</v>
<v English>the measurements quicker.</v> <v English>When you change</v>
<v English>the process noise values,</v> <v English>also make sure to check</v>
<v English>the consistency of your filter.</v> <v English>This is how the consistency</v>
<v English>check of my filter looks like.</v> <v English>What you see here in orange are the NIS</v>
<v English>values of the three dimensional radar</v> <v English>measurements.</v> <v English>I also plotted the 95% line in blue.</v> <v English>Just as expected, a small number</v>
<v English>if NIS values exceed this line.</v> <v English>If your NIS values look like this,</v> <v English>you know you have set</v>
<v English>up a consistent filter.</v> <v English>This is how the NIS values of</v>
<v English>the laser measurements look like.</v> <v English>Be aware that the 95% line is at</v>
<v English>a different level in this case</v> <v English>because the laser measurement</v>
<v English>is a two dimensional vector.</v> <v English>The project description will give you</v>
<v English>details about the exact criteria for</v> <v English>a successful consistency check.</v> <v English>Remember if the UKF is consistent,</v> <v English>it means it provides</v>
<v English>a realistic covariance metrics.</v> <v English>The UKF also estimates the velocity</v>
<v English>of the bicycle of course.</v> <v English>It can do it with or without radar.</v> <v English>But if you compare these two options,</v>
<v English>you will find out</v> <v English>that the velocity estimate converges</v>
<v English>much faster if you use the radar too.</v> <v English>Give it a try and switch on and</v>
<v English>off both sensors, and</v> <v English>see how they contribute</v>
<v English>in different ways.</v> <v English>What I find really impressive is</v>
<v English>how precise the UKF can estimate</v> <v English>the orientation of the bicycle.</v> <v English>None of our sensors is able to</v>
<v English>directly observe the orientation, but</v> <v English>we still get a precise estimate.</v> <v English>Even the yaw rate can be estimated</v>
<v English>providing useful results.</v> <v English>For autonomous vehicles,</v> <v English>the yaw rate of other vehicles</v>
<v English>is very important to know.</v> <v English>Imagine another car</v>
<v English>starting to change lanes or</v> <v English>a bicycle in front of you</v>
<v English>wants to do a left turn.</v> <v English>Hopefully, they would both signalize</v>
<v English>their intention but in the end</v> <v English>the yaw rate is the ultimate indicator</v>
<v English>for such a behavior prediction.</v> <v English>Let's summarize the three most</v>
<v English>important probabilities of the UKF as</v> <v English>a centrifusion tool for</v>
<v English>self driving cars.</v> <v English>Number one, the UKF, you will be able to</v>
<v English>take noisy measurement data as input and</v> <v English>provide a smooth position and</v> <v English>velocity estimation of dynamic objects</v>
<v English>around you, without introducing a delay.</v> <v English>Number two, you can provide</v>
<v English>an estimation of the orientation and</v> <v English>the yaw rate of other vehicles using</v>
<v English>sensors that can't even directly observe</v> <v English>these things.</v> <v English>And number three, in addition to that,</v> <v English>the UKF also give information</v>
<v English>on how precise the result is.</v> <v English>Because it always provides a covariance</v>
<v English>matrix for every estimation.</v> <v English>And you know that this covariance</v>
<v English>matrix is realistic if the UKF performs</v> <v English>a consistency check.</v> <v English>The uncertainty of the estimation result</v>
<v English>is very important for self driving cars.</v> <v English>Because if the position of your leading</v>
<v English>vehicle is quite uncertain at some time,</v> <v English>you better keep a little more distance</v>

## Additional Content

### Initializing the Kalman Filter

As discussed previously, the process noise parameters have an important effect on your Kalman filter; you will need to tune the longitudinal and yaw acceleration noise parameters as part of the project.

The initial values for your state variables will also affect your Kalman filter's performance. Both the:
* state vector **x** and the
* state covariance matrix **P**

need to be initialized for the unscented Kalman filter to work properly.

#### Initializing the State Vector x
The state vector **x** contains

$x = [p_x,  p_y, v, \psi, \dot{\psi}]$

. 

You won't know where the bicycle is until you receive the first sensor measurement. Once the first sensor measurement arrives, you can initialize

$p_x$

and

$p_y$

. 

For the other variables in the state vector **x**, you can try different initialization values to see what works best.

Note that although radar does include velocity information, the radar velocity and the CTRV velocity are not the same. Radar velocity is measured from the autonomous vehicle's perspective. If you drew a straight line from the vehicle to the bicycle, radar measures the velocity along that line. 

In the CTRV model, the velocity is from the object's perspective, which in this case is the bicycle; the CTRV velocity is tangential to the circle along which the bicycle travels. Therefore, you cannot directly use the radar velocity measurement to initialize the state vector.


#### Initializing the State Covariance Matrix P

To initialize the state covariance matrix **P**, one option is to start with the identity matrix. For the CTRV model, **P** is a 5x5 matrix. The identity matrix would be:

$$P_{\text initial} =  \begin{bmatrix}
1 \qquad 0 \qquad 0 \qquad 0 \qquad 0 \\
0 \qquad 1 \qquad 0 \qquad 0 \qquad 0 \\
0 \qquad 0 \qquad 1 \qquad 0 \qquad 0 \\
0 \qquad 0 \qquad 0 \qquad 1 \qquad 0 \\
0 \qquad 0 \qquad 0 \qquad 0 \qquad 1
\end{bmatrix}$$

Think back to what the state covariance matrix represents: take for example the value in the first row, second column. The value at (1, 2) would be the covariance

$\large \sigma_{px, py}$

measuring the linear relationship between the two variables. 

The diagonal values represent the variances for each of the variables in the **x** state vector:

$\large [\sigma^2_{p_x},  \sigma^2_{p_y}, \sigma^2_{v}, \sigma^2_{\psi}, \sigma^2_{\dot{\psi}}]$

. 

Why is the identity matrix a good place to start? Since the non-diagonal values represent the covariances between variables, the **P** matrix is symmetrical. The identity matrix is also symmetrical. The symmetry comes from the fact that the covariance between two variables is the same whether you look at (x, y) or (y, x):

$\large \sigma_{px, py} = \sigma_{py, px}$

. If you print out the **P** matrix in your UKF code, you will see that **P** remains symmetrical even after the matrix gets updated. If your solution is working, you will also see that P starts to converge to small values relatively quickly.

Instead of setting each of the diagonal values to 1, you can try setting the diagonal values by how much difference you expect between the true state and the initialized **x** state vector. For example, in the project, we assume the standard deviation of the lidar x and y measurements is 0.15. If we initialized

$p_x$

with a lidar measurement, the initial variance or uncertainty in

$p_x$

would probably be less than 1.

You will have to experiment with different initialization values to find a working solution.
