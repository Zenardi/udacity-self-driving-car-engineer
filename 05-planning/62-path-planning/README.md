# Path Planning

> Part of: **Motion Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=gcoTwKNrd4Q)

## Summary

**Parametric Curves for Path Planning**
=====================================

This project focuses on mathematically representing curves that vehicles describe in space. We'll explore parametric representations, which are essential for solving path planning problems.

### Key Concepts
* **Parametric Curve**: A set of equations that define a curve in two-dimensional space (R_2) using a parameter t.
	+ Each equation represents the x and y coordinates as functions of t.
	+ The parameter t varies from 0 to 1, tracing the entire curve.
* **Splines**: Parametric curves where the equations describing x and y are polynomials.
	+ Example: Cubic spline representation with coefficients a3, a2, a1, and a0 for X and b coefficients for Y.
* **Curvature**: A measure of how much a curve deviates from a straight line.
	+ Can be represented as an equation describing the curvature along the curve.
* **Polynomial Spiral (or Spiral)**: A type of parametric representation using a polynomial function to describe the curve's curvature.
	+ Example: Cubic spiral with Kappa (curvature) as a function of arc length s from 0 to total length s_f.

### Practical Notes
To implement parametric curves for path planning, you'll need to:

* Understand how to define and use parametric equations to represent curves in two-dimensional space.
* Familiarize yourself with splines and polynomial spirals, including their coefficients and curvature representations.
* Apply this knowledge to develop a parametric curve that accurately models the vehicle's path.

Note: This is just an introduction to parametric curves. The next section will delve deeper into splines and spiral representations.

## Transcript

In the introduction, we defined a path as the curve that the vehicle describes in a space. But the question is, how can we mathematically represent this curve? Well, we use parametric representations. In the next few slides, we will go deeper into what a parametric curve is and what type of parametric representations we are interested for the path planning problem. For simplicity and to get your intuition about parametric curves, we will start looking at them in two dimensions.

A parametric curve, C in R_2, the two-dimension space of real numbers is a set of equations, one for each dimension x of t and y of t that trace the curve C as the parameter t varies, usually from zero to one. This means that at t equals zero, we will get x and y at the beginning of the curve and at t equal one, we will get x and y at the end of the curve. When the equations that describe x and y are polynomials, we call this parametric curves splines. Here's an example of what a cubic spline representation looks like. In this case, the parameter is t and it could vary from zero to one.

The curves coordinate X and Y are defined by the coefficients of each equation, a3, a2, a1, and a0 for the X and the b coefficients for the Y. Sometimes instead of using equations that describe the position X and Y, we can use an equation that describes the curvature along the curve. In simple terms, curvature is the amount by which the curve deviates from this straight line. We will go in more detail in the next section. So don't worry about it for now.

This type of parametric representation of a curve is called spiral, or more precisely polynomial spiral. Here's an example of what this representation looks like. In this case, K, or the Greek letter Kappa is the curvature as a function of the arc length s from zero to the total length s_f. In this notation, s represents the longitudinal distance the vehicle has traveled along the path. Specifically, this is a cubic spiral, since we're using a third order polynomial.

In the next section, we will address in more detail splines and spiral.

## Additional Content

## Path

If you remember from previous sections a path is the curve that the vehicle describes in space. In order to mathematically represent the curve, we can use parametric representation. **Parametric representation** is one or more function of one or more independent parameters.

## Parametric Curve

**A parametric curve** “C” in R2 is a set of equations (one for each dimension)

$x=x(t)$

and

$y=y(t)$

that trace a curve C as the Parameter t varies, usually from 0 - 1. 

### Splines
**Splines** are parametric curves in which the equations that describe X and Y are polynomials. At

$t = 0$

, we will get X and Y at the *beginning* of the curve, and at

$t = 1$

, we will get X and Y at the *end* of the curve. 

#### Cubic spline example:

$X(t) = a_3t^3 + a_2t^2 + a_1t + a_0$

$Y(t) = b_3t^3 + b_2t^2 + b_1t + b_0$

### Spiral

A **spiral**, or a **polynomial spiral** is a parametric representation of a curve where instead of using equations that describe the position X and Y, we use an equation that describe the **“curvature”** along the curve.  

#### Cubic spiral example:

$\kappa(s) = a_3t^3 + a_2t^2 + a_1t + a_0$

$s=[0,s_f]$

This is a Cubic Spiral since the polynomial used is of order 3,

$\kappa$

is the curvature as a function of the arc length

$s$

. 


## Other Resources
https://en.wikipedia.org/wiki/Curvature
