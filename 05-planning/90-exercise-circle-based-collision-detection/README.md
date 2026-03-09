# Exercise: Circle-Based Collision Detection 

> Part of: **Motion Planning**

## Additional Content

## Problem Statement

In this exercise you will generate a circle-based collision detection function.
To do so, you'll have to:
1. Calculate the center coordinates (x,y) of the 3 circles that will represent
every car. To do that, you will use: 
  1.  CIRCLE_OFFSETS = distance that the circles should be at wrt to the center of the vehicle and on the center-line of
the vehicle. 
 2. CIRCLE_RADII = the radii of the circles. 
 3. The vehicles' heading/yaw.

``` 
circle_center.x =  vehicle.location.x +  CIRCLE_OFFSETS[c] * std::cos(vehicle.rotation.yaw);
circle_center.y =  vehicle.location.y +  CIRCLE_OFFSETS[c] * std::sin(vehicle.rotation.yaw);
```

2) Once the circles are placed (i.e we know their centers' coordinates) for both, the ego car and the "actor", we can proceed to check for
collisions. Here you will have to, pairwise (taking 1 circle from ego and 1 circle form the actor) check if they intersect (collision) or not.
```
dist = std::sqrt(
           std::pow((ego_circle_center.x - actor_circle_center.x), 2) +
           std::pow((ego_circle_center.y - actor_circle_center.y), 2));
collision = (dist < (CIRCLE_RADII[c1] + CIRCLE_RADII[c2]));
```
### In order to compile the code, you'll need to create a new terminal and use the command `g++ -o output quiz.cpp`
