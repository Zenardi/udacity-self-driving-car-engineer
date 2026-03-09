# A* Reminder

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lxCCtgHk5Vs)

## Summary

**A-Star Search Algorithm**
==========================

The A-star algorithm is a variant of the search algorithm that uses a heuristic function to guide the search and find the optimal path to the goal. Unlike other search algorithms, A-star takes into account an estimate of the distance from each node to the goal, allowing it to make more informed decisions about which nodes to expand next.

**Key Concepts**
---------------

* **Heuristic Function**: A function that estimates the distance from a given node to the goal. The heuristic function must be optimistic and underestimate or equal the true distance.
* **F-Value**: The cumulative g-value (the cost of reaching a node) plus the heuristic value. The f-value is used to determine which nodes to expand next.
* **G-Value**: The cost of reaching a node from the start node.
* **H-Value**: The heuristic value, which estimates the distance from a given node to the goal.

**Practical Notes**
------------------

To implement A-star, you need to:

1. Define a heuristic function that estimates the distance from each node to the goal.
2. Initialize an open list with the start node and its g-value set to 0.
3. Add the f-value (g-value + heuristic value) for each node in the open list.
4. Expand the node with the lowest f-value, removing it from the open list.
5. Repeat steps 3-4 until the goal node is reached.

Example Use Cases:

* Self-driving cars use A-star to navigate through complex environments and avoid obstacles.
* Route planning algorithms use A-star to find the shortest path between two points.
* Video games use A-star to implement AI characters that can navigate through levels.

## Transcript

Now I want to come with you to the absolute meat of this class, which is called A-star. A-star was invented by Nels Nelson at Stanford many years ago, and is a variant of the search algorithm that's more efficient than expanding every node. If you've gotten so far, and you understand the mechanism for searching by gradually expanding nodes in the open list, A-star is almost the same thing but not quite. To illustrate A-star I'm going to use the same grid as before but with a different obstacle configuration. This is oine way A-star performs really well.

Obviously we are forced to go down to here, but in here we still have to search for the optimal path for the goal. Here is the same in problem code; you can see all the ones over here. Start set is over here, goal set is over here. If I run this code and give you my expand list, the ones you programmed before, you'll find that the expansion goes down from here, but then it expands into the open space. Diagonally it expands into the open space and until it finally hits the goal node 15.

This took 16 expansions to get to this point. Let me now switch on A-star and run the code again. What we now find it only takes 10 expansions to get to this point, zero to nine over here. So it expands down to four, but then it expands straight toward the goal never touching this area over here, somehow magically knowing that up here the path to the goal will be longer than going straight. Now I didn't cheat.

I didn't tell it that there's a straight path over here. So let me put an obstacle right here next to the goal and run A-star again. What you'll find it does expand up to seven over here but then moves to the second line over here, expands up here, and then hits the goal again. So it kind of does the minimum amount of work necessary to make maximum progress to the goal. That's A-star, and now we look into A-star in more detail.

A-star uses a so called heuristic function, which is a function that has to be set up. If its all zeros then A-star resorts back to the search algorithm already implemented. If we call the heuristic function h, then for each cell it results into a value. So let me give you some values. Here is one: Its number of steps it takes to the goal if there was no obstacle.

Clearly the number I'm putting in right now , 1, 2, 3, 4, 5, and so on, are not reflective of the actual distance to the goal because they don't consider the obstacles. In a world without obstacles the heuristic function that I'm giving you would actually measure the distance to the goal. So the heuristic function has to be an optimistic guess how far we are from the goal. So put differently, for any cell x y the heuristic function has to be an optimistic guess, which means a smaller equal to the actual goal distance from the coordinate x and y. Now that sounds a little bit ad hoc, but very often you can give good heuristic functions really easily like in this case over here.

If we just know that the agent can move left, right, up, or down, it's really easy to say what is the number of steps it would take the agent with no obstacles to get to the goal location, and that's this table over here. That is easily generated automatically. Now in reality this is an underestimate. If obstacles, for example, look like this then from here it takes you more than 9 steps to get to the goal. It takes you 13 steps to over the hump over here.

Therein lies the beauty of the heuristic function. It doesn't have to be accurate. If it was accurate you probably already solved the planning problem. There has to be a function that helps you understand where to search next in the case of ties, and it has to be just so that it underestimates or at best equals the true distance from the goal. Many, many problems have functions like these in our self-driving car.

We use a function just like this; in fact the function I was just showing you, we are using in our software for free-form navigation. It boils down much to the number of which cell steps but for the Euclidean distance to a target location. I hope you understand how heuristic function might look like. It has many, many value heuristic function including setting everything to zero, which would not really help me. So let's work with this one heuristic function.

Here is the heuristic function in the code. You can see the same heuristic function. The key modification now for our search algorithm is really, really simple. We again have an open list, and we add our state, we write down the g-value, but we also write down the g-value plus the heuristic value. G-value here is zero; heuristic value is 9.

So the sum of the two is 9, and I call this the f-value. This is the cumulative g-value plus the heuristic value as looked up in the table over here. If I now expand I remove the element with the lowest f-value and not the lowest g-value. That's all there is to A-star. Let me give you an example.

Say we went to the open list all the way down here. That is we expanded all these states over here, and this is the one present here on the open list. Our g-value will be 5. Our heuristic will be 4, and the sum is 9 as before. Let's now expand this node.

We get to this one over here, the g-value increases to 6. G plus heuristic is still 9. Now let's expand it more, and there's now two options finally: This state over here and this state over here. The one up here is called 3 2, the one on the right is called 4 3. The g-value over here in both cases is 7, but when we add the h-value we get a difference.

Up here we find the h-value to be 4. We kind of moved a little bit away from the goal according to the heuristic. That gives us a total of 11. Whereas for the feed over here we find the h-value to be 2. Here is the first time that A-star makes an actual difference.

It has a preference to expand this node over here over the node over here. To see why the f-value, the sum of g and h, over here is 9 but over here is 11. What this reflects is that, according to the heuristic, this guy is actually 2 steps closer to the goal than this guy over here. This guy, according to the heuristic, may be 2 steps away from the goal, and the guy over here is at least 4 steps away. A-star now will expand this node over here because its f-value is 9 versus 11.

So let's do this. In expanding this node we find there is two valid neighbors: the guy up here and the guy on the right. The first guy's coordinate are 3 3. The second guy is 4 4. As before we increment the g-value by one.

It was eight in both cases. Now we add the heuristic to the g-value, which for the first one over here is 3; Whereas for the one on the right we get one as the heuristic. That's the result of expanding the node over here. Here is our new open list, and again we have a preference. On the open list are these three states, and we prefer the one on the right because its f-value is smaller than the other two f-values.

The one over here is 9; the ones over here have an f-value of 11. So once again we expand, and in the expansion will be the goal state, and then we find the goal set and we're done without ever expanding anything in the maze up here. That feels like magic, but the key thing here is by providing additional information, the so called heuristic function, we can guide the search. When we have an impasse we can pick a node that looks closer to the goal state. As a result we will likely make more progress towards the goal.

## Additional Content

## A\* Reminder

If you'd like to refamiliarize yourself with the A\* search algorithm (covered in lesson 1), feel free to watch the video below. The question at the bottom of the page will be asked again later in the lesson in regards to Hybrid A\*.
