# Cost Function Matching

> Part of: **Behavior Planning**

## Additional Content

Consider the following cost functions. What purpose does each serve?

##### Cost Function 1

$$\begin{cases} 
      1 & \ddot{s} \geq a\_{\text{max}} \\
      0 & \ddot{s} < a\_{\text{max}}
   \end{cases}$$

##### Cost Function 2

$$\begin{cases} 
      1 & d \geq d\_{\text{max}} \\
      1 & d \leq d\_{\text{min}} \\
      0 & d\_{\text{min}} < d < d\_{\text{max}}
   \end{cases}$$

##### Cost Function 3

$$\begin{cases} 
      1 & \dot{s} \geq v\_{\text{speed limit}} \\
      0 &  \dot{s} < v\_{\text{speed limit}}
   \end{cases}$$

##### Cost Function 4

$$\frac{1}{1 + e^{-(d - d\_{\text{lane center}})^2}}$$

##### Cost Function 5

$$(\text{lane number} - \text{target lane number}) ^ 2$$
