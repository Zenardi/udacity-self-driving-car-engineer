# Augmentation Solution

> Part of: **Unscented Kalman Filters**

## Additional Content

### Solution

Here's my process:

1. I added two noise values to the mean of the augmented state. The mean of the noise values is zero, so I set these numbers to zero.
2. I filled the augmented covariance matrix with zeros.
3. Then I set the top left block of the augmented covariance matrix using the function `topLeftcorner` from the cheat sheet.
4.I manually put the variances into the lower right block of the augmented matrix. This 2x2 block corresponds to the matrix

$Q$

.

The rest is exactly the same as before, except that I created more sigma points this time.

You can find my solution in the workspace on the previous page. Feel free to play with it!
