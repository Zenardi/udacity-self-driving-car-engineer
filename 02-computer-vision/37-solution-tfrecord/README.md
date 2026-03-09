# Solution: TFRecord

> Part of: **The Machine Learning Workflow**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=8O6f-Vnii2c)

## Summary

**Converting TF Records between Formats**
=====================================

This project involves implementing a function that converts TF records in the Way More Open dataset format to a different TF record format. The goal is to adapt the data format for use with various machine learning libraries.

### Key Concepts
* **TF Record**: A binary file format used by TensorFlow for storing and loading data.
* **Way More Open Dataset**: A specific dataset that stores annotations using class names instead of IDs, and bounding boxes with center coordinates.
* **Protocol Messages**: Data structures used to represent input data in a format compatible with machine learning libraries.
* **Class Mapping**: A dictionary mapping class names to their corresponding IDs.

### Practical Notes
To implement the conversion function:

1. Load the encoded image into memory using Python's input-output library (e.g., `io` module).
2. Use Pillow to open and extract the image dimensions (width, height).
3. Map class names to IDs using the provided class mapping.
4. Convert bounding box coordinates from center-based to corner-based format by adjusting x and y values.
5. Create protocol messages for the converted data using the provided functions.
6. Combine the protocol messages into a TF train example.

Note that this process involves understanding the specific requirements of each dataset format and adapting the data accordingly.

## Transcript

In this exercise, you are asked to implement a function that converts the TF record in the way more open data set format to a different TF record format. This function takes as input the file name of the original TF record, an encoded jpeg image in a byte like format, and the list containing annotations. First, we need to load the encoded image in a memory buffer using Python input-output library. We can then open this image with Pillow and extract the image widths and height. We use the provided class mapping to map classes name to classes IDs.

Indeed, the way more open data set only contain the classes name. We then need to convert the annotation in the right format. In a way more open data sets, bounding boxes use the center coordinates instead of the corner coordinates. We convert them to the wanted format by adding or subtracting half of the lengths and half of the widths. Multiple bounding boxes format exist and this is an operation you will have to do pretty frequently.

Finally, we need to create the different protocol messages using the provided functions. We put these protocol messages into a TF train example. Because different machine learning libraries require different data formats, you need to become comfortable converting data from one format to another.

## Additional Content

## Solution: TFRecord
```python
import io
import os

import tensorflow.compat.v1 as tf
from PIL import Image
from waymo_open_dataset import dataset_pb2 as open_dataset

from utils import parse_frame, int64_feature, int64_list_feature, bytes_feature \
    bytes_list_feature, float_list_feature


def create_tf_example(filename, encoded_jpeg, annotations):
    """
    convert to tensorflow object detection API format
    args:
    - filename [str]: name of the image
    - encoded_jpeg [bytes-likes]: encoded image
    - annotations [list]: bboxes and classes
    returns:
    - tf_example [tf.Example]
    """
    encoded_jpg_io = io.BytesIO(encoded_jpeg)
    image = Image.open(encoded_jpg_io)
    width, height = image.size
    
    mapping = {1: 'vehicle', 2: 'pedestrian', 4: 'cyclist'}
    image_format = b'jpg'
    xmins = []
    xmaxs = []
    ymins = []
    ymaxs = []
    classes_text = []
    classes = []
    filename = filename.encode('utf8')
    
    for ann in annotations:
        xmin, ymin = ann.box.center_x - 0.5 * ann.box.length, 
                     ann.box.center_y - 0.5 * ann.box.width
        xmax, ymax = ann.box.center_x + 0.5 * ann.box.length,  
                     ann.box.center_y + 0.5 * ann.box.width
        xmins.append(xmin / width)
        xmaxs.append(xmax / width)
        ymins.append(ymin / height)
        ymaxs.append(ymax / height)    
        classes.append(ann.type)
        classes_text.append(mapping[ann.type].encode('utf8'))

    tf_example = tf.train.Example(features=tf.train.Features(feature={
        'image/height': int64_feature(height),
        'image/width': int64_feature(width),
        'image/filename': bytes_feature(filename),
        'image/source_id': bytes_feature(filename),
        'image/encoded': bytes_feature(encoded_jpeg),
        'image/format': bytes_feature(image_format),
        'image/object/bbox/xmin': float_list_feature(xmins),
        'image/object/bbox/xmax': float_list_feature(xmaxs),
        'image/object/bbox/ymin': float_list_feature(ymins),
        'image/object/bbox/ymax': float_list_feature(ymaxs),
        'image/object/class/text': bytes_list_feature(classes_text),
        'image/object/class/label': int64_list_feature(classes),
    }))
    return tf_example


def process_tfr(path):
    """
    process a waymo tf record into a tf api tf record
    """
    # create processed data dir
    file_name = os.path.basename(path)

    logger.info(f'Processing {path}')
    writer = tf.python_io.TFRecordWriter(f'{dest}/{file_name}')
    dataset = tf.data.TFRecordDataset(path, compression_type='')
    for idx, data in enumerate(dataset):
        frame = open_dataset.Frame()
        frame.ParseFromString(bytearray(data.numpy()))
        encoded_jpeg, annotations = parse_frame(frame)
        filename = file_name.replace('.tfrecord', f'_{idx}.tfrecord')
        tf_example = create_tf_example(filename, encoded_jpeg, annotations)
        writer.write(tf_example.SerializeToString())
    writer.close()


if __name__ == "__main__": 
    parser = argparse.ArgumentParser()
    parser.add_argument('-p', '--path', required=True, type=str,
                        help='Waymo Open dataset tf record')
    args = parser.parse_args()  
    process_tfr(args.path)
```
## Extra Resources
- [TFRecord tutorial](https://www.tensorflow.org/tutorials/load_data/tfrecord)
