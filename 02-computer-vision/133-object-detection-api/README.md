# Object Detection API

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=67ndg9bAOWE)

## Summary

**TensorFlow Object Detection API**
=====================================

The TensorFlow Object Detection API provides a simple interface for training object detection models, allowing users to experiment with different configurations without having to code them from scratch.

### Key Concepts

* **Object Detection Models**: More complex than classification models, requiring specialized APIs like the TensorFlow Object Detection API.
* **Config Files**: A single file that dictates the dataset, model, and hyperparameters for training, making experimentation easy.
* **Pretrained Models**: The API comes with a "zoo" of pretrained models on ImageNet, allowing users to leverage transfer learning.
* **Model Definition**: The config file's first section, describing the model type, input dimensions, backbone, and other parameters.
* **Train Config**: The second part of the config file, requiring editing for custom datasets, including updating pre-trained model paths and fine-tuning checkpoints.
* **Data Augmentation**: Experimenting with different augmentation types for the final project, available in the TensorFlow object detection API's proto file.
* **Input Readers**: Two input readers (train_input_reader and eval_input_reader) with the same structure, requiring a label map and training files' paths.

### Practical Notes

To train a model on a custom dataset using the TensorFlow Object Detection API:

1. Create a label map file containing class name to ID mappings.
2. Provide the path to the training files (TensorFlow records).
3. Edit the config file's model definition, train config, and input readers sections as necessary.

Additionally, users can leverage TensorBoard for visualization of losses, metrics, and model outputs during training by launching a TensorBoard server using the instructions provided below the video.

## Transcript

In the following videos, we are going to learn how to use the TensorFlow Object Detection API. What is this API? Well, it provides a simple interface to train object detection models. As we have seen at the beginning of this lesson, object detection models are much more complex than classification models, and we will not ask you to code them from scratch. Instead, we'll be using this API.

One great thing about the TensorFlow object detection API is the fact that it uses config files. A single file is going to dictate the dataset, the model, and the hyperparameter, making it extremely easy to experiment. The TensorFlow object detection API also comes with a zoo of pretrained model. We won't have to train models from scratch and we can use transfer learning from pretrained model on ImageNet. Let's start by looking at the structures of the config files.

Let's look at the config file of a faster R-CNN model with a ResNet-101 backbone. One great thing about the TensorFlow object detection API is the minimal amount of modification we have to make to train a model on a custom dataset. The config file begins with the model definition. This section will describe the type of model, as well as the input dimension, the backbone, and many other parameters. If we want to keep the exact same model, we just need to edit the number of classes filled.

Right now, the model is ready to be trained on the COCO dataset, which has 90 classes. We can edit this value to adjust it to our problem. The second part of the config that we need to edit is the train config. Because we are using transfer learning, we need to download one of the pre-trained model from the model zoo and update the absolute plus of that model in the config file. This is exactly what the fine-tune checkpoint field is about.

Moreover, you may need to experiment with different types of augmentation for the final project. You can add them to the data augmentation option field highlighted. Finding the list of augmentation available in the TensorFlow object detection API is a little challenging, and I added the link to the proto file listing them below this video. The last thing we have to edit in our config files are the input readers. We have two of them: the train_input_reader and the eval_ input_reader.

But both of them have the same structure. To get the model to train on our custom dataset, we first need to create a file called a label map. This file simply contains a mapping of the classes name to predefined ID. The label map would be provided for the final project. Bur you can look at the TensorFlow object detection API tutorial if you're curious about its structure.

Finally, we have to provide the path to the training files, which are TensorFlow records. If you were to train an out-of-the-box faster R-CNN model, we just saw the minimum amount of editing of the config files you have to make to train this model on a custom dataset. TensorFlow has its own visualization tool called TensorBoard. TensorBoard allows the user to visualize losses, metrics, and model outputs during training. In previous lessons, I mentioned how important it was to babysit the training of your deep learning model, where thanks to TensorBoard, it is now extremely easy.

Launching your own TensorBoard server is a simple task and I included some instruction below the video. You will learn how to leverage TensorBoard power in the final project.

## Additional Content

## Object Detection API
The **Tensorflow Object Detection API** provides a simple interface to develop and train object detection models in TensorFlow. It uses a single **config file** to describe the entire training pipeline, including the model architecture, the different datasets and hyperparameters. 
### Demo: Object Detection API
The config file described in this video is located [here](https://github.com/tensorflow/models/blob/master/research/object_detection/configs/tf2/faster_rcnn_resnet101_v1_640x640_coco17_tpu-8.config). 

- model: contains the description of the model architecture (eg: model name, backbone)
- train_config: contains the training parameters (eg: batch size)
- train_input_reader: contains the training files locations
- eval_config: contains the eval parameters (eg: metrics)
- eval_input_reader: contains the eval files locations
### Demo: Tensorboard
**Tensorboard** is TensorFlow's custom dashboard to monitor the training of your models. You simply launch a Tensorboard server by running `tensorboard --logdir

` where `LOGDIR` is the location of your log files.
