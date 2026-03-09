# Solution: Lidar Tracking

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=k3x2H2CRd8I)

## Summary

**Kalman Filter Implementation**
=====================================

This project demonstrates the implementation of a Kalman filter to estimate the state of a system from noisy measurements. The code utilizes NumPy matrices to represent the system and measurement models.

### Key Concepts

* **System Matrix F**: A 4x4 NumPy matrix containing the timestep DT, used in the system model.
* **Process Noise Matrix Q**: Calculated using the design parameter `q`, which determines the covariance of the process noise.
* **Measurement Metrics H**: A 2x4 NumPy matrix that projects the body position and velocity vector to a 2D position measurement.
* **Kalman Filter Results**: The green crosses in the output plot, which closely follow the ground truth trajectory despite using a linear motion model.

### Practical Notes

The code provided uses a linear motion model, but notes that further improvement can be achieved by switching to a nonlinear motion model. The output plot shows the noisy measurements (blue dots) and the estimated state (green crosses), demonstrating the effectiveness of the Kalman filter in tracking the system's true trajectory.

## Transcript

Here's how I did it. The system matrix F is a four-by-four Numpy Matrix containing the timestep DT. The process [inaudible] matrix q uses the design parameter lowercase q to calculate the matrix entries as learned in the lesson, and the measurement metrics H, is a two by four numpy matrix that projects the body position and velocity vector to the 2D position measurement. If I run this script, this is the output. We can see the ground truth in gray.

Note that it follows a curve due to the non-linear motion. The noisy measurements are the blue dots and the green crosses are the Kalman filter results that follow the grade trajectory quite well. Even though we used a linear motion model that does not perfectly fit the nonlinear motion, we could of course, further improve our results by using a nonlinear motion model.

## Additional Content

## Solution: Lidar
```python
import numpy as np
import matplotlib
matplotlib.use('wxagg') # change backend so that figure maximizing works on Mac as well  
import matplotlib.pyplot as plt

class Filter:
    '''Kalman filter class'''
    def __init__(self):
        self.dim_state = 4 # process model dimension
        self.dt = 0.1 # time increment
        self.q=0.1 # process noise variable for Kalman filter Q

    def F(self):
        # system matrix
        dt = self.dt
        return np.matrix([[1, 0, dt, 0],
                        [0, 1, 0, dt],
                        [0, 0, 1, 0],
                        [0, 0, 0, 1]])

    def Q(self):
        # process noise covariance Q
        q = self.q
        dt = self.dt
        q1 = ((dt**3)/3) * q 
        q2 = ((dt**2)/2) * q 
        q3 = dt * q 
        return np.matrix([[q1, 0, q2, 0],
                        [0, q1, 0, q2],
                        [q2, 0, q3, 0],
                        [0, q2, 0,  q3]])
        
    def H(self):
        # measurement matrix H
        return np.matrix([[1, 0, 0, 0],
                       [0, 1, 0, 0]]) 
    
    def predict(self, x, P):
        # predict state and estimation error covariance to next timestep
        F = self.F()
        x = F*x # state prediction
        P = F*P*F.transpose() + self.Q() # covariance prediction
        return x, P

    def update(self, x, P, z, R):
        # update state and covariance with associated measurement
        H = self.H() # measurement matrix
        gamma = z - H*x # residual
        S = H*P*H.transpose() + R # covariance of residual
        K = P*H.transpose()*np.linalg.inv(S) # Kalman gain
        x = x + K*gamma # state update
        I = np.identity(self.dim_state)
        P = (I - K*H) * P # covariance update
        return x, P     
        
        
def run_filter():
    ''' loop over data and call predict and update'''
    np.random.seed(0) # make random values predictable
    
    # init filter
    KF = Filter()
    
    # init figure
    fig, ax = plt.subplots()
    
    # init track state and covariance
    x = np.matrix([[0],
                [0],
                [0],
                [0]])
    P = np.matrix([[0.1**2, 0, 0, 0],
                [0, 0.1**2, 0, 0],
                [0, 0, 2**2, 0],
                [0, 0, 0, 2**2]])
    
    # loop over measurements and call predict and update
    for i in range(1,101):        
        
        # prediction
        x, P = KF.predict(x, P) # predict to next timestep
        
        # ground truth generation
        gt = np.matrix([[i*KF.dt], 
                       [0.1*(i*KF.dt)**2]])
        
        # measurement generation
        sigma_z = 0.2 # measurement noise 
        z = np.matrix([[float(gt[0]) + np.random.normal(0, sigma_z)],
                       [float(gt[1]) + np.random.normal(0, sigma_z)]]) # generate noisy measurement
        R = np.matrix([[sigma_z**2, 0], # measurement noise covariance matrix
                            [0, sigma_z**2]])
        
        # update
        x, P = KF.update(x, P, z, R) # update with measurement
        
        # visualization    
        ax.scatter(float(x[0]), float(x[1]), color='green', s=40, marker='x', label='track')
        ax.scatter(float(z[0]), float(z[1]), color='blue', marker='.', label='measurement')
        ax.scatter(float(gt[0]), float(gt[1]), color='gray', s=40, marker='+', label='ground truth')
        ax.set_xlabel('x [m]')
        ax.set_ylabel('y [m]')
        ax.set_xlim(0,10)
        ax.set_ylim(0,10)
           
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
        ax.legend(handle_list, label_list, loc='center left', shadow=True, fontsize='x-large', bbox_to_anchor=(0.8, 0.5))

        plt.pause(0.01)
    plt.show()
        

####################
# call main loop
run_filter()
```
