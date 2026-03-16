# Track Deletion

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=VFwAy91k16U)

## Summary

**Track Deletion Criteria**
==========================

This document summarizes the key concepts and practical notes from the Udacity lesson on track deletion criteria for self-driving cars. The main topic is how to quickly decide which tracks are real and which are not, allowing for unnecessary emergency braking to be avoided.

### Key Concepts

* **Track Score**: a measure of the likelihood that a track is correct
	+ Thresholds can be set to delete or confirm tracks based on their score (e.g. below 0.1 or 0.6)
* **Estimation Error Covariance P**: represents an ellipse around the track where the true position of the object is likely to lie
	+ The covariance increases with prediction and decreases with measurement updates, but keeps increasing if no measurements are received
	+ Large covariance values indicate that the object could be anywhere, making it unnecessary to keep the track in the list

### Practical Notes

* To delete a track, use one of the following criteria:
	+ Track score drops below a certain threshold (e.g. 0.1 or 0.6)
	+ Covariance metrics gets too big (i.e. the ellipse becomes too large)
* These are heuristic criteria based on experience and do not have a theoretical foundation
* You can define your own deletion criteria if needed

Note: The code for implementing these track deletion criteria is not provided in this document, but it would involve using the track score and covariance metrics to make decisions about which tracks to delete or confirm.

## Transcript

Let's go back to our example. Our initial question was, how can we quickly decide which track is real and which is not? Or in other words, how can we quickly delete the false positive track two, before the self-driving car will trigger an unnecessary emergency braking? With our newly refined track score and track state, this is straight forward. We can simply delete a tentative track once the score drops below a certain threshold, for example, below 0.1 and we can delete or confirm track once the score drops below 0.6 for example.

The idea behind defining a different threshold for confound tracks is to accelerate their deletion. There's one more criterion that could be helpful for track deletion, which is the size of the estimation error covariance P. Remember that we can think of the covariance as an ellipse around the track. The true position of the object most likely lies somewhere inside the ellipse. If we predict the track, the covariance increases and with every measurement update, it decreases again, but if we do not get any measurement updates, the covariance keeps increasing.

After some cycles, the covariance has increased so much that the object could basically be anywhere. So it makes not much sense to keep this track in our track list. Therefore, one can use an additional track deletion criteria based on the size of the matrix entries in the estimation error covariance P. To sum it up, we delete a track if either the track score drops below a certain threshold or the covariance metrics gets too big. Again, these are heuristic criteria based on experience.

There's no theoretic foundation and you can define your own deletion criteria if you like.

## Additional Content

## Track Deletion
### Example Track Deletion Criteria
Here is one example for heuristic track deletion criteria that you could use in the final project:

- Confirmed tracks:
  - Delete if score $< 0.6$. This only holds for confirmed tracks, so the score must have been above 0.8 before and then drop below 0.6.
  - Delete if $\mathbf P_{11}> 3^2$ or $\mathbf P_{22}> 3^2$. This means our object could be anywhere inside a circle of 3 meters radius, the position uncertainty has increased so much that the track should be deleted.
- Tentative or initialized tracks:
  - Delete if score $< 0.17$. Note that this threshold is much lower than for confirmed tracks, we don't want new tracks to be immediately deleted before they can stabilize.
  - Delete if $\mathbf P_{11}> 3^2$ or $\mathbf P_{22}> 3^2$.

Again, these are heuristic design parameters, feel free to experiment and define your own in the final project!
