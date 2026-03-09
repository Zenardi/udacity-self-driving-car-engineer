# Path Planning: Polynomial Splines & Spirals

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=iU-r-3tDfqE)

## Summary

**Parametric Curves in Path Planning**
=====================================

This project explores the use of parametric curves in path planning, specifically polynomial splines and polynomial spirals. We delve into the challenges associated with these representations and introduce Simpson's rule as a numerical integration technique to approximate integrals.

**Key Concepts**
---------------

* **Parametric Curves**: Representations used to describe paths in a problem space.
* **Polynomial Splines**: Piece-wise connected parametric curves where x and y coordinates are defined by polynomials. (e.g., quintic spline)
* **Polynomial Spirals**: Curves whose curvature is a polynomial function of the arc length S.
* **Simpson's Rule**: A numerical integration technique used to approximate integrals, often more precise than other methods.

**Practical Notes**
------------------

To implement Simpson's rule, you will need to:

1. Calculate `Theta` using the provided expression and return its value.
2. Implement the `integrate_by_Simpson` function, which takes `Delta_x` and `n` as inputs. This function calculates the sum of odd and even elements and multiplies them by 4 and 2, respectively, according to Simpson's rule equation.

Example code for implementing Simpson's rule:
```python
def integrate_by_Simpson(Delta_x, n):
    # Calculate sum of odd elements
    odd_sum = 0
    for i in range(1, n+1, 2):
        x_i = a + i * Delta_x
        odd_sum += f(x_i)

    # Calculate sum of even elements
    even_sum = 0
    for i in range(2, n+1, 2):
        x_i = a + i * Delta_x
        even_sum += f(x_i)

    # Apply Simpson's rule equation
    result = (Delta_x / 3) * (4 * odd_sum + 2 * even_sum)
    return result

# Define the function to integrate
def f(x):
    # Replace with your own implementation
    pass
```
Note: This is a simplified example and you should adapt it to your specific use case.

## Transcript

The first question we must ask ourselves is, why do we use parametric curves in path planning? They make setting up and solving the path planning problem way easier, which translates mainly into less computational load and faster results. The first type of parametric representations we mentioned earlier was the polynomial spline. Polynomial splines are piece-wise connected parametric curves where the equations that describe the coordinate x and y are polynomials. One of the most common used splines in path planning is the quintic spline.

Quintic splines have x and y coordinates defined by a fifth order polynomials as you can see here. What are the polynomial spline challenges when it comes to solving the path planning problem? Well, since we need to satisfy the vehicles curvature constraint, we are forced to calculate the curvature given x and y equations. As you can see from the formal mathematical definition of curvature in 2D, it's hard to guarantee that we will not have discontinuities in the curvature or its derivatives. For this reason, polynomials splines are not a good choice for this problem where we are using curvature as one of the coordinates in the state space and where the vehicle has a curvature constraint.

The second type of parametric representations we mentioned was the polynomial spiral. Polynomial spirals are curves whose curvature is a polynomial function of the arc length S. For example, you can see here a third-order polynomial spiral, also known as a cubic spiral, which actually is one of the most commonly used polynomial spirals in path planning due to its combination of simplicity and smoothness. The same way splines had challenges, polynomial spirals are not free from them either. With the splines, we had the coordinate x and y well-defined as polynomials and we encountered a problem calculating the curvature.

In the case of polynomial spirals, we have exactly the opposite problem. We have a well-defined curvature as a cubic polynomial and now we need to get x and the y coordinates. By definition, x and y coordinates can be obtained by solving these two integrals you see here. Unfortunately, these integrals don't have a closed form solution and we're forced to solve them by other means. Let's take a look at how to solve this challenge and if it is a big problem, like the curvature was for the spline.

To solve this integrals, we will need to use a numerical integration technique. Many exist, but we will apply one called Simpson's rule. Simpson's rule is a commonly used numerical integration technique that is often more precise than other numerical methods. Let's summarize what we have talked about in this section. We explained why the use of parametric curves is a good choice to set up and solve the path planning problem.

We introduce the two most common parametric curves representations used in path planning, the quintic spline and the cubic spiral, and we explained the challenges that both representations have. Finally, we chose the polynomial spirals as the best choice. In this video, we're going to go through the Simpson's rule exercise, and the first thing we're going to do is it's starting with the code. We're going to read the problem statement. In this exercise, you will calculate the value of the integral x of s, and we're going to check out exactly right now what this integral is.

What we are trying to calculate is x of s the integral of cos of Theta varies between zero and s, s being the length of the curve. As you remember from the lectures, this integral doesn't have any closed form solution, and that's why we need to use Simpson's rule to approximate this integral. The only two things that you need to calculate this integral using Simpson's rule is Theta_s and we're going to check right now the definition of Theta_s. Theta_s is this expression right here. We're going to assume right now that Theta_0 is 0 all the time, so we care about only this polynomial, which is also for help is written in here.

