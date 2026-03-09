# Collision Detection

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=7zGYf3S4ku4)

## Summary

**README: Collision Detection Fundamentals**

Collision detection is a critical component of motion planning in autonomous vehicles. It involves detecting potential collisions with other objects on the road, ensuring safe navigation and preventing accidents.

### Key Concepts

* **Dynamic Collision Detection**: Detects collisions with moving objects by predicting their trajectories.
	+ Requires a set of predicted trajectories for all relevant participants in the driving scene.
	+ Checks for future collisions based on trajectory information.
* **Static Collision Detection**: Concerned with static objects on the ego vehicle's path.
	+ Does not consider time component, only presence of obstacles.
	+ Assumes objects are static, even if they may be moving.
* **Shape-Based Conservative Collision Checking**: A common technique used in motion planning for autonomous driving.
	+ Uses regular shapes to enclose the vehicle and perform collision checking.
	+ Ensures the vehicle is fully enclosed within the shape.

### Practical Notes

To implement collision detection in real-world applications, consider the following:

* Use simple and fast approximations of perfect collision detection algorithms to meet real-time requirements.
* Employ robust techniques that can handle noisy observations and imperfect measurements.
* Utilize shape-based conservative collision checking with circles as the best choice for minimizing overflow area around the vehicle.

Example code snippet:
```python
import math

def calculate_collision(shape, object):
    # Calculate distance between center of shape and object
    distance = math.sqrt((shape.x - object.x) ** 2 + (shape.y - object.y) ** 2)
    
    # Check if object is inside the shape
    if distance <= shape.radius:
        return True
    
    return False
```
Note: This code snippet is a simplified example and may not be suitable for actual implementation.

## Transcript

Collision detection is the last piece of the motion planning puzzle. Due to a safety critical nature, it's one of the most important and challenging task in motion planning. We could definitely devote a whole lesson to address this topic, but we will focus on the most relevant characteristics of collision detection for autonomous vehicles, its real-time requirements, and its safety critical nature. There are two types of collision detection, dynamic collision detection and static collision detection. We will start addressing dynamic collision detection.

This type of collision detection tries to detect collisions with objects that are in motion. To be able to do so, a set of predicted trajectories of all relevant participants in the driving scene is required. This trajectories will provide information about where and when each participant will be, allowing us to check for any future collisions. In this sense, path that intersect might not always lead to a collision as you can see in this sequence of three images. The blue vehicle is driving faster than the green vehicle and will pass the intersection point earlier, leading to no collision.

In static collision detection we are concerned about static objects that are on ego's car path. We are not concerned about the time component, but more precisely, that there is an obstacle in our path. In a static collision checking, objects are assumed to be static even though they might be moving. Let's take a look at three different scenarios. In this is scenario on the left, we have detected a collision with a tree since it's in our path.

We are not concerned about information in regards to when this collision would happen, but rather that it will happen. In the center scenario the green vehicle might be moving or might be parked. In either case, collision is detected since it's in our path. Finally, in the scenario on the right, we can see that we still don't detect any collision since no object is in our path, even though the green vehicle is moving towards the intersection. It is obvious that in real life autonomous vehicles applications, we must perform dynamic collision checking.

But it's also evident that there are many challenges. Let's take a look at them. To be 100 percent accurate in our detections and guarantee safety, we need perfect observation of the scene to accurately know where everyone is, the state of the road, that weather etc. We also need perfect internal measurements to know accurately where we are, what speed and acceleration we're traveling at, etc. All of which we don't have.

We also need long computational time, which we don't have in real-time applications. Finally, we need highly accurate predictions and intent predictions which are extremely challenging and an open area of research. In the next slides, we will see how we can tackle some of these challenges. How can we overcome these challenges? Well, since information is imperfect, algorithms need to be robust to noisy observations.

Since we don't have all the compute time in the world, algorithms need to use simple and fast approximations of a perfect collision detections, but without sacrificing safety. How do we implement this recommendations? Let's take a look. The most common collision detection techniques using motion planning for autonomous driving is the shape-based conservative collision detection. What do we mean by shape-based and conservative?

Well, in an ideal world with perfect observations and long computational time available, we would use the perfect contour of our vehicle and generate a perfect swath as we move. So we are able to evaluate what objects come in contact with us. In real life, this is not effective, so instead of perfect contour, we can use other regular shapes that fit our vehicle inside and that allows us to perform collision checking easily. The term conservative is due to the fact that the vehicle must be fully enclosed within the shape we use, as you can see in this set of images. The question now is, what shape should we use, what size should it be, and where should it be located to enclose all the vehicle?

To answer this question, we need to first ask ourselves, what's actually the main objective of what we're trying to do? Well, we want to use a shape that allows for a very fast collision check in any orientation. We want to minimize false-positive, meaning that we don't want to call it a collision when in fact it's not. Basically, we want to minimize the area of the shape where the vehicle is not there. Here we're presented this four possibilities as an example.

We know that everything that is detected inside the shape will be called as a collision. To check if something is inside the shape in any orientation, turns out that the circle is the best choice. Since we wanted to use circles to minimize the overflow area around the vehicle. You can see how the last image with three circles is our best choice. Let's summarize what we have learned in this last section of the motion planning lesson.

