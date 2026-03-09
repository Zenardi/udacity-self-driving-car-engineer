# Sigma Point Prediction Solution

> Part of: **Unscented Kalman Filters**

## Additional Content

### Solution

In this case, the solution is the CTRV process model implemented with C++. The solution code is present in the workspace on the previous page. Feel free to play with it!
### Note:

Some students have noticed that transposing initialized dimensions for `MatrixXd(15, 5)` produces the same result.  This is due to the manner in which arguments are passed.

In `ukf.cpp`, a pointer is being passed as a function argument not as a reference:

```
void UKF::GenerateSigmaPoints(MatrixXd* Xsig_out) {
     ..... other code ...

    //write result
    *Xsig_out = Xsig;
```

Ultimately, we change the contents of the memory location which points to `Xsig_out`. That is why in this case the initialized dimensions are interchangeable.


See [this post](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/forum_archive/Sigma+Point+post.pdf) for more detail.
