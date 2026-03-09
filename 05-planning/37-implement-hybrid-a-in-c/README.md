# Implement Hybrid A* in C++

> Part of: **Trajectory Generation**

## Additional Content

## Implementing Hybrid A*
In this exercise, you will be provided a working implementation of a *breadth first* search algorithm which does **not** use any heuristics to improve its efficiency. Your goal is to try to make the appropriate modifications to the algorithm so that it takes advantage of heuristic functions (possibly the ones mentioned in the previous paper) to reduce the number of grid cell expansions required.

### Instructions:

1. Modify the code in `/home/workspace/quiz/hybrid_breadth_first.cpp`.
2. Note the number of expansions required to solve an empty 15x15 grid (it should be about 18,000!). Modify the code to try to reduce that number. How small can you get it?
3. Check your output against the output of the solution code.

>Note: 
1. The code for this exercise is present in the directory `/home/workspace/quiz/`. The solution files are present in `/home/workspace/solution/`
2. To run your code, you first need to compile all the **.cpp** files. For this exercise, you can compile the code by running the following commands from the workspace terminal:
	```bash
    cd /home/workspace/quiz/
    g++ main.cpp hybrid_breadth_first.cpp
    ```
3. The compiler will generate an executable file with the name **a.out**. Run the executable file from the workspace terminal as follows:
	```bash
    ./a.out
    ```
4. You can test your output against the output of the solution code. Run the solution code as follows:
	```bash
    cd /home/workspace/solution/
    g++ main.cpp hybrid_breadth_first.cpp
    ./a.out
    ```
