# Implement Behavior Planner in C++

> Part of: **Behavior Planning**

## Additional Content

## Implement a Behavior Planner

In this exercise, you will implement a behavior planner and cost functions for highway driving. The planner will use prediction data to set the state of the ego vehicle to one of 5 values and generate a corresponding vehicle trajectory: 

* `"KL"` - Keep Lane
* `"LCL"` / `"LCR"`- Lane Change Left / Lane Change Right
* `"PLCL"` / `"PLCR"` - Prepare Lane Change Left / Prepare Lane Change Right

The objective of the quiz is to navigate through traffic to the goal in as little time as possible. Note that the goal lane and s value, as well as the traffic speeds for each lane, are set in `main.cpp` below. Since the goal is in the slowest lane, in order to get the lowest time, you'll want to choose cost functions and weights to drive in faster lanes when appropriate. We've provided two suggested cost functions in `cost.cpp`.

#### Instructions

1. **Implement the **`choose_next_state`** method in the **`vehicle.cpp`** class.** You can use the

Behavior Planning Pseudocode

page in the current lesson as a guideline for your implementation. In this quiz, there are a couple of small differences from that pseudocode: you'll be returning a best trajectory corresponding to the best state instead of the state itself. Additionally, the function inputs will be slightly different in this quiz than in the classroom concept. For this part of the quiz, we have provided several useful functions:
   1. `successor_states()` - Uses the current state to return a vector of possible successor states for the finite 
   state machine.
   1. `generate_trajectory()` - Returns a vector of Vehicle objects representing a vehicle trajectory, given a state and predictions. Note that trajectory vectors might have size 0 if no possible trajectory exists for the state. 
   1. `calculate_cost()` - Included from cost.cpp, computes the cost for a trajectory.
1. **Choose appropriate weights for the cost functions in **`cost.cpp`** to induce the desired vehicle behavior.** Two suggested cost functions have been implemented based on previous quizzes, but you are free to experiment with your own cost functions. The `get_helper_data()` function in `cost.cpp` provides some preprocessing of vehicle data that may be useful in your cost functions. See if you can get the vehicle to move into a fast lane for a portion of the track and then move back to reach the goal!
1. Hit Test Run and see how your car does! How fast can you get to the goal?

> Note:   
>
>    1. The code for this exercise is present in the directory `/home/workspace/quizzes/03_impl_behavior_planner_cpp/`. The solution is present in `/home/workspace/solutions/03_impl_behavior_planner_cpp/`  
>    1. To run your code, you first need to compile all the **.cpp** files. For this exercise, you can compile the code by running the following commands from the workspace terminal:  
>    ```bash  
>     cd /home/workspace/quizzes/03_impl_behavior_planner_cpp/  
>     g++ cost.cpp main.cpp road.cpp vehicle.cpp  
>    ```  
>    1. The compiler will generate an executable file with the name **a.out**. Run the executable file from the workspace terminal as follows:  
>    ```bash  
>     ./a.out  
>    ```  
>    1. You can test your output against the output of the solution code. Run the solution code as follows:  
>    ```bash  
>     cd /home/workspace/solutions/03_impl_behavior_planner_cpp/  
>     g++ cost.cpp main.cpp road.cpp vehicle.cpp  
>     ./a.out  
>    ```  
>
### Extra Practice

Provided in one of the links below is a zip file `python_3_practice`, which is the same problem written in Python 3 - you can optionally use this file for additional coding practice. In the `python_3_solution` link, the solution is provided as well. If you get stuck on the quiz see if you can convert the python solution to C++ and pass the classroom quiz with it. You can run the python quiz with `python simulate_behavior.py`.
##### Supporting Materials
*

[python_3_practice](https://video.udacity-data.com/topher/2017/November/5a024c18_python-3-practice/python-3-practice.zip)

*

[python_3_solution](https://video.udacity-data.com/topher/2017/November/5a024c70_python-3-solution/python-3-solution.zip)
