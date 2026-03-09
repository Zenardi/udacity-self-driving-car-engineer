# Implement a Second Cost Function in C++ (solution)

> Part of: **Behavior Planning**

## Additional Content

One possible solution for the previous quiz is the following:
```
double inefficiency_cost(int target_speed, int intended_lane, int final_lane, 
                         const std::vector

&lane_speeds) {
  // Cost becomes higher for trajectories with intended lane and final lane 
  //   that have traffic slower than target_speed.
  double speed_intended = lane_speeds[intended_lane];
  double speed_final = lane_speeds[final_lane];
  double cost = (2.0*target_speed - speed_intended - speed_final)/target_speed;
  
  return cost;
}
```
