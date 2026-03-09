# Solution: Initialization

> Part of: **Multi-Target Tracking**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=LTC5r85EbuY)

## Summary

**Kalman Filter Initialization in Sensor Coordinates**
=====================================================

This README file summarizes the key concepts and practical steps for initializing a Kalman filter in sensor coordinates.

### Key Concepts

* **Homogeneous coordinates**: A mathematical representation of points or vectors that combines spatial information with scaling factors. Used to transform vectors between different coordinate systems.
* **Transformation matrix**: A 4x4 matrix used to perform transformations between homogeneous coordinates. In this case, the `sensor_to_vehicle` transformation matrix is used to convert sensor measurements to vehicle coordinates.
* **Estimation error covariance matrix P**: A 6x6 matrix that represents the uncertainty of the state vector x. It's initialized with two parts: `P_pos` for position and `P_vel` for velocity.
* **Rotation matrix M**: Used to rotate the measurement covariance matrix from sensor to vehicle coordinates.

### Practical Notes

To initialize a Kalman filter in sensor coordinates, follow these steps:

1. Set up a vector `pos_sens` in homogeneous coordinates using the measurement.
2. Transform `pos_sens` from sensor to vehicle coordinates by multiplying with the `sensor_to_vehicle` transformation matrix.
3. Initialize the position covariance matrix `P_pos` by rotating the measurement covariance matrix with the rotation matrix M and its transpose.
4. Initialize the velocity components of the state vector x with dummy values (e.g., 50 for VX and VY, 5 for VZ) to represent high uncertainty.
5. Define the overall 6x6 covariance matrix P as a concatenation of `P_pos` and `P_vel`.

Note: The script provided in the lesson demonstrates the initialization process and shows how the track is initialized correctly using the transformed measurement.

## Transcript

Here's how I did it. I used the measurement to set up a vector pos_sens in homogeneous coordinates. Then I transformed this vector from sensor to vehicle coordinates by multiplying with the given transformation matrix called sensor to vehicle. Then I save the transformed position as well as zeros for the velocity components in the state vector x. For the estimation error covariance matrix P, we need the rotation matrix M.

We rotate the measurement covariance matrix from sensor to vehicle coordinates by multiplying with M and with its transpose. This gives the position covariance P_pos. For the velocity components, we don't have any measurement information, so we simply initialize them with some high uncertainty. Here I used 50 for the VX and VY standard deviations, and five for the velocity in Z, because we don't assume as much velocity in height, unless we have very steep hills. We use these dummy values to initialize the velocity covariance matrix P_vell.

Finally, we define the overall 6 by 6 covariance matrix P, where the first half is given by P plus and the second half is given by P_vell. Let's see what happens if I run the script now. As you can see, the initialized track is not zero anymore. In the last image, you can see that the track is initialized where the measurement lies. The transformation was correct.

## Additional Content

