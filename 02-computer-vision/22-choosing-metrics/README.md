# Choosing Metrics

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Mdc0cS033Sc)

## Summary

**Machine Learning Metrics for Classification and Object Detection**
====================================================================

This project focuses on evaluating the performance of machine learning models using various metrics. These metrics are crucial in understanding how well a model is performing on a specific task.

### Key Concepts

* **True Positive (TP)**: When the image contains a burger and the model predicts a burger.
* **True Negative (TN)**: When the image does not contain a burger and the model does not predict a burger.
* **False Positive (FP)**: When the image does not contain a burger, but the model predicts a burger.
* **False Negative (FN)**: When the image contains a burger and the model does not predict a burger.
* **Precision**: The ratio of true positives to the sum of true positives and false positives. It measures the error rate when predicting a specific class.
* **Recall**: The ratio of true positives to the sum of true positives and false negatives. It measures the error rate when the actual class is present.
* **Accuracy**: A metric that gives the total error rate, measuring how good the algorithm is at predicting classes correctly.

### Practical Notes

To calculate these metrics, you need to create a confusion matrix, which displays the counts for each metric. The following example illustrates this:

|  | Predicted Burger | Not Burger |
| --- | --- | --- |
| **Actual Burger** | TP (1) | FN (0) |
| **Not Burger** | FP (1) | TN (2) |

In this example, we have one true positive, one false positive, and two true negatives. The precision would be 0.5 (TP / (TP + FP)), recall would be 1 (TP / (TP + FN)), and accuracy would be 2/3 ((TP + TN) / (TP + TN + FP + FN)).

Note: This is a simplified example, and you will perform more complex calculations on larger datasets later in the course.

## Transcript

Now that we have a better understanding of our problem, we need to evaluate how good we are at solving it. To evaluate our solution, we want to create a set of metrics. Keep in mind that these metrics may be different from the ones you will use to evaluate your algorithm performances. A good metric must be easy to understand and adapted to a specific problem. In the case of traffic sign classification, metrics like accuracy, or recall, may be used to evaluate the model's performance.

But we may be putting more weights in accurately classifying certain traffic signs than other. For example, misreading speed limit signs can result in a speeding ticket, or a missed up sign can lead to an accident. Whereas Machine Learning Metrics, like accuracy, can generalize well across problems. You may need to find custom business metrics that best fit your situation. Let's take a step back from the traffic sign classification problem and tackle an even simpler problem.

You're creating a phone app that classifies an image as containing a burger or not. Let's go over some definition of Machine Learning Metric. A true positive or TP is when the image contains a burger and the model predicts the burger. A true negative or TN is when the image does not contain a burger and the model does not predict a burger. A false positive, or FP is when the image does not contain a burger, but the model predicts burger.

Finally, a false negative or FN is when the image contains a burger and the model does not predict burger. Let's go over this definition one more time. This is the picture of a burger and our algorithm detected a burger. We have a true positive. In the second case, we have a picture of a hot dog, but our algorithm predicted a burger.

This is a false positive. In this third example, we have a picture of a burger, but our algorithm is classifying it as not burger, which is a false negative. Finally, the last picture contains a dog, and our algorithm does not classify it as a burger, making it a true negative. A two-by-two matrix, such as the one shown here, where we display the counts for each metric is called a confusion matrix. True positive, false positive, false negative, and true negatives are the building blocks of many Machine Learning Metrics.

It is critical that you have a good understanding of them. False negative and false positive are sometime used by themselves, but they are often combined to create the following metrics. First of all, let's talk about precision. Precision is defined as the ratio of a true positives plus false positives. It is going to give the error rate of our algorithm when it's predicting a hamburger.

The recall is defined as the ratio of true positives over true positives plus false negatives. It indicates the error rate when the picture is a burger. Finally, accuracy is a metric that will give us the total error rate, meaning how good our algorithm is at predicting burgers and not burgers. Precision, recall, and accuracy are being used for many different categories of machine learning problem, such as classification, semantic segmentation, or object detection. Therefore, it is critical that you have a good understanding of them.

Let's now consider an example. We have three images. The first image contains a burger, and a burger is predicted. The second image contains a hot-dog, and not burger is predicted. The last one contains a steak, and burger is predicted.

We therefore have one true positive, one true negative, and one false positive, giving us a precision of 0.5, a recall of one, and an accuracy of two-thirds. You will perform such calculation over the entire traffic sign data-set later in this course. Later on, we will focus on object detection. But now is a good time to introduce some metrics definition for this task. Let's look at this image from the Waymo data-set and let's consider that we're building an algorithm that detects cars.

The red boxes are the ground-truth and the green dash boxes are the models detections. As we can see, one of the detection is not a car but a traffic sign. The precision of our algorithm for this image is four out of five and the recall is one because all the cars in this image are detected. How do we define true positive in the context of object detection? By using something called intersection over union or IOU.

Let's consider these two bounding boxes. The IOU is defined as the ratio of the intersection of these bounding boxes and the union of these bounding boxes. An IOU of 0.5 between a ground-truth bounding box and a detected bonding box is a pretty common threshold to qualify the detection as a true positive. The IOU is a very important concept when it comes to object detection. It will not only be used to define true positives, but will also be used in algorithm such as non-max suppression, which we will tackle later on in this course.

## Additional Content

## Choosing Metrics
Each Machine Learning problem requires its own metrics, and whereas some metrics like **Accuracy** may be suited for many problems, you need to keep in mind the consequences of misprediction. Let's consider the following: you are building a spam classification algorithm. Well, you should aim for very few **False Positives**, because you do not want your algorithm to classify some potentially important emails to your spam folder. A **False Negative** however is simply a spam located in your inbox, which could be manually removed by the user.


### Classification & Object Detection Metrics
> **Correction at 2:03**: Green boxes are ground truth, and red dotted boxes are model's predictions.

$$Precision = \frac{TP}{TP + FP}$$

**Precision:** Of the elements classified as a particular class, how many did we get right? For example, we classified 6 images as containing burgers and only 5 of them actually contain a burger. The precision is `5/6`.

$$Recall = \frac{TP}{TP + FN}$$

**Recall:** The number of images classified correctly divided by the total number of images. For example, we have 40 images of burgers and we classified 15 of them correctly. The recall is `15/40`. 

We use the same definitions of precision and recall for object detection but instead we consider the number of instances of an object per image.

$$Accuracy = \frac{TP + TN}{TP + FN + FP + TN}$$

**Accuracy:** (Only for classification problems) The number of correctly classified images over the total number of images.
