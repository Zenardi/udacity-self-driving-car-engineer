# Exercise Solution: Boundary Conditions: Offset Goals 

> Part of: **Motion Planning**

## Additional Content

## Boundary Conditions: Offset Goals Exercise Solution
Refer to the code below to check the solution to the exercise you just completed!
## TODO - Perpendicular direction: ADD pi/2 to the goal yaw (goal_state.rotation.yaw)

The offset goals will be aligned on a perpendicular line to the heading of the main goal. To get a perpendicular angle, just add 90 degrees (or PI/2rad) to the main goal heading.
```
  auto yaw_plus_90 = goal_state.rotation.yaw + M_PI_2;
```
## TODO - offset goal location: calculate the x and y coordinates of the offset goals using "offset" (calculated above) and knowing that the goals should be laid on a perpendicular line to the direction (yaw) of the main goal. You calculated this direction above (yaw_plus_90).
    
    // From earlier we had this
    auto yaw_plus_90 = goal_state.rotation.yaw + M_PI_2;
    float offset = (i - (int)(_num_goals / 2)) * _goal_offset;

    // This is the solution
    goal_offset.location.x += offset * std::cos(yaw_plus_90);
    goal_offset.location.y += offset * std::sin(yaw_plus_90);
