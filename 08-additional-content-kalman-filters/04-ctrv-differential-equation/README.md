# CTRV Differential Equation

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=o2HVZFSH1Fs)

## Summary

**README: Deriving Process Models from Circular Motion**

This project explores how to derive a process model from the assumption of circular motion. The goal is to predict the state of an object at time step k + 1, given its state at time step k and a noise vector.

### Key Concepts

* **Process Model**: A mathematical function that predicts the state of an object at time step k + 1, given its state at time step k and a noise vector.
* **Differential Equation**: An equation that describes how the change rate of a state variable depends on the state itself.
* **Change Rate (x dot)**: The rate at which the state x changes over time.
* **Geometric Relations**: Mathematical relationships between the state variables, used to derive the differential equation.

### Practical Notes

To apply this concept in practice:

1. Identify the state variables and their dependencies using geometric relations.
2. Derive a differential equation that describes how each change rate depends on the state variables.
3. Use the derived process model to predict the state of an object at time step k + 1, given its state at time step k and a noise vector.

Example: Given a circular motion scenario with state variables x (position), V (speed), psi (orientation), and Px (velocity in x direction), derive the differential equation for each change rate:

* `Px dot = Vx`
* `Vx = cos(psi) * V`
* `Vy = sin(psi) * V` (derived similarly to `Vx`)
* `dpsi/dt = omega` (angular velocity, derived from geometric relations)

Note: This is a simplified example and actual implementation may require more complex mathematical derivations.

## Transcript

<v English>Now, let's take a look at how</v>
<v English>the assumption of a circular motion</v> <v English>leads to a process model.</v> <v English>So in this example,</v>
<v English>at time k, the car's here.</v> <v English>The goal of the process model f is to</v>
<v English>predict where the car is at time k + 1.</v> <v English>Written as an equation,</v>
<v English>it looks like this.</v> <v English>The process model f predicts</v>
<v English>the state at time step k + 1.</v> <v English>Given the state at time step k and</v> <v English>a noise vector new k,</v>
<v English>this is the function we want to find.</v> <v English>What we want to do now is</v>
<v English>derive this process model.</v> <v English>I will show you a very general and,</v>
<v English>therefore, powerful approach.</v> <v English>You will be able to use this approach</v>
<v English>to derive process models for</v> <v English>many, many real world problems.</v> <v English>We cannot directly write down the</v>
<v English>process model simply by looking at this</v> <v English>figure.</v> <v English>But we can say something about</v>
<v English>the change rate of the state x,</v> <v English>called x dot.</v> <v English>>From the geometric relations,</v> <v English>we can directly derive how the change</v>
<v English>rate x dot depends on the state x.</v> <v English>This is a differential equation.</v> <v English>What I would like you to do now is</v>
<v English>derive this differential equation.</v> <v English>The goal is to express each of</v>
<v English>the five-time relatives of the state,</v> <v English>independency of any of</v>
<v English>the state elements.</v> <v English>I'll show you an example, Px dot is</v>
<v English>the same as the velocity in x direction.</v> <v English>Unfortunately, the velocity</v>
<v English>in x direction</v> <v English>is not part of the state vector,</v>
<v English>otherwise, I would be finished already.</v> <v English>But the speed V and the origin of psi</v>
<v English>are both elements of the state vector.</v> <v English>And if I look at this triangle,</v> <v English>I can identify that Vx</v>
<v English>= cosine psi times V.</v> <v English>Now, go ahead and</v>
<v English>pick the correct terms for</v> <v English>the four remaining change</v>
<v English>rates of the state.</v>

## Images

![The CTRV model.](images/screenshot-from-2017-02-27-20-45-49.png)
*The CTRV model.*

## Additional Content

In the following quizzes, you'll need to pick the correct terms for the change rates of the state using the diagram above and some calculus! We started with:

$$\dot{p_x} = cos(\psi) \cdot v$$

Now, pick the correct terms for

$\dot{p_y}$

,

$\dot{v}$

,

$\dot{\psi}$

and

$\ddot{\psi}$

.
### Question 1:

$\dot{p_y}$

= ???

A.

$sin(\psi) \cdot v$

B.

$cos(\psi) \cdot v$

C.

$tan(\psi) \cdot v$

### Question 2:

$\dot{v}$

= ???

A.

$0$

B.

$v$

C.

$\psi$

### Question 3:

$\dot{\psi}$

= ???

A.

$0$

B.

$\dot{\psi}$

C.

$\psi$

### Question 4:

$\ddot{\psi}$

= ???

A.

$0$

B.

$v$

C.

$\psi$
