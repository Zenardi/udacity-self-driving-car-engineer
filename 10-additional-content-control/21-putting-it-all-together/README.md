# Putting It All Together

> Part of: **Model Predictive Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=CZ71uEy8EtI)

## Summary

**Model Predictive Control (MPC) with Optimizer**
=====================================================

This project demonstrates the application of Model Predictive Control (MPC) using an optimizer to minimize a cost function. MPC is a control algorithm that predicts future states of a system and adjusts control inputs accordingly.

### Key Concepts
* **Optimizer**: A mathematical tool used to find the optimal solution by minimizing or maximizing a cost function.
* **Cost Function**: A mathematical expression that defines the objective of the optimization problem, which in this case is to minimize the cost.
* **Model Predictive Control (MPC) Algorithm**:
	+ Set up MPC loop with duration `T`, number of steps `N`, and time step `dt`.
	+ Define vehicle model and constraints (e.g., speed limits).
	+ Define cost function to be minimized.
* **IPOPT Solver**: A nonlinear programming solver used to find the optimal control inputs that minimize the cost function.

### Practical Notes
To implement MPC, you need to:

1. Set up the MPC loop with `T`, `N`, and `dt`.
2. Define the vehicle model and constraints (e.g., speed limits).
3. Define the cost function to be minimized.
4. Use an optimization solver like IPOPT to find the optimal control inputs that minimize the cost function.
5. Apply the first control input to the vehicle and repeat the loop.

Note: This project assumes a basic understanding of control systems, optimization techniques, and programming concepts.

## Transcript

<v English>Model predictive control uses</v> <v English>an optimizer to find the control inputs and minimize the cost function.</v> <v English>We actually only execute the very first set of control inputs.</v> <v English>This brings the vehicle to a new state and then you repeat the process.</v> <v English>Here is the MPC algorithm.</v> <v English>First, we set up everything required for the model predictive control loop.</v> <v English>This consists of defining the duration of the trajectory,</v> <v English>T, by choosing N and dt.</v> <v English>Next, we define the vehicle model and constraints such as actual limitations.</v> <v English>Finally, we define the cost function.</v> <v English>With the setup complete,</v> <v English>we begin to state feedback loop.</v> <v English>First, we pass the current state to the model predictive controller.</v> <v English>Next, the optimization solver is called.</v> <v English>The solver uses the initial state,</v> <v English>the model constraints and cost function to</v> <v English>return a vector of control inputs that minimize the cost function.</v> <v English>The solver we'll use is called IPOPT.</v> <v English>We apply the first control input to the vehicle and repeat the loop.</v>
