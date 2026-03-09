# Why Bother With Performance

> Part of: **Inference Performance**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=pCg0q8qmgsk)

## Summary

**Optimizing Neural Network Performance for Real-Time Applications**
===========================================================

This lesson explores the importance of optimizing neural network performance, particularly in real-time applications where speed and efficiency are critical. We'll discuss why simply relying on existing inference speeds may not be sufficient for demanding tasks like autonomous vehicles.

### Key Concepts

* **Neural network performance**: The ability of a neural network to process data quickly and accurately.
* **Real-time processing**: The need for neural networks to make predictions in real time, without latency or delay.
* **Autonomous vehicle perception system**: A critical component that relies on fast and accurate neural network predictions to navigate safely.
* **Inference speeds**: The speed at which a neural network can make predictions based on input data.

### Practical Notes

When working with demanding applications like autonomous vehicles, it's essential to optimize neural network performance to ensure real-time processing. This may involve:

* Using specialized hardware or software to accelerate inference speeds
* Implementing techniques like model pruning or knowledge distillation to reduce computational overhead
* Fine-tuning models for specific tasks and environments to improve accuracy and efficiency

Note that the specific requirements and constraints of each application will dictate the necessary optimizations, but the goal is always to squeeze every last bit of performance out of available hardware.

## Transcript

<v English>The first question you might have is, "Why even bother?</v> <v English>Are neural networks fast enough already?"</v> <v English>And that's a good question. The answer depends on the application.</v> <v English>If we were classifying whether something is a hotdog or not a hotdog,</v> <v English>we'd be fine with out of the box inference speeds.</v> <v English>Autonomous vehicles however, are more demanding than just identifying hotdogs.</v> <v English>The perception system in our vehicle has to make predictions in real time.</v> <v English>We can't use cloud computing resources due to the latency.</v> <v English>So all of these predictions must take place on the vehicle computational hardware.</v> <v English>Squeezing every last bit of performance out of this hardware is crucial.</v>