Collision detection is a safety critical and challenging task in motion planning, we introduced the types of collision detection, static and dynamic, and we defined each one of them. We enumerated the main challenges in collision detection, being noisy observations and measurements and the challenge of prediction and intend prediction. We introduced the most common techniques used in motion planning for autonomous driving, the shape-based conservative collision checking. We discussed the different shapes that we could possibly use and chose the circle as our best choice, finally, we also proposed three circles that made up an ideal footprint for an efficient collision detection.

## Additional Content

## Collision Detection

Due to its safety-critical nature, **collision detection** is one of the most important and challenging tasks in motion planning. We will focus on the most relevant characteristics of collision detection for autonomous vehicles: 

- The _real-time requirements_ of collision detection 
- The _safety-critical nature_ of collision detection



## Types of Collision Detection: Static and Dynamic

There are 2 types of collision detection:

### Dynamic Collision Detection

**Dynamic collision detection** tries to detect collisions with objects that are in motion. It requires a set of predicted trajectories of all relevant participants on the driving scene. These trajectories predict where and when each participant will be, allowing us to check for future collisions.

Note that paths that intersect may not always lead to a collision. In the example above, even though the paths of the blue and green vehicles intersect, the blue vehicle is driving faster and will pass the intersection earlier than the green vehicle, leading to no collision.


### Static Collision Detection

**Static collision detection** detects any static objects or obstacles that are on ego’s car path. We are not concerned about the time component in this case.

In static collision checking, objects are assumed to be static even though they might be moving. In the example above, we've looked at 3 scenarios:

1. A tree is in our path. A collision will happen, no matter when it happens.
2. A green vehicle is in our path. Whether this vehicle is moving or parked, a collision is detected, since the vehicle is in our path.
3. A green vehicle is moving towards our vehicle and our paths intersect, but since the green vehicle is not yet in our path, we don’t detect any collision.

**Conclusion: It is obvious that in real-life autonomous vehicle applications, _we must perform dynamic collision checking_.** But there are many challenges associated with this technique. 
## Collision Detection: Challenges and Solutions 

### Main Challenges of Collision Detection

We _cannot_ be 100% accurate in our detection and guarantee safety, because we do _not_ have the following:

1. Perfect observations of the scene. E.g. where everyone is, the state of the road, the weather, etc.
2. Perfect internal measurements. These measurements should tell us accurately where we are, what speed and acceleration we’re traveling at, etc.
3. “Long” computational time, which is not available in real-time applications.
4. Highly accurate predictions and intent predictions, which are extremely challenging and an open area of research.

Noisy observations & measurements, and the challenge of prediction and intent prediction.


### Solutions to the Main Challenges of Collision Detection

| **Challenge**      | **Solution** |
| ----------- | ----------- |
| Imperfect information      | Our algorithms need to be **robust to noisy observations**.        |
| Short computational time       | Algorithms need to **use simple and fast approximations** of a perfect collision detection **without sacrificing safety**.        |


## Most Common Technique Used in Motion Planning for AD

The most common collision detection technique used in Motion Planning for AD is the **Shape-based Conservative Collision Detection**. 

**Shape-based**: In real life, it is not effective to use the vehicle's exact contour due to the lack of exact observations and long computational time. Instead, we can use **other regular shapes** that fit our vehicle inside and allow us to easily perform collision checking. 
- **Conservative**: The vehicle must be fully enclosed within the shape we use.

### What Shape Should We Use?

Our main objective is to use a shape that allows for a very fast collision check _in any vehicle orientation_. Since everything that is detected inside the shape will be considered a collision, we also want to minimize false positives, i.e., we don’t want to call it a collision when in fact it’s not. So we want to _minimize the area of the shape that is not part of the vehicle_.

### Conclusion
To check if something is inside the shape in any orientation, it turns out that a **circle** is the best choice.

Since we wanted to use circles, to minimize the overflow area around the vehicle, the last image with 3 circles is our best choice.


### Collision Detection
- Collision Detection is a **safety-critical** and **challenging task** in Motion Planning
- Types of Collision Detection: **Static** and **Dynamic**
- Collision Detection Challenges: 
  - Noisy observations & measurements, 
  - Challenge of prediction and intent prediction of other actors on the driving scene
- Collision detection **algorithms need to use simple and fast approximations** of a perfect collision detection but **without sacrificing safety**.
- Most common technique used in Motion Planning for AD: 
  - Shaped-Based Conservative Collision Checking
    - In an ideal world with perfect observations and long computational time available, we would use the perfect contour of our vehicle and generate a perfect swath as we move, so we are able to evaluate what objects come in contact with us. In real-life this is not effective so instead of a perfect contour, we can use other regular shapes that fit our vehicle inside and that allows us to perform collision checking easily.
    - The term “conservative” is due to the fact that the vehicle must be fully enclosed within the shape we use as you can see in this set of images.
- Circles are ideal due to its simplicity in checking when something is inside or outside the circle
- 3 circles well placed are ideal for an average compact car collision checking.
