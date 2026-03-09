# Region-Based CNNs (RCNNs) I

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=iHZ8Oefcdy0)

## Summary

**README: Selective Search and Region-Based Object Detection**

Selective search is an iterative algorithm used in computer vision for object detection. It generates regions from an image by grouping pixels together, which are then combined using a similarity criterion into larger regions.

### Key Concepts

* **Selective Search**: An iterative method that generates regions from an image by grouping pixels together.
* **Region Proposal Network (RPN)**: A network that extracts 2,000 region proposals from an input image using selective search.
* **Convolutional Neural Network (CNN)**: A neural network architecture used for object detection, which requires a fixed-size input.
* **Spatial Pyramid Pooling (SPP) Layer**: A layer that takes variable-size inputs and outputs a fixed-size feature vector by splitting the input into different fixed splits and applying max-pooling.

### Practical Notes

To implement selective search, you can use libraries such as OpenCV or scikit-image. The SPPNet architecture improves upon R-CNN by reusing feature maps calculation and removing the need for resizing regions, resulting in a significant speed improvement (up to 100x faster).

**Example Code**
```python
import cv2

# Load image
img = cv2.imread('image.jpg')

# Apply selective search
regions = cv2.selective_search(img)

# Use SPP layer to extract features from regions
spp_layer = cv2.SPPLayer()
features = spp_layer.extract_features(regions)
```
Note: This is a simplified example and actual implementation may vary depending on the specific requirements of your project.

## Transcript

Even though the focus on this lesson is on deep learning-based algorithm, I always think that mentioning classic computer vision approaches is important. Indeed, the challenge of object detection existed long before the deep learning revolution. Selective search is one of the algorithm that were used to perform object detection before convolutional neural network. Selective search is an iterative method that consists in generating region from an image by grouping pixels together. Such regions are then combined using a similarity criterion into larger region, and this process is repeated.

Finally, the algorithm uses a support vector machine algorithm to classify the region. We can see selective search in action here. Deep learning method have been yielding to much better performances. However, the first iteration of deep learning-based object detection algorithm is relying on selective search. Therefore, I believe it's important for you to know about this algorithm.

But enough said. Let's now dive into the first class of object detection algorithm using COVNETS, the region-based convolutional neural network or R-CNN. The main idea behind the 2014 R-CNN paper is the following: Given an input image, we extract 2,000 region proposal using selective search. Such regions are then fed into a convolutional neural network similar to the one we have built in the previous lesson. Because most CNN take a fixed size input, we have to resize said regions before feeding them into the network.

This network will then classify the region as being an object or not, and also output the class of this object. It is a very simple, yet powerful idea. It is also worth noting that the author experimented with a regression model to get final results on the bounding box coordinates. What are the limitation of such an algorithm? Well, first, it relies on selective search, which is a relatively slow algorithm.

Then it requires resizing the region created by selective search, which create a loss of information, and will decrease the quality of the classification of the neural network. Despite these default, the R-CNN object detector was a groundbreaking paper in the field of object detection. By the way, the convolutional neural network part of an object detection algorithm is called the backbone. In the next videos, we're going to see how the author of the paper iterated on the method to create one of the most popular object detector to date. Before we tackle the second iteration of the R-CNN model, I wanted to mention another architecture called the SPPNet.

SPP stands for spatial pyramid pooling. The main contribution of SPPNet to the object detection task is the ability to remove the resizing step of the R-CNN architecture and by doing so, reducing the cost of computation. Let's take a step back together and remember why convolutional neural network need a constant size input. Well, the dimension of the output volume of a convolutional neural network depends on its input shape. However, at the end of a convolutional neural network, we have a stack of fully connected layers as we have seen previously.

Such layers take a fixed size input. Therefore, we need a fixed size input for the convolutional layer. Here come the SPP layer to the rescue. This layer takes a variable-size input and outputs a fixed-size feature vector. How does this work?

Well, let's consider a variable-size input. The SPP layer will split such an image using different fixed splits. In this example, we are using two splits, a two-by-two, and a two-by-three. We can then use a max-pooling layer to calculate the maximum of each one of the splits. We went from a variable-size image to a two-by-two and a two-by-three fixed size outputs.

We can use different filter sizes, such as three-by-three or one-by-one. By the way, given that we are using two splits here, the spatial pooling layer, who we describe as a two-level SPP layer. Let's summarize what the SPP layer is doing. It splits available size inputs and pull the splits to create a fixed-size vector. Let's see how the SPP layer fits in our object detection algorithm.

SPPNet differ from R-CNN in the following ways. It starts similarly to the R-CNN model by calculating regions using selective search. However, instead of resizing and feeding each one of the region to the ConvNet, SPPNet uses the full image to feed into the ConvNet. The output of the last convolutional layer is then cropped using each region obtained by the selective search. This region are then fed into SPP layer, and therefore, given a fixed size output vector that can be used by the classifier.

We need to keep in mind that the SPP layer is applied to each channel of the ConvNet output. Let's use our previous example, and assume that we use a two-by-two and a two-by-three split in our SPP layer, and let's assume that the output of the ConvNet has 256 channel. For each region of the selective search, we are creating an output of dimension 256 by 10. How is this an improvement over the R-CNN approach? Well, first, we are reusing the feature maps calculation instead of feeding each region into the ConvNet directly.

Moreover, we do not need to resize each region anymore. While maintaining similar performances, the SPPNet improve the speed of R-CNN by a factor up to 100. The author of the R-CNN paper used this novel approach for the next iteration of region-based ConvNet, Fast R-CNN.

## Additional Content

## Region-Based CNNs (RCNNs) I

### Selective Search
The first iterations of object detection algorithms relied on **selective search**, an [iterative algorithm](http://www.huppelen.nl/publications/selectiveSearchDraft.pdf) that segment regions in an image. 

The first paper of the **Region-Based CNN (RCNN)** family used regions created by selective search as inputs to a convolutional neural network. This [2014 paper](https://arxiv.org/pdf/1311.2524.pdf) takes the regions created by selective search and resizes them to a fixed size resolution before feeding it into a CNN.

Despite being a breakthrough in terms of performances, this architecture still has some downsides:
- The need to resize each region to fixed-size input
- The need to recompute CNN features for each region
- It is slow because it relies on selective search
### SPPNet
[SPPNet](https://arxiv.org/abs/1406.4729) introduced a new type of layer to remediate some of the issues of the RCNN architecture: the **spatial pyramid pooling (SPP)** layer. This layer takes a variable size input and creates a fixed-size input. 

Let's consider an example of a 4 level SPP layer with a `1x1`, `2x2`, `2x3` and `4x4` split. We feed a 2D array to this layer. This array will be pooled using each one of these splits, creating a  vector of dimensions`1x1 + 2x2 + 2x3 + 4x4 = 27`. No matter the resolution of the input image, the output vector will always be a `27x1` vector. 

SPPNet also takes a different approach than RCNN by reusing the CNN feature. Indeed, instead of feeding the cropped input image, the entire image is fed to the CNN and the selective search regions are used to crop the final feature maps. These regions are then fed to a SPP layer. By doing so, SPPNet gets similar performances to RCNN while improving the inference time by almost 100 times.
