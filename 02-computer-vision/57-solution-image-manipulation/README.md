# Solution: Image Manipulation

> Part of: **Sensor and Camera Calibration**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=x7mUqEsC2IA)

## Summary

**Image Processing with Pillow and NumPy**
=====================================

This project demonstrates how to work with images using the Pillow and NumPy libraries in Python. We will cover two main topics: creating binary masks of RGB images and calculating statistics over lists of images, as well as plotting histograms of pixel values.

### Key Concepts

* **Binary Mask**: A binary mask is a grayscale image where each pixel has a value of either 0 (black) or 255 (white), used to highlight specific regions in an image.
* **RGB Image Conversion**: Converting an image to RGB format using Pillow's `Image.open()` function.
* **NumPy Array Operations**: Using NumPy arrays and operations, such as bitwise and comparison operators, to create binary masks.
* **Matplotlib Subplots**: Displaying multiple images side-by-side using Matplotlib subplots.
* **NumPy Broadcasting Rules**: Leveraging NumPy broadcasting rules to create masked images.
* **Image Statistics**: Calculating statistics (mean, variance, standard deviation) over lists of images using Pillow's `image stat` module or NumPy.
* **Histogram Plotting**: Plotting histograms of pixel values for each channel in an image using Seaborn.

### Practical Notes

To implement the binary mask and display functions:

1. Convert the Pillow image to a NumPy array using `np.array()` function.
2. Use bitwise and comparison operators to create a binary mask from the RGB image.
3. Display the original RGB image and the binary mask side-by-side using Matplotlib subplots.

For calculating statistics over lists of images:

1. Use Pillow's `image stat` module or NumPy to calculate mean, variance, and standard deviation for each image.
2. Note that the `image stat` module does not output variance directly; use the square root function to get standard deviation from variance.

For plotting histograms:

1. Open each image individually using Pillow and extract the channels as 2D arrays.
2. Flatten the channels and save them in a list for histogram plotting.
3. Use Seaborn to display the distribution of pixel values for each channel.

## Transcript

Let's go over the solution of this exercise together. In the first section of this exercise, you were asked to implement two functions; one is creating a binary mask of an RGB image using a color threshold. Then, you were asked to display that mask alongside the original RGB image. This is how I implemented the create masks function. Make sure to always convert to RGB when opening an image with Pillow.

I converted the Pillow image to a NumPy array and used this array to create a binary mask using Python, bitwise, and comparison operators. The display function is using Matplotlib subplots. I'm leveraging NumPy broadcasting rules to create the masked image. For both functions, you could have taken an approach based on Pillow only to create the mask and mask the image. In the second part of this exercise, you were asked to calculate statistics over a list of images as well as create a function that plots the histogram of pixel value of each channel.

I leveraged the image stat module of Pillow to calculate the statistics for each image. You could also have used NumPy for this task. I used the square root function to get the standard deviation from the variance because image stat does not output the variance. For the histogram, I am opening each image individually and extracting the channels as 2D arrays. I flatten those channels and save them in a list.

I use the seaborne library to display the distribution. Seaborne is a great addition to Matplotlib for creating visualization in Python.

## Additional Content

## Solution: Image Manipulation
`masking.py`

```python
import matplotlib.pyplot as plt
import numpy as np
from PIL import Image


def create_mask(path, color_threshold):
    """
    create a binary mask of an image using a color threshold
    args:
    - path [str]: path to image file
    - color_threshold [array]: 1x3 array of RGB value
    returns:
    - mask [array]: binary array
    """
    img = np.array(Image.open(path).convert('RGB'))
    R, G, B = img[..., 0], img[..., 1], img[..., 2]
    rt, gt, bt = color_threshold
    mask = (R > rt) & (G > gt) & (B > bt) 
    return img, mask


def mask_and_display(img, mask):
    """
    display 3 plots next to each other: image, mask and masked image
    args:
    - img [array]: HxWxC image array
    - mask [array]: HxW mask array
    """
    masked_image = img * np.stack([mask]*3, axis=2)
    f, ax = plt.subplots(1, 3, figsize=(15, 10))
    ax[0].imshow(img)
    ax[1].imshow(mask)
    ax[2].imshow(masked_image)
    plt.show()


if __name__ == '__main__':
    path = 'data/images/segment-1231623110026745648_480_000_500_000_with_camera_labels_38.png'
    color_threshold = [128, 128, 128]
    img, mask = create_mask(path, color_threshold)
    mask_and_display(img, mask)
```
`statistics.py`

```python
import glob

import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
from PIL import Image, ImageStat

from utils import check_results


def calculate_mean_std(image_list):
    """
    calculate mean and std of image list
    args:
    - image_list [list[str]]: list of image paths
    returns:
    - mean [array]: 1x3 array of float, channel wise mean
    - std [array]: 1x3 array of float, channel wise std
    """
    means = []
    stds = []
    for path in image_list:
        img = Image.open(path).convert('RGB')
        stat = ImageStat.Stat(img)
        means.append(np.array(stat.mean))
        stds.append(np.array(stat.var)**0.5)
    
    total_mean = np.mean(means, axis=0)
    total_std = np.mean(stds, axis=0)

    return total_mean, total_std


def channel_histogram(image_list):
    """
    calculate channel wise pixel value
    args:
    - image_list [list[str]]: list of image paths
    """
    red = []
    green = []
    blue = []
    for p in image_list:
        img = np.array(Image.open(p).convert('RGB'))
        R, G, B = img[..., 0], img[..., 1], img[..., 2]
        red.extend(R.flatten().tolist())
        green.extend(G.flatten().tolist())
        blue.extend(B.flatten().tolist())

    sns.kdeplot(red, color='r')
    sns.kdeplot(green, color='g')
    sns.kdeplot(blue, color='b')


if __name__ == "__main__": 
    image_list = glob.glob('data/images/*')
    mean, std = calculate_mean_std(image_list)
    check_results(mean, std)
```
