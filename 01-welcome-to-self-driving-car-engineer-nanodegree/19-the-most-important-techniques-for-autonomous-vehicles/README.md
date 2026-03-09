# The Most Important Techniques for Autonomous Vehicles

> Part of: **Meet Waymo**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=H4mELzAMnAM)

## Summary

**Self-Driving Car Learning Techniques**
=====================================

This summary covers various machine learning techniques used in self-driving cars, including supervised learning, imitation learning, reinforcement learning, inverse reinforcement learning, self-supervised learning, and generative model learning.

### Key Concepts

* **Supervised Learning**: A standard approach in the industry where models learn from labeled data to make predictions or classify objects.
	+ Widely used in perception and prediction modules
	+ Also applied in planning modules
* **Imitation Learning**: Models learn by imitating expert behavior, useful for tasks like behavior prediction and planning
* **Reinforcement Learning/Inverse Reinforcement Learning**: Maximizes rewards over a longer-term horizon, often used in enclosed loop settings
* **Self-Supervised Learning**: Models can bootstrap themselves without explicit labels, learning representations that generalize to specific tasks with less data
	+ Has the potential to revolutionize perception by reducing the need for hundreds of millions of labeled boxes
* **Generative Model Learning**: Includes models like Variational Autoencoders (VAEs) and Generative Adversarial Networks (GANs)
	+ Useful in tasks like perceptual realism, generating data or sensor inputs that are difficult to distinguish from original data

### Practical Notes

While this lesson doesn't provide specific code examples, it highlights the importance of understanding various machine learning techniques for self-driving car development. These techniques can be applied in perception, prediction, planning, and other modules to improve system performance.

## Transcript

Different types of learning are applicable for self-driving cars. First of all, supervised learning is the standard main stain in the industry, it works really well. You can find it through out the stack, especially popular in perception and prediction, but also in different modules in planning. Other types of learning that are becoming popular are imitation learning and reinforcement or inverse reinforcement learning. They come into play in behavior prediction and planning.

When you want to develop systems that maximize a certain set of behavior or rewards over a longer-term horizon potentially working in what we call enclosed loop setting where the system needs to perform a certain activity over a period of time. Also, recently, another type of learning has become very popular, this is self-supervised learning. This is the ability of models to bootstrap themselves without explicit labels learning representations that generalize to task of interest with less data. That is really exciting and has the potential to revolutionize perception not to require hundreds of millions of labeled boxes, for example. Another type of learning is generative model learning.

This includes models such as variational autoencoders and GANs. Such model is also very useful in certain tasks, for example, perceptual realism, generating data or sensor inputs that are difficult to tell apart from the original, even in the synthesized environment. These are some examples that come to mind.

## Additional Content

## The Most Important Techniques for Autonomous Vehicles
You'll learn about many of these techniques, such as supervised learning and deep learning, later in the Nanodegree. Waymo also published a paper on [ChauffeurNet](https://sites.google.com/view/waymo-learn-to-drive/), an early approach to using imitation learning in their autonomous vehicles, which you may want to check out (or bookmark to come back to later on in the program).
