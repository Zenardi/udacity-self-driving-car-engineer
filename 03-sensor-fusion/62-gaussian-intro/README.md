# Gaussian Intro

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6IhtnM1e0IY)

## Summary

**Gaussian Distribution and Unimodality**

This README file provides an overview of the key concepts covered in this lesson on Gaussian distributions and unimodality.

### Key Concepts

* **Gaussian distribution**: a continuous function that sums up to 1 over a space of locations, characterized by two parameters:
	+ **Mean (μ)**: often represented by the Greek letter Mu
	+ **Variance (σ²)**: often written as Sigma squared
* **Unimodality**: a property of functions with a single peak, which are symmetrical and have an exponential drop-off on both sides
* **Gaussian function formula**: an exponential of a quadratic function, where the exponent is proportional to the quadratic difference between the query point X and the mean μ divided by σ²

### Practical Notes

To identify whether a function is Gaussian or not, look for the following characteristics:

* Symmetry around a single peak
* Exponential drop-off on both sides of the peak
* A single maximum value (unimodality)

Note that this lesson focuses on theoretical concepts and does not provide any practical code examples. However, understanding these key concepts is essential for working with Gaussian distributions in various applications.

## Transcript

In common features the distribution is given by what's called a Gaussian. Gaussian is a continuous function over the space of locations in the area underneath sums up to one. So use our Gaussian again and if we call the space X then the Gaussian is characterized by two parameters. The mean, often abbreviated with the Greek letter Mu, and the width of the Gaussian, often called the variance. And for reasons that I don't want to go into, it's often written as a quadratic variable, Sigma square so any Gaussian is 1-D, which means the parameter space of a year is one dimensional, is characterized by Mu and Sigma squared. Our task in common spaces is to maintain a Mu and a Sigma squared as our best estimate of the location of the option we are trying to find. The exact formula is an exponential of a quadratic function. If we take the exponent of this complicated expression over here, the quadratic difference of our query point X relative to the mean Mu divided by Sigma square by [inaudible] minus a half. Now if X equals Mu then the enumerator becomes 0 and we have exp of zero which is one. It turns out we have to normalize this by a constant, one over the squared root of two Pi Sigma squared. But for every thing we talked about today this constant won't matter so ignore it. What matters is we have an exponential of a quadratic function over here. So let me draw you a couple of functions and you tell me which one you believe are Gaussian by checking the box on the right side. And please excuse my poor drawing skills here.

The answer is this one is a Gaussian, this one, and this one. They are all characterized by this exponential drop-off on both sides that are symmetrical, and they have a single peak. They are what's called "unimodal." This is a bimodal function that has two peaks and as a result is not Gaussian. The same is true over here and over here, so these guys don't qualify.

## Images

![A has one medium size hump, B has one tall hump, C has one fairly flat hump, D has two pointy humps, E has two small humps, and F has multiple small humps.](images/guassian-abc.png)
*Quiz Options*

## Additional Content

## Gaussian Introduction

The Gaussian equation given in the video is:

$\LARGE \frac{1}{\sqrt{2\pi\sigma^2}} \times \exp^{-1/2 \frac{(x - \mu)^2}{\sigma^2}}$

The mean is represented by

$\mu$

("mu") while the variance is represented by

$\sigma^2$

("sigma squared").

### Quiz Image

### Solution
