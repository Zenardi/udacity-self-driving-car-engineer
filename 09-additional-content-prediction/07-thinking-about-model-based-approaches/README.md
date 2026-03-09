# Thinking about Model Based Approaches

> Part of: **Prediction**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2JHmXN4AKNY)

## Summary

**Model-Based Approaches for Predicting Driver Behavior**

This project explores the use of model-based approaches to predict driver behavior, particularly in scenarios where data-driven methods may not be sufficient. By incorporating insights from physics, vehicle dynamics, and driver behavior, we can create more accurate predictions.

### Key Concepts

* **Naive Data-Driven Approaches**: These approaches rely solely on historical evidence to make predictions about future behavior.
* **Model-Based Approaches**: These approaches incorporate mathematical models of object motion to predict behavior.
* **Process Models**: Mathematical descriptions of object motion for a specific behavior, which can be used to compute the state of an object at time t+1 from its state at time t.
* **Uncertainty Representation**: Process models must incorporate some uncertainty to represent how much we trust our model.
* **Multimodal Estimation Algorithm**: An algorithm used to derive the probability of each maneuver by comparing observed states with predicted states.

### Practical Notes

To implement a model-based approach, follow these steps:

1. Identify all possible behaviors for an object in a given situation (e.g., change lanes, turn left).
2. Define a process model for each behavior, which is a mathematical description of object motion.
3. Use the process models to compute the probability of each behavior by comparing observed states with predicted states using a multimodal estimation algorithm.
4. Predict a trajectory for each behavior by iterating on the process models until the prediction horizon is reached.

Note: This project assumes prior knowledge of data-driven approaches and basic mathematical concepts. Further details on process models and multimodal estimation algorithms will be covered in subsequent videos.

## Transcript

<v English>Data driven approaches can be very useful</v> <v English>particularly when we have access to plenty of training data.</v> <v English>But in some ways purely data driven approaches are naïve since they rely</v> <v English>solely on historical evidence to make predictions about likely future behavior.</v> <v English>Ideally, we would also like to include, in our predictions,</v> <v English>all the insights we have about driver behavior,</v> <v English>physics, or vehicle dynamics.</v> <v English>This is where model based approaches can help.</v> <v English>The way these approaches typically work is as follows.</v> <v English>For each object identify all the behaviors</v> <v English>that object is likely to do in the current situation.</v> <v English>The behavior for a vehicle could be something like change lanes,</v> <v English>turn left and for a pedestrian,</v> <v English>it could be cross the street on pedestrian crossing.</v> <v English>For our intersection scenario,</v> <v English>the behaviors could be go straight,</v> <v English>turn left, turn right.</v> <v English>Whatever it is, it needs to be something that we can describe mathematically.</v> <v English>Step two, define a process model for each behavior.</v> <v English>A process model is a mathematical description of object motion for behavior.</v> <v English>It is a function which can be used to compute the state of</v> <v English>the object at time t_plus_1 from the state at</v> <v English>time t. The process model must</v> <v English>incorporate some uncertainty which represents how much we trust our model.</v> <v English>In our intersection example,</v> <v English>the left turn process model would produce an uncertain future state located roughly here.</v> <v English>The going straight process model would produce an uncertain future state located roughly</v> <v English>here and the right turn process model would</v> <v English>produce an uncertain future state located roughly here.</v> <v English>If you keep running the process models your uncertainty will increase.</v> <v English>Once we have a process model for each behavior we can go to the next step,</v> <v English>step three, which is to use</v> <v English>the process models to compute the probability of each behavior.</v> <v English>This is done by taking the observed state of the object at time t_minus_1,</v> <v English>running the process models to compute the expected state of the object at time t.</v> <v English>Then we compare the observed state of the object at</v> <v English>time t with what our process models predicted.</v> <v English>And we use a multimodal estimation algorithm to derive the probability of each maneuver.</v> <v English>The purpose of these algorithms is to maintain some belief about</v> <v English>how likely it is that the driver intends to perform each behavior.</v> <v English>We&#39;ll go into more detail later.</v> <v English>But in this case the probability of going straight</v> <v English>or turning left would be higher than the probability of turning right.</v> <v English>The fourth and final step is to predict a trajectory for each behavior.</v> <v English>This is done easily by iterating on</v> <v English>the process models until the prediction horizon is reached.</v> <v English>In the following videos,</v> <v English>we talk more about the process models we use to model behaviors and then</v> <v English>discuss one version of</v> <v English>multimodal estimation algorithm that can be used to maintain beliefs.</v>
