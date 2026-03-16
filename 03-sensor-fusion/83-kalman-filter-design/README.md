# Kalman Filter Design

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=KYEr4BXhD_E)

## Summary

**Kalman Filter Design and Implementation**
=============================================

The Kalman filter is a mathematical algorithm used for estimating the state of a system from noisy measurements. To design a Kalman filter, you need to define two key components: the state transition function (F) and the measurement function (H).

### Key Concepts
* **State Transition Matrix (F)**: A matrix that describes how the state evolves over time.
* **Measurement Function (H)**: A matrix that maps the state to measurements.
* **Kalman Gain (K)**: A variable used in the measurement update step to determine the optimal estimate of the state.

### Practical Notes
To implement a Kalman filter, you need to perform two main steps:

1. **Prediction Step**: Use the state transition matrix (F) and the motion input (u) to predict the new state (x).
2. **Measurement Update Step**: Use the measurement (z), the prediction, and the measurement function (H) to update the estimate of the state.

The equations for these steps are:

**Prediction Step**

* `x_new = F \* x + u`
* `P_new = F \* P \* T + Q`

**Measurement Update Step**

* `e = z - H \* x`
* `s = H \* P \* T \* H^T + R`
* `K = s^-1 \* H \* P`
* `x_new = x + K \* e`
* `P_new = (I - K \* H) \* P`

Note that these equations are based on the 1D motion example provided in the lesson, and may need to be modified for higher-dimensional spaces.

## Transcript

When we design a Kalman filter, you need effectively 2 things. For the state, you need a state transition function, and that's usually a matrix, so we're now in the world of linear algebra. For the measurements, you need a measurement function. Let me give you those for the 1D motion of an object We know that the new location is the old location + velocity, turns into this matrix. You have a 1 over here and a 1 over here.

The new velocity should just be the old velocity, which gives us 0 over here and a 1 over here. If you multiply this matrix by this vector, this is exactly what you're getting. For the measurement, we only observe the first component of the place, not velocity, and that uses a matrix like this. This matrix would be called F and this H. The actual update equations for a Kalman filter are involved, and I give them to you, but please, don't memorize them, and I won't prove them for you.

Even the proof is very involved. Every time I use them, I just look them up. There's a prediction step where I take my best estimate x, multiply it with a state transition matrix--matrix F, and I add whatever motion I know--u. That gives me my new x. I also have a covariance that characterizes my uncertainty, and that is updated as follows, where T is the transpose.

There's also a measurement update step where we use the measurement z. We compare the measurement with our prediction where H is the measurement function that maps the state to measurements. We call this this the error. The error is mapped into a matrix s, which is obtained by projecting the system uncertainty into the measurement space using the measurement function projection + the matrix R, that characterizes the measurement noise. This is then mapped into a variable called K, which is often called the Kalman gain, where we invert the matrix s, and then finally, we actually update our estimate and our uncertainty using what ought to be the most cryptic equation that you've seen in a long time.

Now I wrote this down so that you have a complete definition, but this is something you should not memorize. If you really wish to understand this math, it happens to be just a generalization of the math I gave you to higher dimensional spaces, but I would recommend just not to worry about this. There's a set of linear algebra equations that implement the Kalman filter in higher dimensions.

## Additional Content

## Kalman Filter Design

The assignment:

```pseudo
x_prime = x + x_dot
```

assumes that the time interval delta_t is equal to 1. A more general formula is:

```pseudo
x_prime = x + x_dot*delta_t
```


### Definitions and Equations

As Sebastian notes, you don't need to memorize all of the equations here to be successful with Kalman Filters. However, we'll include these again below for your reference.

#### Definitions

- $\large x$ = estimate
- $\large P$ = uncertainty covariance
- $\large F$ = state transition matrix 
- $\large u$ = motion vector 
- $\large z$ = measurement 
- $\large H$ = measurement function 
- $\large R$ = measurement noise 
- $\large I$ = identity matrix

#### Prediction Equations

$\large x^\prime = Fx+u$

$\large P^\prime = F \cdot P \cdot F^T$

#### Measurement Equations

$\large y = z - H \cdot x$

$\large S = H \cdot P \cdot H^T + R$

$\large K = P \cdot H^T \cdot S^{-1}$

$\large x^\prime = x + (K \cdot y)$

$\large P^\prime = (I - K \cdot H) \cdot P$