Again, denote this it says that Theta_0 would be always assumed to be 0, and the other thing that you need to know is basically the expression of Simpson's rule. What is the equation of Simpson's rule? This is also written in here, as you remember from the lectures. Simpson's rule is basically another polynomial that is calculated as Delta_x divided by 3 and multiplied by an addition of elements. This element depends on the number n.

If we do Simpson's rule extension for nine elements, we'll have nine elements in here. One of the major characteristics that you need to see is that all odd numbers starting from x_1, so when we do f of x_1 is multiplied by 4, so f of x_3 is also multiplied by 4, and so on. As you can see, expressed right here, 4 times f of x_n minus 1. Then the other thing that you see is that the even numbers is starting from x_2, are multiplied by 2. Here you have 2 times f of x_2 and 2 times f of x_4, and so on until you get to 2 times f of x_n minus 2.

The expression here, Delta_x describes what in this case, Delta_x is going to be is the range of the integral. This is going to be an integral from a to b in our case, and we can go back to the other slide to remember, in our case, x of s is going to be between zero and s. In this case, zero is a and b is s or as I said before, the length of the curve. Delta_x is basically b minus a, and in this case, as we said, is s minus a 0. This is going to be s divided by n.

I remind you that n is a number that we decide. When we wanted to expand the Simpson's rule, we decide how many terms do we wanted to use. In the example is something pre-established to be nine so you don't have to worry about it. X of i, basically the values that you're going to be calculating, f of x, x of i is a plus i times Delta_x x. Delta_x is being calculated here, i is basically the number, so in this case will be x_1 will be the 1, x_2 will be a 2, and so on.

The a, as we said before, is the beginning of the interval that we are going to integrate. It's going to be actually from zero to s. In this case, this is a zero. Let's take a look at the to-dos on the exercise. The first to do that you will see here is calculate Theta.

In this case is asking you what is the expression of Theta? We already gave you the expression of Theta in here, and we also give it to you on the lectures. So you just need to implement the expression of Theta here and return this value. You have access to s and a. S is the value that we're going to inject in the function Theta, and a is basically the array of doubles that contains the different a values that you will see here.

A of 0 would be this one. The first element of a will be this one, the second element of a will be this one, and so on. I think that shouldn't be difficult for you to do. The second to do is located in this function integrate by Simpson. You are giving the function the Delta_x or ddx and n, which is the number of elements that we're going to expand Simpson's rule.

This initial part has been done for you to make it more simple, and in this for loop, the only thing we do is calculate the sum of the even and the odd elements. Lets take a look exactly at what is this. Basically what we did in this for loop is we took x_1, x_3, x_5, and so on until we get to n and we add them. Then we take x_2, x_4, and so on, we get the even numbers and we add them. As you see here, this is exactly what this has done.

After that, you know that you need to multiply the odd additions by four, and the even additions by two, as the Simpson's rule equation showed you in here. All the odd function numbers will be multiplied by four and the even numbers will be multiplied by two. This part of the exercise, the only thing you need to do is implement function rule as described here. Again, remember that in this case we give you already access to the sum of the odd numbers and the sum of the even numbers. Finally, we're going to go to the last to-do of this exercise.

If we read exactly what it's asking us to do, it says, what is s of i, or in this case, what is x or i in Simpson's rule? Let's take a look at the definition. We define x of i here and we said that it was going to be a plus i Delta_x. Delta_x is here, a we said that this is the beginning of the interval that we are integrating on, which is zero in this case is from zero to s. If you don't remember that, you can go to the previous slide and we said that this is the beginning of the interval and this is the end of the interval.

In this case, we know that this Delta is going to be s minus 0 divided by n, and in this case, once we have Delta_x, we just need to, for every single x, for example, for x_1, this would be 0 plus 1 times Delta_x, which is Delta_x. For x_2 would be 0 plus 2 times Delta_x, and so on. This is the hint which gives you all the information of what we know from Simpson's rule and it gives you a little hint to help you out to develop this part of the question. That's it.

## Additional Content

## Why do we use parametric curves in Path Planning?

* Simplicity!

## Polynomial Splines

* Are piecewise connected Parametric Curves where the equations that describe the coordinates X and Y are polynomials.
* One of the most commonly used Splines in Path Planning is the Quintic Spline
* Quintic Splines have X and Y coordinates defined by 5th order polynomials

## Polynomial Splines Challenges

Having x(s) and y(s) (s being a parameter) as the parametrization of the curve, the curvature is defined as:

$\Large k=\frac{(x'. y'' - y'. x'')}{(x'^2 + y'^2)^{3/2}}$

Curvature constraints are hard to guarantee due to:

* Discontinuities on 𝜅(s)
* Discontinuities on its derivative: 𝜅’(s).

## Polynomial Spirals

* Curves whose curvature is a polynomial function of the arc length s are called polynomial spirals
* One of the most commonly used Polynomial Spirals in Path Planning is the Cubic Spiral

## Polynomial Spirals Challenges

* Having the curvature as the parametrization of the curve, it turns out that to get the coordinates X,Y for every point we need to solve two integrals that have no closed-form solution.
* To solve this problem we use Simpson's Rule to Approximate the solution for both.
## Simpson's Rule Pre-Exercise Walkthrough
