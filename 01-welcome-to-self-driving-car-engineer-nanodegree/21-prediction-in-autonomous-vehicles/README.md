# Prediction in Autonomous Vehicles

> Part of: **Meet Waymo**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=-_Xpj4nSurc)

## Summary

**Behavior Prediction in Autonomous Vehicles**
=============================================

This lesson covers various techniques for predicting vehicle behavior over 10-15 seconds into the future. It discusses classical methods combining motion planning and machine learning, as well as recent advancements in end-to-end behavior prediction models.

### Key Concepts

* **End-to-end behavior prediction models**: These models take in environmental representations (from sensor data or intermediate perception) and directly output full behavior predictions.
* **Data structures for prediction**: The lesson highlights the importance of choosing effective data structures to represent agents, actions, history, semantic context, maps, and their contents.
* **Agent modeling**: Agents can be represented as bounding boxes, but understanding gaze, gestures, and actions is crucial for accurate navigation.
* **Map representations**: Traditional methods use top-down images with convolutional neural networks, while recent work employs structured map representations, such as vector networks that model maps as polylines.

### Practical Notes

The lesson mentions the following practical aspects:

* **Vector network architecture**: A neural network that models maps directly as polylines and uses graphical neural nets and transformers to achieve better results.
* **Structured map representation**: This approach is gaining traction, enabling richer and more accurate environmental representations for behavior prediction models.

Note: The provided transcript does not include specific code or formulas. If you need a summary with code examples or mathematical derivations, please provide the relevant sections of the transcript.

## Transcript

In many cases, our vehicle needs to predict over 10-15 seconds into the future in order to plan a complex maneuver, such as an unprotected left turn that could take a while to execute. There is a variety of techniques that work well for prediction. Some of the more classical methods that combine motion planning and machine learning work quite well and encode well the knowledge that humans have about constraints in the environment. However, recently, it's been an incredibly hot field to keep improving the end-to-end behavior prediction models. Those that take in representation of the environment, whether it from sensor data or from an intermediate perception representation, and directly give you the full behavior prediction output, and those are now really good as well.

There's multiple ways in which it can be done well nowadays. There is an open question of what are the most effective data structures for prediction. When thinking about prediction, one needs to think about how to represent agents, actions and history, as well as the semantic context of the scene, the current map, and what is contained in it. Our understanding and the community's understanding of those has been changing and improving. For example, you can model agents as bounding boxes.

That leads to certain quality of prediction. However, understanding the gaze and gestures and actions of people in the environment is often a big part of accurate renavigating the scene. In map representations traditionally, what is popular is representing the map as an image and applying convolutional neural networks to this top-down image. Recently, there is a lot of work that's representing map in a structured way. This includes our vector network that we published at CVPR, where we model the map directly as polylines and feed it into a neural network that contains a graphical neural net processing transformers and get better results than what you can get by rendering top-down images.

There is a trend towards richer, more structured representations of the environment and models that can take advantage of that.

## Additional Content

## Prediction in Autonomous Vehicles

Prediction is an area humans have long been better at than computers when it comes to driving - have you ever felt sure a car in front of you was going to change lanes, even without their blinker on?

On this page, Dragomir will discuss prediction in autonomous vehicles, and how Waymo is closing the gap (or even exceeding!) human ability in the area.

While prediction is not part of the core content of the program, note that when you leave a lesson, on the left side of your classroom, the sidebar contains both "Core Curriculum" as well as "Extracurricular". Within the "Extracurricular" section, you can also find a lesson on Prediction, which you may want to come back to later in the program.

### Predicting Actions in the Future
### Techniques that Work Well for Prediction
### Data Structures used for Prediction
