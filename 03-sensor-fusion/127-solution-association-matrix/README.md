# Solution: Association Matrix

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=-eh8X3b2yFE)

## Summary

**Association Metrics and Mahalanobis Distance**
====================================================

This project involves calculating the Mahalanobis distance between tracks and measurements using a given algorithm.

### Key Concepts
* **Infinity values**: Initializing association metrics with infinity values to ensure all distances are initially set to maximum.
* **MHD function**: A function that takes two measurement matrices `H` and returns their 2D position components.
* **Residual gamma and covariance**: Calculating the residual gamma and its covariance as usual, using the given formulas.
* **Mahalanobis distance**: Calculating the Mahalanobis distance from gamma and S.
* **Association matrix**: A matrix that stores the calculated distances between tracks and measurements.

### Practical Notes
To implement this project, you will need to:

* Initialize association metrics with infinity values
* Loop over all tracks and measurements, calling the MHD function for each pair
* Calculate residual gamma and covariance using given formulas
* Calculate Mahalanobis distance from gamma and S
* Use the resulting association matrix to determine which track will be updated first

Note: The code pattern involves looping over two lists (tracks and measurements), calling a specific function (MHD) for each pair, and storing the results in an association matrix.

## Transcript

Here's my solution. After initializing the association metrics with infinity values, we loop over all N tracks in the track list, and over all M measurements in the measurement list. For each pair, we call the MHD function and restore the result in the association metrics. The MHD function needs the two by far measurement matrix H to reduce the farthest state to its 2D position components. Then we calculate the residual gamma and its covariance as usual.

From gamma and S, we can calculate the Mahalanobis distance, that's it. Let's see how the output looks like. The script now links all associated track measurement paths with gray lines and writes the calculated MHD next to it. It is interesting to see how the Mahalanobis distance differs from the standard Euclidean distance, for example, track one here would be closest to measurement three if you use the Euclidean distance. But according to the Mahalanobis distance, track one is closer to measurement two.

The Mahalanobis distance is 2.7 as compared to 2.9 for measurement three. We can also see in the console output, how the resulting association matrix looks like. Can you tell me which track will be updated first?

## Additional Content

## Solution: Association Matrix
```python
import numpy as np
import matplotlib
matplotlib.use('wxagg') # change backend so that figure maximizing works on Mac as well   
import matplotlib.pyplot as plt
import matplotlib.ticker as ticker

class Association:
    '''Data association class with single nearest neighbor association and gating based on Mahalanobis distance'''
    def __init__(self):
        self.association_matrix = np.matrix([])
        
    def associate(self, track_list, meas_list):
        N = len(track_list) # N tracks
        M = len(meas_list) # M measurements
        
        # initialize association matrix
        self.association_matrix = np.inf*np.ones((N,M)) 
        
        # loop over all tracks and all measurements to set up association matrix
        for i in range(N): 
            track = track_list[i]
            for j in range(M):
                meas = meas_list[j]
                dist = self.MHD(track, meas)
                self.association_matrix[i,j] = dist
        
    def MHD(self, track, meas):
        # calc Mahalanobis distance
        H = np.matrix([[1, 0, 0, 0],
                       [0, 1, 0, 0]]) 
        gamma = meas.z - H*track.x
        S = H*track.P*H.transpose() + meas.R
        MHD = gamma.transpose()*np.linalg.inv(S)*gamma # Mahalanobis distance formula
        return MHD
    

################## 
class Track:
    '''Track class with state, covariance, id'''
    def __init__(self, id):
        # save id
        self.id = id
        
        # generate random state x
        self.x = np.matrix([[np.random.uniform(2,8)],
                        [np.random.uniform(-3,3)],
                        [0],
                        [0]])
        
        # set up estimation error covariance
        self.P = np.matrix([[2, 0, 0, 0],
                        [0, 3, 0, 0],
                        [0, 0, 1, 0],
                        [0, 0, 0, 1]])
        
class Measurement:
    '''Measurement class with easurement, covariance, id'''
    def __init__(self, id, x, y):
        # save id
        self.id = id
        
        # generate random measurement z
        self.z = np.matrix([[x + np.random.normal(0,2)],
                        [y + np.random.normal(0,2)]])
        
        # set up measurement covariance
        self.R = np.matrix([[2, 0],
                        [0, 2]])
         
    
#################
def run():
    '''generate tracks and measurements and call association'''
    # set up track_list and meas_list for association
    np.random.seed(5) # make random values predictable
    association = Association() # init data association
    track_list = []
    meas_list = []

    # initialize visualization
    fig, ax = plt.subplots()

    # generate and plot tracks and measurements
    for i in range(3):
        
        # tracks
        track = Track(i+1)
        track_list.append(track)
        ax.scatter(float(-track.x[1]), float(track.x[0]), marker='x', color='red', label='track')
        ax.text(float(-track.x[1]), float(track.x[0]), str(track.id), color='red')
        
        # measurements
        meas = Measurement(i+1, float(track.x[0]), float(track.x[1]))
        meas_list.append(meas)
        ax.scatter(float(-meas.z[1]), float(meas.z[0]), marker='o', color='green', label='measurement')
        ax.text(float(-meas.z[1]), float(meas.z[0]), str(meas.id), color='green')

    # calculate association matrix
    association.associate(track_list, meas_list)
    print('Association matrix:', association.association_matrix)

    # visualize distances
    for track in track_list:
        for meas in meas_list:
            dist = association.association_matrix[track.id-1, meas.id-1]
            if dist < np.inf: 
                ax.plot([float(-track.x[1]), float(-meas.z[1])], [float(track.x[0]), float(meas.z[0])], color='gray')
                str_dist = "{:.2f}".format(dist)
                ax.text(float((-track.x[1] - meas.z[1])/2), float((track.x[0] + meas.z[0])/2), str_dist)

    # maximize window     
    mng = plt.get_current_fig_manager()
    mng.frame.Maximize(True)

    # remove repeated labels
    handles, labels = ax.get_legend_handles_labels()
    handle_list, label_list = [], []
    for handle, label in zip(handles, labels):
        if label not in label_list:
            handle_list.append(handle)
            label_list.append(label)
    ax.legend(handle_list, label_list, loc='center left', shadow=True, fontsize='large', bbox_to_anchor=(0.9, 0.1))

    # axis
    ax.set_xlabel('y [m]')
    ax.set_ylabel('x [m]')
    ax.set_xlim(-5,5)
    ax.set_ylim(0,10)

    # correct x ticks (positive to the left)
    ticks_x = ticker.FuncFormatter(lambda x, pos: '{0:g}'.format(-x) if x!=0 else '{0:g}'.format(x))
    ax.xaxis.set_major_formatter(ticks_x)
            
    plt.show() 
    
####################
# call main loop
run()
```
