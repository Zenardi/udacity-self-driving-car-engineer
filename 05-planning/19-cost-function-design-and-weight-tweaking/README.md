# Cost Function Design and Weight Tweaking

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=NK6SP-r4dGs)

## Summary

**Designing Cost Functions for Autonomous Vehicles**
=====================================================

Designing cost functions for autonomous vehicles is a challenging task. It requires balancing competing priorities, such as safety, legality, comfort, and efficiency, while ensuring that the vehicle behaves reasonably well in various situations.

**Key Concepts**
---------------

* **Cost function design difficulties**: Solving new problems without unsolving old ones, introducing breaking changes into existing systems, and balancing costs of drastically different magnitudes.
* **Regression testing**: Defining a set of test cases with expected behaviors to ensure that the vehicle behaves as intended after making changes to the cost functions.
* **Weighted cost functions**: Assigning weights to reflect the type of problem each cost function addresses, such as safety, legality, or comfort.
* **Parametrization**: Using parameter optimization techniques like gradient descent to programmatically tweak cost functions based on regression tests.
* **Vehicle state thinking**: Considering position, velocity, and acceleration when designing cost functions.

**Practical Notes**
------------------

When designing cost functions, consider the following practical steps:

1. Identify specific responsibilities for each cost function, such as safety or legality.
2. Use weighted cost functions to balance competing priorities.
3. Parametrize cost functions using parameter optimization techniques like gradient descent.
4. Consider vehicle state when designing cost functions (position, velocity, acceleration).
5. Use regression testing to ensure that the vehicle behaves as intended after making changes to the cost functions.

Example:

| Cost Function | Type | Description |
| --- | --- | --- |
| Binary "Are we exceeding speed?" | Position | Checks if the vehicle is breaking the speed limit |
| Continuous speed cost function | Velocity | Pulls the vehicle towards its target speed |
| Buffer distance cost function | Position | Keeps a safe distance from other vehicles |
| Lane keeping cost function | Position | Ensures the vehicle stays within its lane |

Note: This example illustrates how to categorize and design cost functions based on vehicle state (position, velocity, acceleration).

## Transcript

Designing cost functions is difficult and getting them all to cooperate to produce reasonable vehicle behavior is hard. Some of the difficulties associated with cost functions design include solving new problems without unsolving old ones. When you're working on a self-driving car, you may find that the vehicle is behaving reasonably well except for some particular situations. Maybe it's not being aggressive enough about making left turns at traffic lights. So, in an effort to solve this problem, you either add new cost functions, tweak existing ones, or modify the weights. But every time you do, there's a chance that you will introduce some breaking change into something that already works. In practice, we solve this through regression testing, where we define some set of situations, each of which has an expected behavior. Then, whenever we make a change, we simulate the vehicle in all of our test cases and make sure that it still behaves as expected. We won't say more about testing here, but it is an important part of developing software in a safety-critical application. The next difficulty is balancing costs of drastically different magnitudes. Because, yes, we want to get to our destination efficiently, but if we are in a situation where safety is an issue, we want to solve that problem and not think about efficiency at all. One way to do that is to have weights which reflect the type of problem the cost function addresses. So we want to most heavily penalize any behavior which simply isn't possible due to physics, then we want to think about safety, legality, comfort. And only once those are satisfied do we want to think about efficiency. But we also may want to adjust the relative importance of these weights depending on situation. If a light turns red, for example, legality becomes a much more relevant concern than when we engage in normal highway driving. And this leads us to our last difficulty, reasoning about individual cost functions. Ideally, each cost function will serve a very specific responsibility, which is something we didn't do in our earlier example of a speed cost function. We were trying to balance our desire to drive quickly, which has to do with efficiency, with our desire to not exceed the speed limit, which is legality. In practice, we might want to define several cost functions associated with vehicle speed. In which case we might have a binary cost function which just checks to see if we are breaking the speed limit and the continuous cost function which pulls us towards our target speed. By assigning each cost function to a very specific role, like safety versus legality versus efficiency, we can then standardize the output of all cost functions to be between -1 and 1. Additionally, it's helpful to parametrize whenever possible. This allows us to use some parameter optimization technique like gradient descent along with our set of regression tests to programmatically tweak our cost functions. Finally, thinking in terms of vehicle state is helpful. The things we can indirectly control about our vehicle are its position, velocity, and acceleration. It can be helpful to keep these in mind when coming up with cost functions. Let's walk through an example. Say we want to think about the following classes of cost functions. And to make it easier, to keep everything straight, let's think in terms of position, velocity, and acceleration. The binary "Are we exceeding the speed?" cost function would go here, then the cost function that wanted to keep us close to the speed limit would go here. And now, instead of being that weird discontinuous graph we made earlier, this could just be some parabola like this. And even though the cost of this is low even for speeds that exceed the speed limit, that's OK because we have our binary cost function which would prevent that behavior. Continuing to think about speed, we also might want to try to drive at a speed that's close to the average speed of traffic, for safety reasons, even if that speed is above or below the speed limit. And that would go here. In the position column, we'd have an obvious feasibility concern which is collision avoidance. We can't drive somewhere if there is already a car there. Then, for safety reasons, we would want the buffer distance, which tries to keep us far from other vehicles, and the cost function which checks to make sure we are driving on the road near the center of our lane and in a lane that's close to our goal lane. For acceleration, we'd first want to make sure we only consider behaviors that the car can execute, and then we'd want to avoid having any rapid changes in acceleration because those are perceived as uncomfortable. This is also known as jerk which you'll learn more about in the next lesson. Consider a merge onto a highway, for example. This is a potentially dangerous situation where we really want to get up to traffic speed as quickly as possible. So this cost function may become more relevant than it normally is. But we also want to make sure that we yield if there isn't really a gap, so we want to make sure this cost function and this one are weighted sufficiently high. And we can compare these merge priorities to a different situation. For example, a car approaching a green light that suddenly turns yellow. In this situation, we'd probably want to boost the weights associated with legality and would probably need to add a whole new cost function for obeying traffic rules. Now that doesn't fall neatly into the position, velocity, or acceleration classes, so I'll just put it over here. If this is all starting to feel like it's getting pretty complex, well, you're right. It's pretty hard to avoid this exploding complexity when using finite state machines. Partially that's because of the finite state machine itself, but we're also trying to solve a very hard problem and some complexity is unavoidable no matter what solution approach you take.