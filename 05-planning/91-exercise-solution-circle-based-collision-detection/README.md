# Exercise Solution: Circle-Based Collision Detection 

> Part of: **Motion Planning**

## Additional Content

Refer to the code below to check the solution to the exercise you just completed!
## TODO - Circle placement: Where should the circles be at?
```
      Location ego_circle_center;
      ego_circle_center.x = ego_vehicle.location.x + CIRCLE_OFFSETS[c] * std::cos(ego_vehicle.rotation.yaw);
      ego_circle_center.y = ego_vehicle.location.y + CIRCLE_OFFSETS[c] * std::sin(ego_vehicle.rotation.yaw);
      for (size_t c2 = 0; c2 < n_circles && !collision; ++c2) {
        Location actor_circle_center;
        actor_circle_center.x = actor.location.x + CIRCLE_OFFSETS[c2] * std::cos(actor.rotation.yaw);
        actor_circle_center.y =  actor.location.y + CIRCLE_OFFSETS[c2] * std::sin(actor.rotation.yaw);
```
## TODO - Distance from circles to obstacles/actor: How do you calculate the distance between the center of both circles? HINT: distance between 2 points. Use std::sqrt(...)
```
double dist = std::sqrt(
            std::pow((ego_circle_center.x - actor_circle_center.x), 2) +
            std::pow((ego_circle_center.y - actor_circle_center.y), 2));
```
## TODO - What do we consider a collision? When the distance between the 2 centers is smaller that the sum of their radii.
```
        collision = (dist < (CIRCLE_RADII[c] + CIRCLE_RADII[c2]));
```
