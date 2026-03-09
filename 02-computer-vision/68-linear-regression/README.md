# Linear Regression

> Part of: **From Linear Regression to Feedforward Neural Networks**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=GA9dkMzA9-c)

## Summary

**Linear Regression and Loss Functions**
=====================================

This project introduces linear regression as an algorithm for predicting continuous outcomes based on one or more input variables. We'll explore how to fit a linear model to data using the mean square error loss function (L2 loss).

### Key Concepts

* **Linear Regression**: A machine learning algorithm that predicts a continuous outcome variable based on one or more input variables.
* **Slope** and **Intersection**: Parameters of a linear regression model, where slope is the angle of the line and intersection is the value at which the line intersects the y-axis.
* **Linear Model Equation**: `y = m * x + b`, where `m` is the slope and `b` is the intersection.
* **Fitting**: The process of finding the best values for the model parameters (slope and intersection) to minimize the loss function.
* **Loss Function**: A mathematical formula that measures the difference between predicted and actual outcomes. In this case, we'll use the mean square error loss (L2 loss).
* **Mean Square Error Loss (L2 Loss)**: A common loss function for regression problems, which calculates the sum of squared differences between predicted and actual outcomes.
* **Gradient Descent**: An optimization algorithm used to find the optimal weights of a model by iteratively adjusting the parameters to minimize the loss function.

### Practical Notes

To implement linear regression in practice:

1. Choose a suitable loss function (e.g., L2 loss) based on the problem requirements and data characteristics.
2. Define the linear model equation (`y = m * x + b`) using the chosen loss function.
3. Use gradient descent or another optimization algorithm to find the optimal weights of the model by iteratively adjusting the parameters to minimize the loss function.

Note: This project only introduces the concept of linear regression and loss functions, and does not provide a complete implementation. The next lesson will cover how to implement gradient descent to optimize the model parameters.

## Transcript

Let's dive into our first algorithm, linear regression. Even though the focus on this lesson is classification, many elements from linear regression will be reused in classification algorithm. Later on, when we tackle object detection, we will realize that linear regression occupies a significant place. To understand linear regression, we can consider the following machine learning problem. Given the distance between two geographical locations, can we predict the trip duration of a self-driving car?

We can safely assume that the relation between these variables, time, and distance is not linear but we will still try to fit a linear model as an experiment. In this scenario, the distance is going to be our input variable, and the duration, our output variable. To get started, we gathered data points from hundreds of past trips. In this case, a data point is a pair of distance and duration values. We will use this data as a training set for our algorithm.

Because we learned the importance of good visualization in earlier lessons, we plotted the time as a function of the distance. To predict the time spent in the car from the distance for future trips, we will use a linear regression algorithm. Such an algorithm is defined by the following two parameters, the slope, and the intersection. The slope is the angle of the red line and the intersection, the value at which this line intersect the y-axis. A linear model is defined by the following equation, y equals m times x plus b.

We can see an example of a linear model fitted to our data set here. Later in this lesson, we will use the term weights to describe the parameters of a model. Now that we have chosen an algorithm, we need to fit it to our data. What does fitting mean? It means that we need to find the best value of m and b such that the loss is minimized.

Let's look at three different cases. In this case, we can see that the model poorly fits the data. Our model even suggest that the time spent in the car decreases with the distance. In this case, the fit is much better. However, we see that our model does not really fit the data well for larger distances.

Finally, we have a pretty good fit in this last case. But so how do we evaluate the quality of a fit? This is exactly where the loss function comes into play. But before we can fit a model to a data set, we first need to define the loss function, which is the topic of the next video. In the previous video, I mentioned that fitting a linear regression model meant finding the best values for the weight.

But what does best mean? Well, best according to a loss function that we choose. The loss function, we quantify the fit of our model. We will see many loss functions in this course, and the first one is the mean square error loss, or L2 loss. It is a very common loss function for regression problem in machine learning.

This loss function consist in the sum of the square differences between the ground truth y, and the prediction of y hat for each of the n data points in the training set. Let's look at the square function a little bit more in depth. As we can see here, the closer the prediction are from the observation, the closer to zero is the loss. This is exactly the behavior we would want from a good loss function. The better our model is at accurately estimating y, the smaller the loss is.

As a side note, the L2 loss has a property of penalizing outliers more than other loss functions. Outliers can be described as out of distribution data points. Let's say, for example, that for some reason the duration measured for a particular trip in our training set is wrong. Well, because we use the entire data set to fit our model, chances are that the square difference between the prediction y hat and the outlier is going to be high. The square function emphasizes this difference even more, and the loss value will be greatly affected by this single data point.

The L1 loss, which is the absolute difference between observation and predictions, will not be affected as much. As we can see in this diagram, for lower values of x, the absolute function and the square function have similar y values, but they diverge a great deal as x increases. This behavior must be kept in mind when choosing the loss function. We have picked an algorithm, linear regression and the loss function, the L2 loss. How do we use this loss to calculate the optimal weights of our models?

Well, we cannot try all possible combinations of weights to find the best ones. However, we will learn about a process called gradient descent, which is used to find the optimal weights.

## Additional Content

## Linear Regression
A **linear regression** model is a type of ML algorithm that assumes a linear relation between the input variable and the output variable. Such a model is described by two parameters, the slope `m` and the intersection `b` such that `y = mx +b`. Fitting or training such a model requires to adjust `m` and `b` to minimize the chosen loss function.
### Linear Regression Loss Functions
The **Mean Squared Error (MSE)** loss or **L2** loss is the one of the most common function used with linear regression algorithm. It is calculated by summing the square difference of the ground truths and the predictions. Because of the nature of the square function, this loss is very sensitive to **outliers** (out of distributions data points). If your dataset contains many outliers, the **L1** loss (absolute difference between ground truth and predictions) may be a better candidate.
