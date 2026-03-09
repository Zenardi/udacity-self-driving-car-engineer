# Generating Sigma Points Exercise

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=TIc3n-cxTqc)

## Summary

**Generating Sigma Points in C++**
=====================================

This project involves creating a function called `generateSigmaPoints` that generates 11 sigma points from a given matrix. The function takes a pointer to a matrix as input and stores the generated sigma points in another matrix.

**Key Concepts**
---------------

* **Sigma Points**: These are points used in the unscented Kalman filter algorithm to approximate the distribution of the state.
* **Cholesky Decomposition**: A method for decomposing a covariance matrix into its square root, which is used to calculate the sigma points.
* **Eigen Library**: A C++ library for linear algebra operations that provides functions for Cholesky decomposition and other matrix operations.

**Practical Notes**
------------------

To complete this project, you will need to:

1. Create a function called `generateSigmaPoints` that takes a pointer to a matrix as input.
2. Calculate the square root of the covariance matrix using the Cholesky decomposition provided by the Eigen library.
3. Use the calculated square root to generate 11 sigma points and store them in a matrix called `Xsig`.
4. Fill the columns of `Xsig` with the generated sigma points, following the same ordering as shown in the video.
5. Return the pointer to the `Xsig_out` matrix.

Note: Make sure to use the correct ordering of sigma points to ensure accurate evaluation.

## Transcript

<v English>Welcome to the first coding</v>
<v English>quiz in this lesson.</v> <v English>Let's go ahead and</v>
<v English>put what we have learned into C++.</v> <v English>In this quiz you will write a small</v>
<v English>function that generates Sigma Points.</v> <v English>I've prepared the template for you and</v> <v English>I would like to quickly</v>
<v English>make you familiar with it.</v> <v English>You will be working on a function</v>
<v English>called generate Sigma Points.</v> <v English>Which receives a pointer</v>
<v English>to a matrix as input.</v> <v English>This is where you are expected</v>
<v English>to write your result.</v> <v English>I will show you how this works</v>
<v English>in the end of the function.</v> <v English>This time, we will consider</v>
<v English>the complete state of the CTR remodel.</v> <v English>So we set the state dimension n_x to 5.</v> <v English>Here we set the design parameter</v>
<v English>lambda to 3- n_x as suggested before.</v> <v English>Then we set the example set x and</v> <v English>the example covariance matrix</v>
<v English>P to some realistic values.</v> <v English>Now we create a matrix called Xsig.</v> <v English>This is a matrix with five rows and</v>
<v English>11 columns.</v> <v English>This is where I want you to</v>
<v English>store the sigma points later.</v> <v English>Now here, I give you a little help for</v> <v English>calculating the square root matrix</v>
<v English>of the covariance matrix P.</v> <v English>What you see here are two function calls</v>
<v English>which are part of the Eigen library.</v> <v English>It performs a Cholesky decomposition and</v>
<v English>provides the result we need.</v> <v English>Feel free to Google this approach,</v>
<v English>if you want to know more about it.</v> <v English>This is where you're</v>
<v English>supposed to put your code.</v> <v English>I would like you to calculate</v>
<v English>all 11 sigma points and</v> <v English>fill the columns of Xsig</v>
<v English>with the sigma points.</v> <v English>One thing is important,</v>
<v English>when you fill this matrix,</v> <v English>use the same ordering of sigma</v>
<v English>points as I showed you in the video,</v> <v English>to make sure the evaluation works.</v> <v English>In the end, the result will be printed,</v>
<v English>so you can check if it's realistic.</v> <v English>We received the pointer</v>
<v English>Xsig_out as input.</v> <v English>It points to a matrix.</v> <v English>This is how we put our</v>
<v English>result into this matrix.</v> <v English>Please don't change anything</v>
<v English>outside the student area</v> <v English>to make sure your result</v>
<v English>can be evaluated correctly.</v> <v English>Some of the challenges of these</v>
<v English>programming assignments are related to</v> <v English>handling rows and columns of</v>
<v English>matrices with the Eigen library.</v> <v English>Check link to the Eigen cheat sheet</v>
<v English>in the assignment description,</v> <v English>that will help you a lot.</v>

## Additional Content

## Instructor Notes:
In the video, the upper left value of

$sqrt(P_k|k)$

is 0.00656.  It should actually be  0.0656
### Helpful Equations and Resources

$$X_{k|k} = \Bigg [  x_{k|k} \qquad x_{k|k}+\sqrt{(\lambda+n_x)P_{k|k}} \qquad x_{k|k}-\sqrt{(\lambda+n_x)P_{k|k}} \Bigg]$$

remember that

$\large x_{k|k}$

is the first column of the Sigma matrix.

$\large x_{k|k}+\sqrt{(\lambda+n_x)P_{k|k}}$

is the second through

$\large n_x +1$

column.

$\large x_{k|k}-\sqrt{(\lambda+n_x)P_{k|k}}$

is the

$\large n_x +2$

column through

$\large 2n_x +1$

column.

and you can set columns easily in a matrix using the `.col()` function.

- [Eigen Quick Reference Guide](https://eigen.tuxfamily.org/dox/group__QuickRefPage.html)
- [Eigen Documentation of Cholesky Decomposition](https://eigen.tuxfamily.org/dox/classEigen_1_1LLT.html)

Please note that the algorithm used in the quiz ```(P.llt().matrixL())```produces the lower triangular matrix ```L``` of the matrix ```P``` such that `P = L*L^`. 


>Note: 
* The assignment files are present in `/home/workspace/assignments/01_generating_sigma_points` and the solution files are present in `/home/workspace/solutions/01_generating_sigma_points`

* After completing the assignment, you can run the code from the workspace terminal as follows:
	```bash
    cd /home/workspace/assignments/01_generating_sigma_points
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```
* Test your output against the output of the solution code. You can run the solution code as follows:
	```bash
    cd /home/workspace/solutions/01_generating_sigma_points
    g++ -I ../../eigen-3.4.0/ main.cpp ukf.cpp
    ./a.out
    ```

Solution Hint
  The two remaining sigma points are calculated by subtracting each column times the spreading factor from the mean state estimate, x.
