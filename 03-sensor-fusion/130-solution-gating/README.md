# Solution: Gating

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=ZRRSoGNJ7_c)

## Summary

**Gating Function and Association Matrix**

This README file provides an overview of the key concepts and practical steps involved in implementing a gating function using the SciPy package and managing association matrices. The main topic is the implementation of a gating function to filter out unlikely associations between tracks and measurements.

### Key Concepts

* **Inverse Cumulative Chi-Square Distribution**: The chi2.ppf function from SciPy returns the gating threshold based on the input probability (95% in this case) and degrees of freedom.
* **Percent-Point Function (PPF)**: PPF is the inverse of the cumulative density function, used to calculate the gating threshold.
* **Association Matrix**: A matrix representing associations between tracks and measurements, where each entry represents a possible association.
* **Argmin and Unravel Index**: NumPy functions used to find the indices of the minimum entry in the association matrix and extract the corresponding row and column indices.

### Practical Notes

* To implement the gating function, use the `chi2.ppf` function from SciPy with a probability input (e.g., 95%) and degrees of freedom.
* In real-world applications, consider using a higher probability threshold (e.g., 99%) to avoid removing too many correct measurements.
* When managing association matrices, use NumPy's `argmin` and `unravel_index` functions to find the indices of the minimum entry and extract corresponding row and column indices.
* Carefully read console output and double-check results by hand when debugging association tasks.

## Transcript

Here is my solution. For the gating function, we need the inverse cumulative chi-square distribution. I used the SciPy package for this. The function chi2.ppf does exactly what we want. It takes the probability and degrees of freedom as input and returns the gating threshold.

PPF stands for percent-point function, which is the inverse of the cumulative density function. I use 95 percent as input to see some more effects of the gating here. In real-world applications, I would rather recommend a number around 99 percent in order to not remove too many correct measurements. Then the function returns True if the input image T is smaller than the calculated limit, otherwise it returns False. For the second task, the function named get_closest_track_and_measurement first checks if A contains any values besides infinity.

If not, the function returns nan as a result. To get the indices of the minimum entry in the association matrix A, I use the NumPy function argmin. Usually, this function returns the index of the flattened area. In order to avoid this, we can use a function called unravel_index. This returns an index for the row and one for the column that are stored in variables called ind_track and ind_meas.

Then I delete the corresponding row and column from A. From the unassigned tracks and the unassigned measurement lists, the function then checks which track number and measurement number these indices correspond to. Then I remove these entries from the lists and return the track and the measurement number. Let's see how the output looks like. As you can see, there are much less gray lines, so many unlikely combinations have not been considered.

Our gating was successful because we only removed the faraway associations, for example, between track 2 and measurement 3. Also, the blue lines show which track got associated to which measurement. You can also see in the console output here on the right what happens. At first, we have a three by three association matrix. Then we find the minimum entry 1.1, which corresponds to track 2 and measurement 2.

Therefore, we remove the second row and column from A and the second entry from both lists. Note that, in the lists we start counting at 0. Track number 1 corresponds to index 0 in the list. Then we continue with a two by two association matrix, and so it goes on until the matrix is empty. The association task can be quite difficult to debug.

Carefully reading the console output and double checking by hand might help.

## Additional Content

## Solution: Gating
```python
import numpy as np
import matplotlib
matplotlib.use('wxagg') # change backend so that figure maximizing works on Mac as well   
import matplotlib.pyplot as plt
import matplotlib.ticker as ticker
from scipy.stats.distributions import chi2

class Association:
    '''Data association class with single nearest neighbor association and gating based on Mahalanobis distance'''
    def __init__(self):
        self.association_matrix = np.matrix([])
        self.unassigned_tracks = []
        self.unassigned_meas = []
        
    def associate(self, track_list, meas_list):
        N = len(track_list) # N tracks
        M = len(meas_list) # M measurements
        self.unassigned_tracks = list(range(N))
        self.unassigned_meas = list(range(M))
        
        # initialize association matrix
        self.association_matrix = np.inf*np.ones((N,M)) 
        
        # loop over all tracks and all measurements to set up association matrix
        for i in range(N): 
            track = track_list[i]
            for j in range(M):
                meas = meas_list[j]
                dist = self.MHD(track, meas)
                if self.gating(dist):
                    self.association_matrix[i,j] = dist
        
    def MHD(self, track, meas):
        # calc Mahalanobis distance
        H = np.matrix([[1, 0, 0, 0],
                       [0, 1, 0, 0]]) 
        gamma = meas.z - H*track.x
        S = H*track.P*H.transpose() + meas.R
        MHD = gamma.transpose()*np.linalg.inv(S)*gamma # Mahalanobis distance formula
        return MHD
    
    def gating(self, MHD): 
        # check if measurement lies inside gate
        limit = chi2.ppf(0.95, df=2)
        if MHD < limit:
            return True
        else:
            return False
        
    def get_closest_track_and_meas(self):
        # find closest track and measurement for next update
        A = self.association_matrix
        if np.min(A) == np.inf:
            return np.nan, np.nan

        # get indices of minimum entry
        ij_min = np.unravel_index(np.argmin(A, axis=None), A.shape) 
        ind_track = ij_min[0]
        ind_meas = ij_min[1]

        # delete row and column for next update
        A = np.delete(A, ind_track, 0) 
        A = np.delete(A, ind_meas, 1)
        self.association_matrix = A
        
        # update this track with this measurement
        update_track = self.unassigned_tracks[ind_track] 
        update_meas = self.unassigned_meas[ind_meas]
        
        # remove this track and measurement from list
        self.unassigned_tracks.remove(update_track) 
        self.unassigned_meas.remove(update_meas)
        
        return update_track, update_meas

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
    print('unassigned_tracks list:', association.unassigned_tracks)
    print('unassigned_meas list:', association.unassigned_meas)     

    # visualize distances
    for track in track_list:
        for meas in meas_list:
            dist = association.association_matrix[track.id-1, meas.id-1]
            if dist < np.inf: 
                ax.plot([float(-track.x[1]), float(-meas.z[1])], [float(track.x[0]), float(meas.z[0])], color='gray')
                str_dist = "{:.2f}".format(dist)
                ax.text(float((-track.x[1] - meas.z[1])/2), float((track.x[0] + meas.z[0])/2), str_dist)

    # update associated tracks with measurements
    matrix_orig = association.association_matrix
    while association.association_matrix.shape[0]>0 and association.association_matrix.shape[1]>0:
        
        # search for next association between a track and a measurement
        ind_track, ind_meas = association.get_closest_track_and_meas()
        if np.isnan(ind_track):
            print('---no more associations---')
            break
            
        track = track_list[ind_track]
        meas = meas_list[ind_meas]
        dist = matrix_orig[ind_track, ind_meas]
        ax.plot([float(-track.x[1]), float(-meas.z[1])], [float(track.x[0]), float(meas.z[0])], color='blue', label='association')
        str_dist = "{:.2f}".format(dist)
        ax.text(float((-track.x[1] - meas.z[1])/2), float((track.x[0] + meas.z[0])/2), str_dist)
        print('found association between track', ind_track+1, 'and measurement', ind_meas+1, 'with MHD =', str_dist)
        print('New association matrix:', association.association_matrix)    
        print('New unassigned_tracks list:', association.unassigned_tracks)
        print('New unassigned_meas list:', association.unassigned_meas)        
        

    #################
    # visualization
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
