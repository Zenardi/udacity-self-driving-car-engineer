# Circle-Based Collision Detection

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=QGIOwMJRHaE)

## Summary

**Circle-Based Collision Detection**
=====================================

This project involves implementing a circle-based collision detection system for vehicles. The goal is to determine whether two or more vehicles collide based on their positions and orientations.

### Key Concepts

* **Collision Detection**: A point is inside a circle if the distance between the point and the center of the circle is smaller than the radius of the circle.
* **Circle Intersection**: Two circles intersect if the distance between their centers is smaller than the sum of their radii.
* **Effective Footprint**: Three aligned circles provide the most effective footprint for collision detection.
* **Circle Placement**: Circles should be placed at specific locations and orientations to achieve an effective footprint. For a compact car, three circles of 1.5 meters radius each are used, located at:
	+ One meter behind the center
	+ One meter ahead from the center
	+ Three meters ahead from the center
* **Accounting for Vehicle Heading**: The x and y coordinates of the center of each circle can be calculated using simple trigonometry, taking into account the vehicle's heading angle (Theta).
* **Collision Checking Algorithm**:
	1. Calculate the distance between the centers of two circles.
	2. Check if the distance is smaller than the sum of their radii.

### Practical Notes

To implement a circle-based collision detection system, you will need to:

1. Calculate the center coordinates (x and y) of the three circles for each vehicle using the equations provided.
2. Use the `circle_offsets` variable to determine the locations of the circles.
3. Apply the equations to calculate the x and y coordinates of each circle based on the vehicle's heading or yaw.
4. Check for collisions by calculating the distance between the centers of two circles and comparing it with the sum of their radii.

Note: The Udacity lesson provides a problem statement and an exercise to generate a circle-based collision detection function, which involves implementing these concepts in code.

## Transcript

So far we know that circles are our best choice to detect collisions. But how do we do that? Well, a point will be inside the circle if the distance between the point and the center of the circle is smaller than the radius of the circle. If it's inside, we have a collision and if it's outside, there is no collision. Now that you have built an intuition about how to check for collision when we are talking about a point, let us now take a look at how we can check if two vehicles collide.

Since vehicles will be represented with three circles each, we need to figure out how to check if two circles intersect. We can do that by checking if the distance between their centers is smaller than the sum of their radius. To be able to check for a collision in any possible orientation between two vehicles, we must perform the check with all the circles of one car with respect to all the other circles from the other car, pairwise. Even though the pair made with the middle circle of both cars is unlikely to bring any new valuable information. This totals up to nine comparisons for every collision check between two vehicles.

So far we have learned that circles are a good choice for collision checking and that three circles aligned provide the most effective footprint. Now the question is, how big these circles need to be and how do we need to align them to get that effective footprint? For simplicity, we'll do the calculations for the average compact car. The rough average dimensions are five meters long by two meters wide. With this dimensions and having the longitudinal center of the vehicle being located at about two-thirds from the front bumper, we can calculate that three circles of about 1.5 meters radius each, and located, as you can see in this image, at one meter behind the center, one meter ahead from the center, and three meters ahead from the center will provide the desired footprint.

The last aspect of the circle base collision detection that we need to talk about is, how do we account for the vehicles heading when we are placing the circle? In other words, what are the x and y coordinates of the center of each circle given a specific vehicles heading? On the image on the left, you see our ego car with a heading angle of Theta ego. On the image on the right, you can see projected only circle three for simplicity. Using simple trigonometry, we can locate the center of the circle, as you can see in this two equations.

At this point, you have all the necessary ingredients to perform a circle based collision detection, whether dynamic or static. Let's summarize what we have learned in this section. We explain how to perform collision check-in with a point-mass and with other vehicles. We discuss what should be the ideal location and size for a perfect footprint, and finally, we'll discuss how we account for vehicles heading. In this video, we'll go through the collision checking exercise.

Let's take a look at the problem statement. In this exercise we'll generate a circle-based collision detection function. To do so, you'll have to do two things. One, to calculate the center coordinates, x and y of the three circles that will represent every car. To do that, you will have to use circle_offsets, which will give it to you.

The circle_radii, which is another variable that will be given to you and the vehicles' heading or yaw. With this information, you will be able to apply these equations that will give you the x and y coordinates of every circle that you wanted to calculate for the ego car and for the object or obstacle cars. Once you have this circles placed, the only thing that is left to do is check for collisions. The way you do that is you calculate first the distance between the two centers, and then check if the distance is smaller than the addition of their radiuses. If this is smaller then the two circles intersect, and therefore there's a collision.

If it's bigger, there is no collision. So let's see how we do these two things. First, we need to calculate the x and y coordinates of the center of each of the three circles that represent the ego car. The equations that we mentioned earlier are located here. As we said earlier, after you have located the circles, now we need to check for collisions.

The way we do this is we do have a for loop that allows you to create the actors or the other vehicles circles and after that detect the collision. The first to do that you have in this section is first calculate the distance between the center of the two circles. You have the equations here. The second part is once you have the distance, you now need to check for collisions. The way you check for that is, if the distance is less than the addition of the two radiuses, then you have a collision.

After you finish this, you should be able to detect the collision between the seven objects that we included in the main function.

## Additional Content

### Collision Detection

#### Point mass collision check

* **Inside or outside the circle**: Distance between point

$(x_i,y_i)$

and center circle

$(x_c, y_c)$

* Collision if

$\sqrt{[ (x_i - x_c)^2 + (y_i - y_c)^2]} <= R$

#### Vehicle to Vehicle collision check

* **2 circles intersect when the **distance between their centers

$(x_{c1},y_{c1}) and (x_{c2}, y_{c2})$

is smaller than the sum of their radii.   
* Collision if

$\sqrt{[ (x_{c1} - x_{c2})^2 + (y_{c1} - y_{c2})^2 ]} <= (R1 + R2)$

#### Circles location and size on an average compact car for perfect coverage

* Circles should be located at: [-1m, +1m, +3m] On the centerline
* With 1.5 m Radius

### X and Y coordinates of circles' center

* x

c

= x

ego

+ Offset dist * cos(θ

ego

)
* y

c

= y

ego

+ Offset dist * sin(θ

ego

)
* Where:
   * x

ego

= Car "center" X coordinate on the world reference frame
   * y

ego

= Car "center" Y coordinate on the world reference frame
   * θ

ego

= Car heading in world coordinates
## Pre-exercise Walkthrough
