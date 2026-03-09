# Evaluation

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=n4tUWwzmZps)

## Summary

**Tracking Algorithm Performance Evaluation**
=====================================================

This lesson covers the evaluation of tracking algorithm performance using a common accuracy metric called **Root Mean Square Error (RMSE)**.

### Key Concepts

*   **Root Mean Square Error (RMSE)**: an accuracy metric used to measure the deviation of estimated state from true state in tracking algorithms.
*   **Estimated State**: a vector containing position and velocity components, representing the predicted location and speed of an object or entity.
*   **True State** (or **Ground Truth Values**): actual values representing the real-world location and speed of an object or entity.
*   **Residual**: the difference between estimated state and true state.

### Formula

RMSE is computed using the following formula:

```math
RMSE = √(1/n \* ∑(x_est - x_true)^2)
```

where `n` is the number of samples, `x_est` is the estimated state, and `x_true` is the true state.

### Practical Notes

To evaluate the performance of your tracking algorithm using RMSE:

1.  Compute the difference between estimated state and true state (residual).
2.  Square each residual value.
3.  Average the squared residuals.
4.  Take the square root of the average to obtain the RMSE value.

A lower RMSE indicates higher estimation accuracy.

## Transcript

Once we have implemented our tracking algorithm, we might want to check its performance in terms of how far the estimated result is from the true result. There are many evaluation metrics, but perhaps the most common one is the so-called root mean square error. In the context of tracking, it's an accuracy metric used to measure the deviation of the estimated state from the true state. Let's see how it is computed. At the given processing step, we basically need two values: the estimated state, which is a vector with the position and velocity components, and the real values that are also called ground truth values.

The difference between the estimated state and true state is called residual. These residuals are squared and averaged. Finally, the square root gives us the error metric. The lower the error is, the higher our estimation accuracy. In the final project, you will implement your own AKF tracker and evaluate its performance with the root mean square error.

## Additional Content

## Evaluation
To evaluate the performance of our tracking, we can use the

$\textbf{Root Mean Square Error (RMSE)}$

, which calculates the residual between estimated state and ground truth state:

$$RMSE = \sqrt{\frac 1n\sum_{k=1}^n \left(x_k^{\text{est}}-x_k^{\text{true}}\right)^2}$$
