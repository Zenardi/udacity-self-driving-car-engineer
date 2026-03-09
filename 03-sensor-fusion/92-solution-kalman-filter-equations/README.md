# Solution: Kalman Filter Equations

> Part of: **Extended Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=p-HodvOJxQk)

## Summary

**Kalman Filter Implementation**
=====================================

This README file provides a summary of the key concepts and practical steps introduced in the Udacity lesson on implementing a Kalman filter.

**Key Concepts**
---------------

* **State Transition Function**: The function `F` that predicts the next state `x` based on the current state.
	+ Formula: `x = F * x`
* **Measurement Function**: The function `H` that calculates the measurement `z` based on the current state.
	+ Formula: `gamma = z - H * x`
* **Kalman Gain**: The gain `K` used to update the state and covariance.
	+ Formula: `K = S * H^T / (H * S * H^T)`
* **Covariance Update**: The update of the covariance matrix `P` using the measurement residual `gamma`.
	+ Formula: `P = F * P * F^T + Q`
* **State Update**: The update of the state `x` using the Kalman gain and measurement residual.
	+ Formula: `x = x + K * gamma`

**Practical Notes**
-------------------

* When performing matrix multiplication, NumPy matrices can be multiplied directly without extra care.
* To calculate the transpose of a matrix `F`, use `F.dot(F.T)`.
* To get the inverse of a matrix, use `np.linalg.inv(matrix)`.
* The two-by-two identity matrix can be obtained using `np.identity(2)`.
* In the example code, the measurement noise is simulated by adding a small value to the true measurement.

## Transcript

Here is how I did it. The predict function first gets the prepared state transition function F. Then x is predicted by multiplication with F. Since x and F are numPy matrices, we do not have to take extra care of the matrix multiplication. We then predict P with the prepared F and Q.

The transpose of F can simply be calculated using F dot transpose. The update function calls the prepared measurement function H and calculates the residual gamma equals z minus H times x. Then we update S and K. You can get the inverse of a matrix using the numPy dot linalg dot inv function. Finally, we update the state and the covariance.

Note that you can get a two by two identity matrix using numPy dot identity. Let's see what has changed in the output. The position at the last time step is very close to a 100. Remember that the ground truth is also 100, so our filter is quite accurate. The velocity estimation is very close to one, so this is also very close to the real value.

Note that the measurement here is 98 instead of 100 due to the noise. But our common filters still gets the correct position despite the measurement noise. Finally, note that the entries of P are very small even though they were initialized with big values of 25. This means our filter has stabilized and is very certain about its state estimation x.

## Additional Content

## Solution: Kalman Filter Equations
```python
import numpy as np

class Filter:
    '''Kalman filter class'''
    def __init__(self):
        self.dim_state = 2 # process model dimension

    def F(self):
        # system matrix
        return np.matrix([[1, 1],
                        [0, 1]])

    def Q(self):
        # process noise covariance Q
        return np.matrix([[0, 0],
                        [0, 0]])
        
    def H(self):
        # measurement matrix H
        return np.matrix([[1, 0]])
    
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
    np.random.seed(10) # make random values predictable
    
    # init filter
    KF = Filter()
    
    # init track state and covariance
    x = np.matrix([[0],
                [0]])
    P = np.matrix([[5**2, 0],
                [0, 5**2]])  
    
    # loop over measurements and call predict and update
    for i in range(1,101):        
        print('------------------------------')
        print('processing measurement #' + str(i))
        
        # prediction
        x, P = KF.predict(x, P) # predict to next timestep
        print('x- =', x)
        print('P- =', P)
        
        # measurement generation
        sigma_z = 1 # measurement noise
        z = np.matrix([[i + np.random.normal(0, sigma_z)]]) # generate noisy measurement
        R = np.matrix([[sigma_z**2]]) # measurement covariance
        print('z =', z)
        
        # update
        x, P = KF.update(x, P, z, R) # update with measurement
        print('x+ =', x)
        print('P+ =', P)
        

# call main loop
run_filter()
```
