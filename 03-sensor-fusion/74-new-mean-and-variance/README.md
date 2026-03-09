# New Mean and Variance

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=yo8jf0U4hlc)

## Summary

**Mean and Variance Update for Kalman Filter**

This README file provides a summary of the key concepts and practical steps involved in updating the mean and variance in a Kalman filter using Python.

### Key Concepts

* **Kalman Filter**: A mathematical algorithm used to estimate the state of a system from noisy measurements.
* **Mean Update Equation**:
```python
new_mean = (mean1 * variance2 + mean2 * variance1) / (variance1 + variance2)
```
* **Variance Update Equation**:
```python
new_variance = (variance1 * variance2) / (variance1 + variance2)
```
* **Measurement Update Step**: The process of updating the mean and variance based on new measurements.

### Practical Notes

To implement the mean and variance update equations in Python, you can use the following code pattern:

```python
def update(mean1, variance1, mean2, variance2):
    new_mean = (mean1 * variance2 + mean2 * variance1) / (variance1 + variance2)
    new_variance = (variance1 * variance2) / (variance1 + variance2)
    return new_mean, new_variance
```

You can test this function with example inputs, such as:

```python
mean1, variance1 = 10, 8
mean2, variance2 = 13, 2

new_mean, new_variance = update(mean1, variance1, mean2, variance2)
print(new_mean)  # Output: 12.4
print(new_variance)  # Output: 1.6
```

Note that the output may not be exact due to floating-point precision issues in Python.

## Transcript

Let's now go back and write a program in which we calculate the new mean and the new variance term. I really just want you to write a Python program that implements those equations so that we can test them. I'm giving you a skeleton program, which has a function update, that takes as an input a mean and a variance for the first distribution and a mean and a variance for the second distribution and outputs the new mean and the new variance of the product of those. Here I am testing it with a mean of 10 and a variance of 8 and a mean of 13 and a variance of 2, which was one of our examples. Out should come the answer over here--12.4 and 1.6.

Of course, Python tends to not give you the exact output, so there are a couple of zeros over here but ignore those. The answer is effectively 12.4 and 1.6. Can you fill in those gaps? Here's my answer. This is the expression for the mean.

This is the one for the variance. I run it, and I get the exact same answer. I run it again for my other example of equal variances and 10 and 12 as means, and miraculously, the correct answer comes out-- 11 for the new mean and 2 for the new variance. If you programmed this correctly, then congratulations. You've just programmed an essential update step in the Kalman filter-- the measurement update step.

That's really the difficult step in Kalman filtering. The other one--the prediction step or the motion step--is much, much easier to program.

## Additional Content

## New Mean and Variance

### Solution
