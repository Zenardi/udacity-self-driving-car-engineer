# Exercise: Gating

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=VISEuCqgB-k)

## Summary

**Gating Function and Track Association**
=====================================

This project introduces the concept of a gating function to filter out unlikely track-measurement associations based on their Mahalanobis distances. The goal is to implement a gating function using the inverse cumulative chi-square distribution and use it to refine the association matrix.

**Key Concepts**

* **Inverse Cumulative Chi-Square Distribution**: A statistical distribution used to calculate the probability of a measurement lying within a certain range.
* **Gating Function**: A method that filters out unlikely track-measurement associations based on their Mahalanobis distances.
* **Mahalanobis Distance**: A measure of the distance between a point and a distribution, used to determine the likelihood of association between tracks and measurements.
* **Association Matrix**: A matrix representing the possible associations between tracks and measurements, with entries indicating the Mahalanobis distances.

**Practical Notes**

To implement the gating function, you will need to:

1. Use the inverse cumulative chi-square distribution to calculate the probability of a measurement lying within a certain range.
2. Implement the `gating_function` method, which should return `True` if the measurement lies inside the gate and `False` otherwise.
3. Implement the `get_closest_track_and_measurement` function, which searches the association metrics for the smallest entry (i.e., the closest track-measurement pair).
4. Use the gating function to refine the association matrix by deleting rows and columns corresponding to unlikely associations.

Note: The starter script provides a basic implementation of the track and measurement classes, as well as a sample loop that calls the `get_closest_track_and_measurement` function. You will need to modify this code to implement the gating function and refine the association matrix.

## Transcript

Here's the last exercise before we can move on to the final project. This data code should look very familiar, it is quite similar to the last exercise. We will use the same association class as before, where the associate function fills the association metrics with the image devalues. One difference is that we now also use the unassigned tracks and unassigned measurements list. There are two tasks for you in this exercise.

First, I want you to implement the gating function based on the inverse cumulative chi-square distribution. If you are unsure of how to do this in Python, check out the hint below the video. The gating function should return true if the measurement lies inside the gate, otherwise false. The second task is to implement the function called get_ closest_track_and_measurement, which should return the closest track and closest measurement for the next update. Therefore, you have to search the association metrics for the smallest entry.

If the association matrix only contains infinities entries, please return none. Otherwise, you should delete the row and column of the minimum entry from the matrix, and get the right track number and measurement number from the two lists. Finally, please delete the corresponding entries from the unassigned tracks and unassigned measurements list respectively, and return the track and the measurement. In the remainder of the starter script, you can find the track and measurement classes that you already know from the previous exercise. Just like before, we generate three random tracks and three noisy measurements and calculate the association matrix.

Here is a new loop that calls the new function named get_closest_track_and_ measurement, and plots the return distance. The loop is repeated until a is empty or contains only infinities entries. Let's see what happens if I run the script. The output looks just like in the last exercise, where we have our three tracks and three measurements, and the possible associations with Mahalanobis distances in-between. Now see if you can remove some of these unlikely far away associations by implementing the correct gating method.

## Additional Content

## Exercise: Gating
### Hints

- To calculate the inverse cumulative $\chi^2$ distribution $F_{\chi^2}^{-1}\left(p|df\right)$ with probability $p$ and degrees of freedom $df$ (which equals the dimension of the measurement space here), you can use the scipy package:

    ```python
    from scipy.stats.distributions import chi2

    chi2.ppf(p, df)
    ```

    `ppf` stands for percent point function, which is the inverse of the cumulative density function. See the [related scipy documentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.chi2.html) for more details.

- To get the indices of the minimum entry in the association matrix A, you can use `numpy.argmin`. Usually, this function returns the index of the flattened array. In order to avoid this, we can use `numpy.unravel_index` as follows:

    ```python
    np.unravel_index(np.argmin(A, axis=None), A.shape)
    ```

    Check out the [numpy `argmin` documentation](https://numpy.org/doc/stable/reference/generated/numpy.argmin.html) for more details!
