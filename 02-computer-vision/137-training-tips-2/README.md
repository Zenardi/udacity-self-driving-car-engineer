# Training Tips #2

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=WaHdV8UCAKQ)

## Summary

**Training a New Neural Network Architecture: A Guide**
=====================================================

As a machine learning engineer, it's essential to develop a deep understanding of your dataset before training a new neural network architecture. This involves becoming familiar with the data and establishing baselines for model performance.

### Key Concepts
* **Data Familiarity**: Spend hours examining images in your dataset to gain insight into its characteristics.
* **Baselines**: Establish a baseline for model performance using the random guess method as a minimum threshold.
* **Overfitting Check**: Train on a single batch and check for overfitting by monitoring loss and visualizing predictions.
* **Data Transformation**: Verify that data is not being transformed during loading into your pipeline.
* **Model Iteration**: Experiment with different models, hyperparameters, and learning rates to optimize performance.

### Practical Notes
When building your training pipelines, follow these practical steps:

1. **Overfitting Check**: Train on a single batch, monitor loss, and visualize predictions to ensure the model is not overfitting.
2. **Data Verification**: Verify that data is not being transformed during loading into your pipeline.
3. **Model Iteration**: Experiment with different models, hyperparameters, and learning rates to optimize performance.
4. **Hyperparameter Tuning**:
	* Start with the optimizer and learning rate used in the original architecture for existing models (e.g., Faster R-CNN).
	* Avoid using learning rate annealing initially.
	* Only add data augmentation when necessary.
5. **Model Complexity**: Experiment with different model sizes to balance overfitting and underperformance.

By following these guidelines, you'll develop a deeper understanding of your dataset and improve the performance of your neural network architecture.

## Transcript

In this video, I wanted to share a few steps to follow when training a new neural network architecture. Before anything else, and I cannot emphasize this enough, as a machine learning engineer, you need to become one with the data. You should spend hours looking at the different images in your dataset. Once you've become familiar with the data, you can establish baselines. I usually use the random guess baseline as a lowest threshold for my model performances.

Next, you can start building your training pipelines. However, before you start training your model on the whole dataset, you need to perform a few check. First, you should try to overfit a single batch. By doing so, you're checking that your model is complex enough to model the signal of a few examples, you should wait for the loss to reach zero and visualize the model predictions to be sure that they are matching the ground truth. Because your data may be transformed when it's being loaded in your pipeline, you should check it right before it's being fed to the network.

Similarly, you should also visualize your model predictions. Once you're confident that your pipeline is working correctly, you can start iterating on models and hyperparameters. If you using an existing model, such as Faster R-CNN, you should start with the optimizer and the learning rate used in the original architecture before experimenting with different values. Similarly, I do not recommend using learning rate, annealing at first. I usually do not add any data augmentation until I'm confident that it is needed to train my model.

For example, if I see that my model is overfitting, I can start using data augmentation. Finally, you should experiment with different model sizes. For example, if you're overfitting your training set a lot, you can try to reduce your model size. If you think that your model is underperforming, you can try to increase its complexity. Hopefully, this provides a few guidelines to follow when training a deep neural network.

By training more models, you will eventually get the intuition of what works and what does not. The final project will be a good introduction to such processes.

## Additional Content

## Training Tips #2
When training a NN model on a new problem, following these steps might save yourself headaches:
- Become one with the data. Study and analyze your dataset in as much depth as possible
- Establish baselines
- Check your training pipelines
- Start with a simple model and don't use any training tricks, such as learning rate annealing
- Iterate based on your results

You can find an exhaustive check list to follow when training a new architecture [here](http://karpathy.github.io/2019/04/25/recipe/).
