# Story Time

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=gFdT8W1fmf8)

## Summary

**Unscented Kalman Filter: A Better Alternative to the Extended Kalman Filter**

The unscented Kalman filter is a type of recursive estimation algorithm used in signal processing and control systems. In this lesson, we explore why it's called "unscented" and how it differs from its predecessor, the extended Kalman filter.

**Key Concepts:**

* **Extended Kalman Filter**: A linearization-based approach to estimating system states, which can be limited by its reliance on a single operating point.
* **Linearization**: The process of approximating a nonlinear function using a linear one, which can lead to inaccuracies if not done properly.
* **Jacobian Matrix**: A mathematical representation of the partial derivatives of a function with respect to its inputs, often used in linearization.
* **Unscented Kalman Filter**: A method that uses a deterministic sampling approach to capture the true distribution of the system states, rather than relying on linearization.

**Practical Notes:**

The unscented Kalman filter is particularly useful when dealing with nonlinear systems or when the system dynamics are not well-represented by a single operating point. By avoiding the need for Jacobian matrices and linearization, the unscented Kalman filter can provide more accurate estimates of system states.

Note that this lesson does not provide any code examples or practical steps to implement the unscented Kalman filter. However, understanding its underlying principles and advantages over traditional methods can help you choose the right approach for your specific application.

## Transcript

<v English>Today, we're here with Sebastian,</v> <v English>because there's one important thing about</v> <v English>the unscented Kalman filter we haven't explained yet.</v> <v English>Sebastian, could you tell us why the unscented Kalman filter is called unscented.</v> <v English>Okay. So, I'm Sebastian,</v> <v English>I'm lived long time,</v> <v English>old enough to witness these early stories.</v> <v English>A long time ago, two grad students,</v> <v English>which invented the unscented filter,</v> <v English>called unscented because they felt that the extended Kalman filter stinks,</v> <v English>and they felt it stinks because they were deeply</v> <v English>dissatisfied by linear rising among this one operating point.</v> <v English>And further, if you sample this,</v> <v English>then you would get a much better estimate of what the better linearization look like.</v> <v English>The fact that the adviser, turns out,</v> <v English>was a very religious person,</v> <v English>believing in the extent of Kalman filter,</v> <v English>and there was a bit of a fight going on and</v> <v English>the students that personally practice on their own without</v> <v English>the fairy adviser called it specifically unscented to</v> <v English>make this point loud and clear to the entire world that the old stuff,</v> <v English>the extended Kalman filter stinks.</v> <v English>That's a nice story.</v> <v English>Yeah. Now, we know why linearization stinks.</v> <v English>And I hate Jacobians,</v> <v English>let this be on record, I don't like Jacobians.</v> <v English>I think we can all agree.</v>
