# Solution: Lidar Data in the Waymo Dataset

> Part of: **The Lidar Sensor**

## Additional Content

## Solution: Lidar Data in the Waymo Dataset
Here is my approach:

```python
def print_no_of_vehicles(frame):
    
    num_vehicles = 0
    for label in frame.laser_labels:
        if label.type == label.TYPE_VEHICLE:
            num_vehicles = num_vehicles + 1
            
    print("number of labeled vehicles in current frame = " + str(num_vehicles))
```
