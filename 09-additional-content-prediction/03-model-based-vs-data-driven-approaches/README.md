# Model-Based vs Data-Driven Approaches

> Part of: **Prediction**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ehfA_NC7Ka4)

## Summary

**Intersection Prediction: Model-Based vs. Data-Driven Approaches**
===========================================================

This project explores two approaches to predicting vehicle behavior at intersections: model-based and data-driven.

### Key Concepts

* **T-shaped intersection**: A type of intersection where one road crosses another, requiring vehicles to make decisions about turning or going straight.
* **Model-based approach**: Uses mathematical models of motion that take into account physical capabilities and constraints imposed by traffic laws and other restrictions.
	+ **Process models**: Separate models for different behaviors (e.g. going straight, turning right).
	+ **Trajectory generator**: Predicts expected trajectory based on model assumptions.
	+ **Multimodal estimation algorithm**: Compares observed behavior to predicted trajectories and assigns probabilities to each outcome.
* **Data-driven approach**: Uses a blackbox algorithm trained on large datasets to predict behavior without relying on physical models or constraints.
* **Strengths of each approach**:
	+ Model-based: Incorporates knowledge of physics and traffic laws, but may miss subtle patterns in data.
	+ Data-driven: Can extract complex patterns from data, but lacks understanding of underlying physics.

### Practical Notes

This project does not provide specific code examples or implementation details. However, the discussion highlights the importance of considering both model-based and data-driven approaches when predicting vehicle behavior at intersections. The choice between these two methods depends on the specific requirements of the problem and the trade-offs between incorporating domain knowledge and leveraging large datasets.

Note: This summary focuses on the key concepts and ideas presented in the transcript, rather than providing a detailed explanation or implementation guide.

## Transcript

<v English>Imagine a T-shaped intersection.</v> <v English>The blue self-driving car pulls up to that stop sign and would</v> <v English>like to make a left turn but it sees this green car coming from the left.</v> <v English>If the green car is turning right,</v> <v English>it is safe for the blue car to go.</v> <v English>But if the green car is going straight,</v> <v English>then the blue car should wait.</v> <v English>The way we would handle this with the model based approach is as follows.</v> <v English>First we would come up with two process models,</v> <v English>one for going straight and one for turning right.</v> <v English>And we would use some simple trajectory generator to figure out</v> <v English>what trajectory we would expect to see if</v> <v English>the driver were going straight or turning right.</v> <v English>Then we would pay attention to the actual behavior of the target vehicle and using</v> <v English>a multimodal estimation algorithm which is still a black box for now we would</v> <v English>compare observed trajectory to the ones we would expect for each of our models.</v> <v English>And then based on that we would</v> <v English>assign a probability to each of the possible trajectories.</v> <v English>But the important takeaway for purely model based prediction is that we</v> <v English>have some bank of possible behaviors and each has a mathematical model of</v> <v English>motion which takes into account the physical capabilities of the object as well</v> <v English>as the constraints imposed by the road traffic laws and other restrictions.</v> <v English>What about a data driven approach.</v> <v English>Well with the purely data driven approach we have</v> <v English>a truly blackbox algorithm and this algorithm will be trained on lots of training data.</v> <v English>Once it&#39;s trained we just fitted</v> <v English>the observed behavior and let it make a prediction about what will happen next.</v> <v English>So we can see that each approach has its own strengths.</v> <v English>Model based approaches incorporate our knowledge of</v> <v English>physics constraints imposed by the road traffic et cetera and</v> <v English>data driven approaches are nice because they let us use data to</v> <v English>extract subtle patterns that would otherwise be missed by model based approaches.</v> <v English>For example differences in</v> <v English>vehicle behavior at an intersection during different times of the day.</v> <v English>And this leads to the somewhat leading question.</v> <v English>Which approach is the best.</v>
