# Implement a Cost Function in C++

> Part of: **Behavior Planning**

## Additional Content

In the previous quizzes, you designed a cost function to choose a lane when trying to reach a goal in highway driving:

$$\text{cost} = 1 - e^{- \frac{|\Delta d|}{\Delta s}}$$

Here,

$\Delta d$

was the lateral distance between the goal lane and the final chosen lane, and

$\Delta s$

was the longitudinal distance from the vehicle to the goal. 

In this quiz, we'd like you to implement the cost function in C++, but with one important change. The finite state machine we use for vehicle behavior also includes states for planning a lane change right or left (PLCR or PLCL), and the cost function should incorporate this information. We will provide the following four inputs to the function:

- Intended lane: the intended lane for the given behavior. For PLCR, PLCL, LCR, and LCL, this would be the one lane over from the current lane.
- Final lane: the immediate resulting lane of the given behavior. For LCR and LCL, this would be one lane over.
- The

$\Delta s$

distance to the goal.
- The goal lane.

Your task in the implementation will be to modify

$|\Delta d|$

in the equation above so that it satisifes:
-

$|\Delta d|$

is smaller as both intended lane and final lane are closer to the goal lane.
- The cost function provides different costs for each possible behavior: KL, PLCR/PLCL, LCR/LCL.
- The values produced by the cost function are in the range 0 to 1.

You can implement your solution in `cost.cpp` in the workspace below.

>Note: 
1. The code for this exercise is present in the directory `/home/workspace/quizzes/01_impl_cost_fn_cpp/`. The solution is present in `/home/workspace/solutions/01_impl_cost_fn_cpp/`
2. To run your code, you first need to compile all the **.cpp** files. For this exercise, you can compile the code by running the following commands from the workspace terminal:
	```bash
    cd /home/workspace/quizzes/01_impl_cost_fn_cpp/
    g++ cost.cpp main.cpp
    ```
3. The compiler will generate an executable file with the name **a.out**. Run the executable file from the workspace terminal as follows:
	```bash
    ./a.out
    ```
4. You can test your output against the output of the solution code. Run the solution code as follows:
	```
    cd /home/workspace/solutions/01_impl_cost_fn_cpp/
    g++ cost.cpp main.cpp
    ./a.out
    ```
