# Trajectory Clustering 2 - Online Prediction

> Part of: **Prediction**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=UPiED4soM4w)

## Summary

**Online Prediction with Prototype Trajectories**
=====================================================

This README file summarizes the key concepts and practical steps involved in online prediction using prototype trajectories.

### Key Concepts

* **Prototype Trajectories**: These are representative trajectories of each cluster identified by the clustering algorithm.
* **Similarity Measure**: The same measure used for clustering is applied to compare the partial trajectory with prototype trajectories.
* **Belief Update**: The probability for each cluster is updated based on the similarity between the partial trajectory and prototype trajectories.
* **Predicted Trajectory**: A predicted trajectory for each cluster is computed by selecting the most similar prototype trajectory.

### Practical Notes

To implement online prediction, follow these steps:

1. Observe the vehicle's partial trajectory.
2. Compare it to corresponding segments of prototype trajectories for each cluster using a similarity measure.
3. Update the belief for each cluster based on the comparison results.
4. Compute a predicted trajectory for each cluster by selecting the most similar prototype trajectory.

Note that as more data becomes available, the probability for the most likely cluster will quickly approach 1.

## Transcript

<v English>Once our clustering algorithm has identified clusters and prototype trajectories,</v> <v English>in this case three clusters with three prototype trajectories each,</v> <v English>we can begin the job of online prediction for a vehicle that we meet on the road.</v> <v English>First, we observed the vehicle&#39;s partial trajectory.</v> <v English>Next we compare it to</v> <v English>the corresponding segments of the prototype trajectories for each cluster.</v> <v English>This comparison is done using</v> <v English>the same similarity measure we used earlier to perform the clustering.</v> <v English>The belief for each cluster is updated based on</v> <v English>how similar the partial trajectory is to the prototype trajectories.</v> <v English>And finally, we compute a predicted trajectory for each cluster.</v> <v English>For example, by taking the most similar prototype trajectory.</v> <v English>Let&#39;s make this more clear by following this car forward</v> <v English>in time from T equals zero to T equals one.</v> <v English>Let&#39;s go through these steps.</v> <v English>One, we observe the partial trajectory between time zero and one.</v> <v English>It is this green line behind the vehicle.</v> <v English>Two, well since all of the prototype trajectories overlap up to this point,</v> <v English>the trajectory comparison step will yield the same probability for each cluster.</v> <v English>Three, even though there is no clear winner within each cluster we still have to choose</v> <v English>one prototype trajectory to represent each cluster and we</v> <v English>broadcast these three trajectories with their associated probabilities.</v> <v English>Next, a T equal two- things get more interesting.</v> <v English>First, let&#39;s get rid of the car so we can see the trajectory more clearly.</v> <v English>Now when you make a comparison of</v> <v English>the partial trajectory with the nine prototype trajectories,</v> <v English>we find that the vehicle&#39;s partial trajectory</v> <v English>seems more similar to the red than purple or blue.</v> <v English>When we update the associated probabilities we might get something like this.</v> <v English>Note that red grows in probability and the blue and purple both shrink,</v> <v English>but blue shrinks more than purple since the partial trajectory is a worse match for blue.</v> <v English>Then, we pick the best prototype trajectory for</v> <v English>each cluster and use them to represent the future trajectory of the car.</v> <v English>As we continue this process,</v> <v English>we see the probability for the red cluster quickly approaches one.</v>

## Additional Content

**Note:** At the end of the video the red cluster is associated with a  probability of 0.99 rather than 0.009 as depicted.
