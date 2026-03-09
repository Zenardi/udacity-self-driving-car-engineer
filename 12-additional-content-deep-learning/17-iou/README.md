# IoU

> Part of: **Scene Understanding**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=--9BTjOsO6U)

## Summary

**Intersection Over Union (IOU) Metric**
=====================================

The Intersection Over Union (IOU) metric is a widely used measure to evaluate the performance of models on semantic segmentation tasks. It calculates the ratio of correctly classified pixels to the total number of pixels in each class.

**Key Concepts**
---------------

* **Intersection**: The set of elements that exist in both sets, calculated using an AND operation.
* **Union**: The set of elements that exist in at least one of the two sets, calculated using an OR operation.
* **IOU Formula**: IOU = (Intersection) / (Union)
* **Mean IOU**: The average IOU for all classes, giving a comprehensive measure of model performance.

**Practical Notes**
------------------

To calculate IOU, you need to:

1. Calculate the intersection and union sets for each class.
2. Divide the intersection set by the union set to get the IOU ratio.
3. For multiple classes, calculate the mean IOU as the average of all individual IOU values.

Note: In practice, you can use matrix operations to efficiently calculate the mean IOU using functions like `matrix_mean_IOU`.

## Transcript

<v English>IOU, not the monetary kind,</v> <v English>is Intersection Over Union Metric,</v> <v English>commonly used to measure the performance of a model on the semantic segmentation task.</v> <v English>It is literally just the intersection set divided by the union set.</v> <v English>Intersection of two sets is an AND operation.</v> <v English>If it exists in both sets,</v> <v English>then we put it into the intersection set.</v> <v English>For each class, the intersection is defined as the number of pixels that are both</v> <v English>truly part of that class and are classified as part of that class by the network.</v> <v English>Union of the two set is a OR operation.</v> <v English>If it exists in at least one of the two sets,</v> <v English>then we put it into the union set.</v> <v English>The union is defined as the number of pixels that are truly part of that class</v> <v English>plus the number of pixels that are classified as part of that class by the network.</v> <v English>So, the intersection set should always be smaller or equal to the union set.</v> <v English>The ratio then tell us the overall performance per pixel, per class.</v> <v English>Since this intersection set is divided by the union set,</v> <v English>the ratio will always be less than or equal to one.</v> <v English>We can go even further and calculate the mean IOU for a network,</v> <v English>which is just the average of all the IOU for all the classes.</v> <v English>This gives you an idea of how well it handles</v> <v English>all the different classifications for every single pixel.</v> <v English>Intensive flow we can use matrix mean IOU function and call it directly.</v>
