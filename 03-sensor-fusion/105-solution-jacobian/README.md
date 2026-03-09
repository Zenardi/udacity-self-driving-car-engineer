# Solution: Jacobian

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=_sdUmSY6abg)

## Summary

**Nonlinear Measurement Function and Jacobian**

This README file summarizes key concepts related to nonlinear measurement functions and Jacobians in computer vision.

### Key Concepts

* **Nonlinear Measurement Function**: A function that projects 3D points to image coordinates using a central point `c` and focal length `f`. It is represented as `H(x) = [x1 / (c1 + f), x2 / (c2 + f)]`.
	+ Raises an error if the first component of `x` is zero.
* **Jacobian**: A matrix that represents the linear approximation of a nonlinear function at a given point. In this case, the Jacobian of the nonlinear measurement function `H(x)` is represented as:
```python
H = [[1 / (c1 + f), 0],
     [0, 1 / (c2 + f)]]
```
* **Linear Approximation**: A linear function that approximates a nonlinear function at a given point. The linear approximation of the nonlinear measurement function `H(x)` is represented as:
```python
L(x) = H(x) + J \* (x - x0)
```
where `J` is the Jacobian and `x0` is the point at which the linearization is performed.

### Practical Notes

* To use the nonlinear measurement function, ensure that the first component of `x` is not zero.
* The Jacobian can be used to approximate the nonlinear measurement function in a small area around a given point. This can be useful for simplifying complex calculations and improving computational efficiency.
* Visualizing the nonlinear measurement function and its linear approximation using plotting tools can help understand how the Jacobian works and why it is a good approximation.

## Transcript

Here is my solution. The nonlinear measurement function divides by the first component of x, so we raise an error if this component is zero. Otherwise, this is how H projects x to image coordinates using the central point c and focal length f. Likewise, the function get_H makes sure to not divide it through zero. Then, this is how the Jacobian H looks like as derived in the last lesson.

If I run the script, we can see the blue first and second component of the non-linear measurement function H. The red line is the linear approximation with the Jacobian. As desired, the red line is tangential to the blue curve at the green point x, so we have correctly calculated the Jacobian. If we zoom in at the green point x, it becomes clearer why we can use the linearized red line as an approximation to the blue curve. Both lines are very similar in a small area around x, so we can neglect the non-linearity.

## Additional Content

## Solution: Jacobian
```python
import numpy as np
import matplotlib
matplotlib.use('wxagg') # change backend so that figure maximizing works on Mac as well  
import matplotlib.pyplot as plt

class Camera:
    '''Camera sensor class including measurement matrix'''
    def __init__(self):
        self.f_i = 2095.5 # focal length i-coordinate
        self.f_j = 2095.5 # focal length j-coordinate
        self.c_i = 944.9 # principal point i-coordinate
        self.c_j = 640.2 # principal point j-coordinate 
        
    def get_hx(self, x):    
        # calculate nonlinear measurement expectation value h(x)   
        hx = np.zeros((2,1))
        # check and print error message if dividing by zero
        if x[0]==0:
            raise NameError('Jacobian not defined for x[0]=0!')
        else:
            hx[0,0] = self.c_i - self.f_i*x[1]/x[0] # project to image coordinates
            hx[1,0] = self.c_j - self.f_j*x[2]/x[0]
            return hx    
    
    def get_H(self, x):
        # calculate Jacobian H at current x from h(x)
        H = np.matrix(np.zeros((2, 6)))
        # check and print error message if dividing by zero
        if x[0]==0:
            raise NameError('Jacobian not defined for x[0]=0!')
        else:
            H[0,0] = self.f_i * x[1] / (x[0]**2)
            H[1,0] = self.f_j * x[2] / (x[0]**2)
            H[0,1] = -self.f_i / x[0]
            H[1,2] = -self.f_j / x[0]
            return H

def calc_Jacobian(x):
    # calculate Jacobian for x
    cam = Camera()
    H = cam.get_H(x)

    # init visualization
    fig, (ax1, ax2) = plt.subplots(1,2)
    plot_x = []
    plot_y1 = []
    plot_y2 = []
    lin_y1 = []
    lin_y2 = []

    # calculate Taylor series expansion point
    hx_orig = cam.get_hx(x)
    ax1.plot(x[0], hx_orig[0], marker='x', color='green', label='expansion point x')
    ax2.plot(x[0], hx_orig[1], marker='x', color='green', label='expansion point x')

    # calculate linear approximation at this point 
    s1 = float(H[0,0]) # slope of tangent given by Jacobian H
    s2 = float(H[1,0])
    i1 = float(hx_orig[0] - s1*x[0]) # intercept i = y - s*x
    i2 = float(hx_orig[1] - s2*x[0])

    # calculate nonlinear measurement function h
    for px in range(1,50):
        x[0] = px
        hx = cam.get_hx(x)
        plot_x.append(px)
        plot_y1.append(hx[0])
        plot_y2.append(hx[1])
        lin_y1.append(s1*px + i1)
        lin_y2.append(s2*px + i2)
        
    # plot results
    ax1.plot(plot_x, plot_y1, color='blue', label='measurement function h')
    ax1.plot(plot_x, lin_y1, color='red', label='linear approximation H')
    ax2.plot(plot_x, plot_y2, color='blue', label='measurement function h')
    ax2.plot(plot_x, lin_y2, color='red', label='linear approximation H')

    # maximize window     
    mng = plt.get_current_fig_manager()
    mng.frame.Maximize(True)

    # legend
    ax1.legend(loc='center left', shadow=True, fontsize='large', bbox_to_anchor=(0.5, 0.1))
    ax1.set_xlabel('x [m]')
    ax1.set_ylabel('h(x) first component [px]')
    ax2.legend(loc='center left', shadow=True, fontsize='large', bbox_to_anchor=(0.5, 0.1))
    ax2.set_xlabel('x [m]')
    ax2.set_ylabel('h(x) second component [px]')

    plt.show()

#################
# define expansion point for Taylor series
x = np.matrix([[10],
            [1],
            [-1],
            [0],
            [0],
            [0]])

calc_Jacobian(x)
```
