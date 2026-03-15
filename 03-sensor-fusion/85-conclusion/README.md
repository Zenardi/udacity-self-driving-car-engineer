# Conclusion

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=6kFMxhlfHuI)

## Summary

**Kalman Filter Summary**
=========================

This summary covers the key concepts and practical steps introduced in the Udacity lesson on Kalman filters.

### Key Concepts

* **Gaussians**: A probability distribution used to model uncertainty in measurements.
* **Measurement updates using multiplication**: The process of updating a Gaussian distribution based on new measurement data, represented by the formula: `x_new = x_old * measurement`
* **Prediction or state transitions using convolution**: The process of predicting the next state of a system based on its current state and a set of transition probabilities, represented by the formula: `x_new = x_old * transition_matrix`
* **Kalman filter implementation**: A step-by-step guide to implementing a Kalman filter in the context of vehicle tracking.

### Practical Notes

* Implemented a Kalman filter for vehicle tracking, estimating nonobservable velocity from measurement data.
* Used multiplication and convolution operations to update and predict state transitions.
* Applied Kalman filter concepts to real-world problem of estimating velocity from measurement data.

## Transcript

So this completes my unit on Kalman filters. You learned actually quite a bit. You learned about Gaussians, how to do measurement updates using multiplication, how to do prediction or state transitions using convolution, and you even implemented your first Kalman filter, which is really super cool. You've implemented it in the context of vehicle tracking, and you used this to estimate a nonobservable velocity for measurement data. Now, next is your homework assignment. I hope you can prove what you've learned and ace it. Then, next week, we're going to move into particle filters, which is an exciting third method for state estimation. So I'll see you for the homework assignment, and then I'll see you in class for particle filters.


## Other Videos

If you'd like to watch another set of videos on Kalman filters, you might check out:

[The Kalman Filter](http://www.ilectureonline.com/lectures/subject/SPECIAL%20TOPICS/26/190)

from iLectureOnline
