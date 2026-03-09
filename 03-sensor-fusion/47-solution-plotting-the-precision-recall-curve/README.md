# Solution: Plotting the Precision & Recall Curve

> Part of: ** Detecting Objects in Lidar**

## Additional Content

## Solution: Plotting the Precision & Recall Curve
Here is my approach (there are multiple potential ways to accomplish this):

```python
def plot_precision_recall(): 

    # Please note: this function assumes that you have pre-computed the precions/recall value pairs from the test sequence
    #              by subsequently setting the variable configs.conf_thresh to the values 0.1 ... 0.9 and noted down the results.
    
    # Please create a 2d scatter plot of all precision/recall pairs 
    import matplotlib.pyplot as plt
    P = [0.97, 0.94, 0.93, 0.92, 0.915, 0.91, 0.89, 0.87, 0.82]
    R = [0.738, 0.738, 0.743, 0.746, 0.746, 0.747, 0.748, 0.752, 0.754]
    plt.scatter(R, P)   
    plt.show()
```