## Solution: Initialization
```python
import numpy as np
import matplotlib
matplotlib.use('wxagg') # change backend so that figure maximizing works on Mac as well  
import matplotlib.pyplot as plt
import matplotlib.ticker as ticker

class Track:
    '''Track class with state, covariance, id'''
    def __init__(self, meas, id):
        print('creating track no.', id)
        self.id = id
        
        # transform measurement to vehicle coordinates
        pos_sens = np.ones((4, 1)) # homogeneous coordinates
        pos_sens[0:3] = meas.z[0:3] 
        pos_veh = meas.sens_to_veh*pos_sens
        
        # save initial state from measurement
        self.x = np.zeros((6,1))
        self.x[0:3] = pos_veh[0:3]
        
        # set up position estimation error covariance
        M_rot = meas.sens_to_veh[0:3, 0:3]
        P_pos = M_rot * meas.R * np.transpose(M_rot)
        
        # set up velocity estimation error covariance
        sigma_p44 = 50 # initial setting for estimation error covariance P entry for vx
        sigma_p55 = 50 # initial setting for estimation error covariance P entry for vy
        sigma_p66 = 5 # initial setting for estimation error covariance P entry for vz
        P_vel = np.matrix([[sigma_p44**2, 0, 0],
                        [0, sigma_p55**2, 0],
                        [0, 0, sigma_p66**2]])
        
        # overall covariance initialization
        self.P = np.zeros((6, 6))
        self.P[0:3, 0:3] = P_pos
        self.P[3:6, 3:6] = P_vel
        
        
###################  
        
class Measurement:
    '''Lidar measurement class including measurement z, covariance R, coordinate transform matrix'''
    def __init__(self, gt, phi, t):
        # compute rotation around z axis
        M_rot = np.matrix([[np.cos(phi), -np.sin(phi), 0], 
                    [np.sin(phi), np.cos(phi), 0],
                    [0, 0, 1]])
        
        # coordiante transformation matrix from sensor to vehicle coordinates
        self.sens_to_veh = np.matrix(np.identity(4))            
        self.sens_to_veh[0:3, 0:3] = M_rot
        self.sens_to_veh[0:3, 3] = t
        print('Coordinate transformation matrix:', self.sens_to_veh)
        
        # transform ground truth from vehicle to sensor coordinates
        gt_veh = np.ones((4, 1)) # homogeneous coordinates
        gt_veh[0:3] = gt[0:3] 
        gt_sens = np.linalg.inv(self.sens_to_veh) * gt_veh
        
        # create measurement object
        sigma_lidar_x = 0.01 # standard deviation for noisy measurement generation
        sigma_lidar_y = 0.01
        sigma_lidar_z = 0.001
        self.z = np.zeros((3,1)) # measurement vector
        self.z[0] = float(gt_sens[0,0]) + np.random.normal(0, sigma_lidar_x)
        self.z[1] = float(gt_sens[1,0]) + np.random.normal(0, sigma_lidar_y)
        self.z[2] = float(gt_sens[2,0]) + np.random.normal(0, sigma_lidar_z)
        self.R = np.matrix([[sigma_lidar_x**2, 0, 0], # measurement noise covariance matrix
                            [0, sigma_lidar_y**2, 0], 
                            [0, 0, sigma_lidar_z**2]])
        
def visualize(track, meas):
    fig, (ax1, ax2, ax3) = plt.subplots(1,3)
    ax1.scatter(-meas.z[1], meas.z[0], marker='o', color='blue', label='measurement')
    ax2.scatter(-track.x[1], track.x[0], color='red', s=80, marker='x', label='initialized track')

    # transform measurement to vehicle coordinates for visualization
    z_sens = np.ones((4, 1)) # homogeneous coordinates
    z_sens[0:3] = meas.z[0:3] 
    z_veh = meas.sens_to_veh * z_sens
    ax3.scatter(-float(z_veh[1]), float(z_veh[0]), marker='o', color='blue', label='measurement')
    ax3.scatter(-track.x[1], track.x[0], color='red', s=80, marker='x', label='initialized track')
        
    # maximize window     
    mng = plt.get_current_fig_manager()
    mng.frame.Maximize(True)

    # legend and axes
    for ax in (ax1, ax2, ax3):
        ax.legend(loc='center left', shadow=True, fontsize='large', bbox_to_anchor=(0.5, 0.1))
        ax.set_xlabel('y [m]')
        ax.set_ylabel('x [m]')
        ax.set_xlim(-2,2)
        ax.set_ylim(0,2)
        # correct x ticks (positive to the left)
        ticks_x = ticker.FuncFormatter(lambda x, pos: '{0:g}'.format(-x) if x!=0 else '{0:g}'.format(x))
        ax.xaxis.set_major_formatter(ticks_x)
        
    # titles
    ax1.title.set_text('Sensor Coordinates')
    ax2.title.set_text('Vehicle Coordinates')
    ax3.title.set_text('Vehicle Coordinates\n (track and measurement should align)')

    plt.show()

        
###################  
# ground truth         
gt = np.matrix([[1.7],
                [1],
                [0]])

# sensor translation and rotation angle
t = np.matrix([[2],
                [0.5],
                [0]])
phi = np.radians(45)

# generate measurement
meas = Measurement(gt, phi, t)

# initialize track from this measurement
track = Track(meas, 1)

# visualization
visualize(track, meas)
```
