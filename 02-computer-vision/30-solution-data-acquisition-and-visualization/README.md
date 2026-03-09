# Solution: Data Acquisition and Visualization

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=3TIS2QLuGn0)

## Summary

**Visualizing Images with Bounding Boxes**
======================================

This project involves implementing a function that displays a list of images in a grid and highlights color-coded bounding boxes using Matplotlib.

### Key Concepts

* **Colormap**: A dictionary that maps each class ID to an RGB triplet, used for color-coding bounding boxes.
* **Matplotlib patches**: Used to display bounding boxes on top of the images.
* **Subplots function**: Creates a grid layout for displaying multiple images.
* **Ground truth input**: A dictionary that stores data about the images, including their corresponding class IDs.

### Practical Notes

To implement this project, you will need to:

* Create a Colormap dictionary that maps each class ID to an RGB triplet
* Use the subplots function in Matplotlib to create a grid layout for displaying multiple images
* Loop through the different images and display them in the grid using Matplotlib patches to highlight bounding boxes

Example code:
```python
import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle

# Create a Colormap dictionary
colormap = {
    1: (255, 0, 0),  # Red for class ID 1
    2: (0, 255, 0),  # Green for class ID 2
    3: (0, 0, 255)   # Blue for class ID 3
}

# Create a grid layout using subplots function
fig, axs = plt.subplots(nrows=2, ncols=2)

# Loop through the different images and display them in the grid
for i, ax in enumerate(axs.flat):
    img = load_image(i)  # Load an image from disk
    ax.imshow(img)
    
    # Display bounding boxes using Matplotlib patches
    for box in get_bounding_boxes(i):  # Get the bounding boxes for the current image
        x, y, w, h = box
        rect = Rectangle((x, y), w, h, edgecolor='black', facecolor=colormap[box['class_id']])
        ax.add_patch(rect)
```
Note: The above code is a simplified example and may require modifications to fit your specific use case.

## Transcript

In this exercise, you are asked to implement a function that visualizes a list of images in a grid and displays color-coded bounding boxes using Matplotlib. I started by reformatting our ground_truth input to a dictionary to make the data more accessible. I then created a Colormap, in this case, a dictionary that maps each class ID to a RGB triplet. We can use the subplots function in Matplotlib to create a grid. We can loop through the different images to display them in the grid.

Using Matplotlib patches, we can display on each image, the different bounding boxes using the Colormap we created. Creating such visualization is extremely useful to better understand your data.

## Additional Content

## Solution: Data Acquisition and Visualization
```python
import glob
import json
import os

import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle
from PIL import Image

from utils import get_data


def viz(ground_truth):
    """
    create a grid visualization of images with color coded bboxes
    args:
    - ground_truth [list[dict]]: ground truth data
    """
    paths = glob.glob('data/images/*')

    # mapping to access data faster
    gtdic = {}
    for gt in ground_truth:
        gtdic[gt['filename']] = gt

    # color mapping of classes
    colormap = {1: [1, 0, 0], 2: [0, 1, 0], 4: [0, 0, 1]}

    f, ax = plt.subplots(4, 5, figsize=(20, 10))
    for i in range(20):
        x = i % 4
        y = i % 5

        filename = os.path.basename(paths[i])
        img = Image.open(paths[i])
        ax[x, y].imshow(img)

        bboxes = gtdic[filename]['boxes']
        classes = gtdic[filename]['classes']
        for cl, bb in zip(classes, bboxes):
            y1, x1, y2, x2 = bb
            rec = Rectangle((x1, y1), x2- x1, y2-y1, facecolor='none', 
                            edgecolor=colormap[cl])
            ax[x, y].add_patch(rec)
        ax[x ,y].axis('off')
    plt.tight_layout()
    plt.show()


if __name__ == "__main__": 
    ground_truth, _ = get_data()
    viz(ground_truth)
```
