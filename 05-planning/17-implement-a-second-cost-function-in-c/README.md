# Implement a Second Cost Function in C++

> Part of: **Behavior Planning**

## Additional Content

In most situations, a single cost function will not be sufficient to produce complex vehicle behavior. In this quiz, we'd like you to implement one more cost function in C++. We will use these two C++ cost functions later in the lesson. The goal with this quiz is to create a cost function that would make the vehicle drive in the fastest possible lane, given several behavior options. We will provide the following four inputs to the function:

- Target speed: Currently set as 10 (unitless), the speed at which you would like the vehicle to travel.
- Intended lane: the intended lane for the given behavior. For PLCR, PLCL, LCR, and LCL, this would be the one lane over from the current lane.
- Final lane: the immediate resulting lane of the given behavior. For LCR and LCL, this would be one lane over.
- A vector of lane speeds, based on traffic in that lane: {6, 7, 8, 9}.

Your task in the implementation will be to create a cost function that satisifes:
- The cost decreases as both intended lane and final lane are higher speed lanes.
- The cost function provides different costs for each possible behavior: KL, PLCR/PLCL, LCR/LCL.
- The values produced by the cost function are in the range 0 to 1.

You can implement your solution in `cost.cpp` in the workspace below.

>Note: 
1. The code for this exercise is present in the directory `/home/workspace/quizzes/02_impl_second_cost_fn_cpp/`. The solution is present in `/home/workspace/solutions/02_impl_second_cost_fn_cpp/`
2. To run your code, you first need to compile all the **.cpp** files. For this exercise, you can compile the code by running the following commands from the workspace terminal:
	```bash
    cd /home/workspace/quizzes/02_impl_second_cost_fn_cpp/
    g++ cost.cpp main.cpp
    ```
3. The compiler will generate an executable file with the name **a.out**. Run the executable file from the workspace terminal as follows:
	```bash
    ./a.out
    ```
4. You can test your output against the output of the solution code. Run the solution code as follows:
	```bash
    cd /home/workspace/solutions/02_impl_second_cost_fn_cpp/
    g++ cost.cpp main.cpp
    ./a.out
    ```
