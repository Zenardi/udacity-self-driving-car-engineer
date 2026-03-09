# Numerical Approximation vs. Numerical Optimization

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=edzubE9c7Ug)

## Summary

**Path Planning Problem: Numerical Approximation and Optimization**

This project involves finding the best coefficients for our polynomials spiral using numerical approximation or optimization. We will explore both methods and discuss their key components, challenges, and solutions.

### Key Concepts

* **Numerical Approximation**: A method that provides approximate but accurate solutions to problems.
* **Numerical Optimization**: A method that minimizes or maximizes a function by selecting a set of elements from available alternatives.
* **Objective Function**: A function that needs to be minimized in numerical optimization, often including penalty terms for deviating from the end state.
* **Boundary Conditions**: Requirements that must be met at the start and end states of the problem.
* **Parameter Mapping**: A technique used to reduce the dimensionality of a problem by mapping multiple variables to a smaller set of parameters.
* **Dimensionality Reduction**: The process of reducing the number of unknowns in a problem, resulting in faster computation times.

### Practical Notes

To implement numerical approximation and optimization for path planning problems:

1. Set up a tolerance value to determine when the error is below a certain threshold, indicating that the goal state has been achieved.
2. Include penalty terms in the objective function to penalize deviations from the end state.
3. Use parameter mapping to reduce the dimensionality of the problem by introducing new parameters (P0-P4) and expressing original coefficients in terms of these parameters.

Example code for implementing numerical optimization:
```python
def objective_function(P):
    # Define penalty terms for deviating from the end state
    penalty_x = alpha * (sf - xf)
    penalty_y = alpha * (sf - yf)
    penalty_theta = alpha * (thetaf - theta)

    # Calculate the objective function value
    return penalty_x + penalty_y + penalty_theta
```
Note: This code snippet is a simplified example and may require modifications to fit your specific use case.

## Transcript

Finding the best coefficients for our polynomials spiral requires either the use of a numerical approximation or numerical optimization. In numerical approximation, also known as numerical analysis. The goal is to give approximate but accurate solutions to problems. In numerical optimization, the goal is to minimize or maximize a function by selecting a set of elements from some set of available alternatives. Depending on what method we use to solve the path planning problem, we may have an additional requirement, as we already addressed when we defined the components of the path planning problem.

Both numerical approximation and numerical optimization require start and end states and vehicle curvature constraints. Numerical optimization requires one additional component, the objective function. A function that we will have to minimize. Since both methods need to use boundary conditions, both suffer from the same problem of having to match exactly the end or goal state. Both numerical approximation and numerical optimization struggle to match exactly the end-state.

An easy way to solve this challenge is when we use numerical approximation to set up a tolerance value such that when our error is below this tolerance, then we can say that we have achieved the goal state. When we use numerical optimization, include terms into the objective function that penalize deviating from the end state, as you can see here, when the x-component at the end of the curve, sf is too far from the desired final x, xf, then the penalty would be higher as it will be multiplied by a positive number alpha. The same for the y and the same for the heading. In the same fashion as in the previous slide, both methods used a cubic spiral and both of them will benefit from our parameter mapping that will lead us to a dimensionality reduction, which means that we will have fewer unknowns to figure out. Let's see how we can do that.

The cubic spiral has four coefficients, a3, a2, a1, and a0. But when S is equal to 0 at the starting position, all terms vanish except a0. So a0 is actually our known starting curvature. We also don't know the length of the curve, sf, which is needed to calculate x, y, and theta along this spiral. That leaves us with four unknowns, a3, a2, a1, and sf.

Now we are going to write all eight coefficients in terms of a new set of parameters, P. We'll introduce P0, P1, P2, and P3 as being equal to the curvatures at four evenly spaced points along this spiral, as you can see in the sketch. So P0 is the curvature at the beginning of the spiral. It's our starting curvature. P1 and P2 are the curvatures at one-third and two-thirds of the wave respectively.

P3 is the goal curvature. Finally, we will introduce P4, which will be the unknown spiral length, sf. Let's see how we can write all eight coefficient in terms of this P parameters. Let's now see how we reduce the problem dimensionality. P0 and P3 are known to us since they represent the starting and goal curvatures.

As you can see, we are left with only three unknowns, P1, P2, and P4. The curvatures at one-third and two-thirds of the way and the final path length. This process of parameter mapping and dimensionality reduction will result in a significant computational speedup, which is essential in a real time problem like this one. Let's recap what we learned in this section. To solve the path planning problem, we can use numerical approximation or numerical optimization.

We briefly describe what each method does and presented the main components to solve the problem. We also described a common challenge, both approaches have and how to overcome it. This challenge was to satisfy exactly the end state. At the end of this section, we reduce the dimensionality of the problem from four unknowns to three, by the use of a parameter mapping approach.

## Additional Content

We mentioned optimization earlier in the lesson when discussing objective functions. We're coming back to it now to discuss the difference between numerical approximation and optimization. Remember, objective functions are only used for optimization. methods. Finding the "best" coefficients for our polynomial spiral requires either:
- **Numerical Approximation**: Techniques that give approximate but accurate solutions to problems, or
- **Numerical Optimization**: Minimizing or maximizing a function by selecting a sample of elements from the large complete distribution of possibilities. 

The challenge for both of the approaches is to satisfy the exact end state. With numerical approximation, we set a tolerance value that achieves the goal state when the error is below the set tolerance. For numerical optimization, a challenge can arise when including terms into the objective function that penalize deviating from the end state.
