# Coding the Motion Model

Udacity Self-Driving Car Engineer Nanodegree — Project 4: Localization

## Overview

This exercise implements the **motion model** step of a 1D Markov localization filter. The vehicle moves along a 25-meter map containing landmarks at positions 5, 10, and 20 m. At each time step, the motion model estimates the probability of being at position *x* by convolving the prior belief distribution with a Gaussian transition probability.

### Mathematical formulation

$$
p(x_t \mid u_t, x_{t-1}) = \sum_{x_{t-1}} p(x_t \mid u_t, x_{t-1}) \cdot \text{prior}(x_{t-1})
$$

Where:
- `pseudo_position` — candidate position *x* at time *t*
- `movement` — control input (distance moved per time step)
- `priors[j]` — prior probability of being at position *j* at *t−1*
- Transition probability uses `normpdf(x_t - x_{t-1}, movement, control_stdev)`

## File Structure

```
.
├── main.cpp       # Entry point + TODO: implement motion_model()
├── helpers.h      # Helpers::normpdf() — 1D Gaussian PDF utility
└── solution/
    └── main.cpp   # Reference implementation
```

## Prerequisites

- C++17-compatible compiler (g++ ≥ 7 or clang++ ≥ 5)

No external libraries required — only the C++ standard library and `<math.h>`.

## Build & Run

```bash
# Compile
g++ -std=c++17 main.cpp -o motion_model

# Run
./motion_model
```

Output is tab-separated `position  probability` pairs for each of the 25 map positions:

```
0    1.65867e-07
1    1.50359e-05
...
5    0.0772117
...
```

### Build & run the reference solution

```bash
g++ -std=c++17 solution/main.cpp -o solution/motion_model
./solution/motion_model
```

## Your Task

Implement the `motion_model()` function in `main.cpp` (marked with `// YOUR CODE HERE`).

The function must loop over all previous positions *j*, compute the Gaussian transition probability from *j* to `pseudo_position` given `movement`, and accumulate the weighted sum:

```cpp
for (float j = 0; j < map_size; ++j) {
    float distance_ij = pseudo_position - j;
    float transition_prob = Helpers::normpdf(distance_ij, movement, control_stdev);
    position_prob += transition_prob * priors[j];
}
```

## Parameters

| Parameter              | Value | Description                              |
|------------------------|-------|------------------------------------------|
| `map_size`             | 25    | Number of discrete positions on the map  |
| `landmark_positions`   | 5, 10, 20 | Landmark locations (metres)         |
| `movement_per_timestep`| 1.0   | Control input: distance moved (metres)   |
| `control_stdev`        | 1.0   | Standard deviation of control noise      |
| `position_stdev`       | 1.0   | Standard deviation used to seed priors   |
