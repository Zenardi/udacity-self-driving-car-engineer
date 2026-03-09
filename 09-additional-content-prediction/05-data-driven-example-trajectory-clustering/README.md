# Data Driven Example - Trajectory Clustering

> Part of: **Prediction**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=jbFeQ9P2V9A)

## Summary

**Trajectory Clustering for Predictive Modeling**

This project demonstrates how machine learning algorithms can be used in data-driven approaches for prediction, specifically in trajectory clustering. The goal is to identify patterns and similarities in vehicle trajectories at an intersection.

### Key Concepts

* **Data-Driven Prediction**: A method of using historical data to make predictions about future events.
* **Trajectory Clustering**: A technique used to group similar vehicle trajectories together based on their characteristics.
* **Offline Training Phase**: The process of preparing and training a model using historical data before it is deployed in real-world scenarios.
* **Online Prediction Phase**: The process of using the trained model to generate predictions about future events.
* **Agglomerative Clustering** and **Spectral Clustering**: Machine learning algorithms used for clustering similar trajectories together.
* **Prototype Trajectories**: Representative examples of typical behavior within each cluster.

### Practical Notes

To implement trajectory clustering, you will need to:

1. Gather a large dataset of vehicle trajectories using sensors or cameras at an intersection.
2. Clean and preprocess the data by removing any occluded or corrupted trajectories.
3. Define a mathematical measure of similarity between trajectories (e.g., Euclidean distance).
4. Use a machine learning algorithm (e.g., agglomerative clustering, spectral clustering) to group similar trajectories together.
5. Identify prototype trajectories for each cluster, which represent typical behavior within that cluster.
6. Deploy the trained model in real-world scenarios to generate predictions about future events.

Note: This project assumes prior knowledge of machine learning and data-driven prediction techniques.

## Transcript

<v English>There are many ways that machine learning algorithms can</v> <v English>be used in purely data driven approaches for prediction.</v> <v English>Since you already went through a machine learning class,</v> <v English>we won&#39;t go into these techniques into much detail.</v> <v English>But in this video,</v> <v English>I would like to show you one example that is representative</v> <v English>of what these algorithms are good at-- Trajectory clustering.</v> <v English>As is the case with all data driven prediction techniques,</v> <v English>there will be two phases.</v> <v English>An offline training phase where the algorithm learns a model from data</v> <v English>and online prediction phase where it uses that model to generate predictions.</v> <v English>Let&#39;s discuss the offline face first.</v> <v English>The first step is to get a lot of data which you</v> <v English>might do by placing a static camera at an intersection.</v> <v English>Then, we have to clean the data since some of the cars we</v> <v English>observe may be occluded or something else went wrong in the processing step.</v> <v English>So we need to discard the bad data.</v> <v English>Once the data is gathered and cleaned up,</v> <v English>we would be left with a bunch of trajectories that look something like this.</v> <v English>Next, we need to define some mathematical measure of</v> <v English>trajectory similarity and there are many ways to do this but intuitively we want</v> <v English>something that says a trajectory like this one in red is more</v> <v English>similar to this one in pink than it is to this one in blue,</v> <v English>even though they&#39;re red and blue trajectories overlap</v> <v English>more closely for a while than the red and pink ever do.</v> <v English>If you&#39;re interested in learning more,</v> <v English>I will include a link to a paper that discuss measures of similarity in detail,</v> <v English>but once we have a measure of similarity we can use a machine learning algorithm</v> <v English>like agglomerative clustering or a spectral clustering to clustered these trajectories.</v> <v English>In the case of a four-way stop intersection,</v> <v English>we would expect to see 12 clusters since at each of</v> <v English>the four stop signs cars can do one of three things: turn right,</v> <v English>go straight or turn left.</v> <v English>So if we were looking at just one of those four stop signs,</v> <v English>we would expect to see a cluster of trajectories for left turns,</v> <v English>going straight, and turning right.</v> <v English>Note that in some situations you may obtain even more clusters than that.</v> <v English>For example, if this lane is controlled by a traffic light instead of stop,</v> <v English>your clustering algorithm will probably create twice as many clusters.</v> <v English>Three of them go through the intersection without</v> <v English>stopping and three of them stop at the traffic light first.</v> <v English>Once the trajectories have been grouped into clusters,</v> <v English>it is useful to define what prototype trajectories look like for each cluster.</v> <v English>For the left turn cluster,</v> <v English>maybe these three trajectories are a good model.</v> <v English>They provide a compact representation of what</v> <v English>left turns typically look like at this intersection.</v> <v English>At this point, we have a trained model of typical car behavior at this intersection.</v> <v English>The next step is to use this model on the road to actually generate predictions.</v>

## Additional Content

#### Supporting Materials
*

[Trajectory Clustering for Motion Prediction - Sung, Feldman, and Rus](https://video.udacity-data.com/topher/2017/July/5978c2c6_trajectory-clustering/trajectory-clustering.pdf)
