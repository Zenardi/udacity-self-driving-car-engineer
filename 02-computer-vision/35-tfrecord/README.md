# TFRecord

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=RCiDNt_loRE)

## Summary

**TF Records: A Custom Data Format for TensorFlow**

This lesson introduces you to **TF Records**, a custom data format used in TensorFlow. While not required for training models with TensorFlow, TF Records can help speed up data loading when working with large datasets.

### Key Concepts

* **TF Records**: A custom data format used in TensorFlow to store and load data efficiently.
* **Protofiles**: Files that define the structure of TF Records using protocol buffers (protobuf).
* **Protocol Buffers (protobuf)**: A mechanism for serializing data, used to create and parse TF Record files.
* **tf.train.Example**: A TensorFlow function used to create TF Record files from custom data formats.

### Practical Notes

To work with TF Records in your final project, you'll need to understand how to leverage protofiles to define the structure of your data. You can use protocol buffers (protobuf) to serialize and deserialize your data, making it easier to load into TensorFlow models. Additionally, you can create TF Record files from your own custom data formats using the `tf.train.Example` function.

**Example Protofile**
```proto
message CameraName {
  enum CameraType {
    UNKNOWN = 0;
    FRONT = 1;
    FRONT_LEFT = 2;
    FRONT_RIGHT = 3;
    SIDE_LEFT = 4;
    SIDE_RIGHT = 5;
  }

  CameraType camera_type = 1 [default = UNKNOWN];
}
```
This protofile defines the structure of a TF Record file, including the `CameraName` field with its corresponding attributes.

## Transcript

Let's take a break from the theory and spend some time talking about TF records. TF records are TensorFlow custom data format. They are not necessarily required to train model with TensorFlow, but may help when data loading becomes a bottleneck. Also, the data in the Waymo Open Dataset is using the TFRecord format, and you will be using that format for your final project. Whereas XML or JSON format are human readable, TF records files are not.

For example, let's try to open this TF record. As you can see, this file is not human readable. However, we can use protofiles to understand the structure of these TF records. Let's look at an example of a protofile from the Waymo Open Dataset. This protofile describes the structure of a TF record.

Well, from this profile, I see that the TF record contains a field called CameraName, which has the following six attributes; UNKOWN, FRONT, FRONT_LEFT, FRONT_RIGHT, SIDE_LEFT, and SIDE_RIGHT. Looking at this protofile is extremely informative, and you will have to learn how to leverage them for the final project. By the way, you can create TF records files from your own data format. To do so, you will have to leverage a TensorFlow function called tf.train.Example. You will learn about this in the next exercise.

Let's summarize what we have learned about TF records. TF records are TensorFlow custom data formats. They are not required to train a model with TensorFlow, but they may help to speed up data loading. Their structure is defined by protofiles. TF records are created using protocol buffers or proto buff, a mechanism to serialize data.

## Additional Content

## TFRecord
**TF Records** are TensorFlow's custom data format. Even though they are not technically required to train a model with TensorFlow, they can be very useful. For some pre-existing TensorFlow APIs, such as the object detection API that we will use for the final project, a TF Record format is required to train models. 
### Waymo Open Dataset vs. TensorFlow Object Detection API

In the final project of this course, you will use data from the Waymo Open Dataset with the TensorFlow Object Detection API to perform object detection on camera images. While each use `.tfrecord` files, there is a difference in the structure of each. As such, the upcoming exercise will have you take a `.tfrecord` from the Waymo Open Dataset and convert it into a new `.tfrecord` useable by the TensorFlow Object Detection API.

While also linked in the exercise itself, you'll need a few resources to be able to do so more easily.

- First, [this repository](https://github.com/Jossome/Waymo-open-dataset-document) gives some additional information around the Waymo Open Dataset itself (note that Waymo link to https://waymo.com/open/data/ therein now should be https://waymo.com/open/data/perception, as Waymo has also added a "motion" component to the previous perception-only dataset).
- Secondly, [this tutorial for the TF Object Detection API](https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/training.html#create-tensorflow-records) for converting from `.xml` to `.tfrecord` also shows certain steps that will apply in our case as well.

This exercise will require some research on your own of the above documentation (and potentially other documentation) to reach a converted file; however, if you get stuck, it is perfectly reasonable to skip ahead to the solution video for some assistance.
### Additional Resources

- [Using TFRecord and `tf.train.Example` from the TensorFlow documentation](https://www.tensorflow.org/tutorials/load_data/tfrecord)

The above documentation will be useful to refer to as you work on the upcoming exercise.
