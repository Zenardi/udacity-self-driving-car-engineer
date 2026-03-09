# Twiddle

> Part of: **PID Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=2uQ2BSzDvXs)

## Summary

**Twiddle Algorithm for Optimizing Parameters**
=====================================================

This README file provides an overview of the Twiddle algorithm, a method for optimizing parameters by minimizing the average crosstrack error.

### Key Concepts

* **Goodness value**: A measure of how well a set of parameters performs, represented as a numerical value.
* **Parameter vector**: A collection of parameters to be optimized, initialized with zeros.
* **Probing values**: Potential changes to be applied to each parameter, initially set to 1.
* **Best error**: The minimum goodness value achieved so far, used to compare with new errors.
* **DP (probing interval)**: A factor by which the probing interval is increased or decreased based on performance.

### Practical Notes

To implement Twiddle:

1. Initialize a parameter vector `p` and a probing values vector `dp`.
2. Set the best error `best_err` to a large value and initialize the DP to 1.
3. Run the `run()` function with the current parameters, updating the best error if necessary.
4. For each parameter in isolation:
	* Increase the parameter by the probing value and compute a new error.
	* If the new error is better, retain it and increase the DP by multiplying it with 1.1.
	* Otherwise, decrease the parameter by the probing value and repeat the process.
5. If both attempts fail, reset the parameter to its original value and decrease the DP by multiplying it with 0.9.
6. Repeat steps 4-5 until the sum of DPs is less than a threshold (e.g., 0.00001).

Note that Twiddle is an efficient local hill climber algorithm, capable of converging on optimal parameters in a few iterations.

## Transcript

In Twiddle, we're trying to optimize for a set of parameters. To do so, our function run() must return a goodness. This goodness value might be the average crosstrack error. Say I wanted to implement Twiddle so as to minimize the average crosstrack error. If that's the case, then the output of run depends on the three parameters.

Here's how Twiddle works. Build a parameter vector of our 3-target parameters, and initialize it with zero. Also, build a vector of potential changes that you want to probe and initialize them for now with 1. Then you can run our command run( ) with our parameters, and whatever it outputs is our best error so far. Now we wish to modify p as to make the error smaller.

That's where Twiddle comes in. It's a really smart algorithm, I believe. We sequentially go through these parameters. Obviously, you shouldn't write 3. You should write len of p.

First we tried to increase p by our probing value, compute a new error for this new modified p. If this new error is better than our best error, then we do two things. First, we set best_err to err, and we even modify our dp to a slightly larger value by multiplying it with 1.1. Otherwise, we try the other way. We subtract dp from p--and we have to do it twice now because we added it before.

Then we do the same thing again as over here. I'm not going to write it out. We check whether the error is better than our best error, we retain it, and we multiply dp by 1.1. But if both of those fail--this one over here and this one over here-- we set p[ i ] back to the original value, and we decrease our probing thing over here, say, by multiplying it with 0.9. That's the core of Twiddle, and what it really does is for each coordinate in isolation it moves our parameter down a little bit by this value over here.

If it then finds a better solution, it retains it, and it even increments the probing interval. If it fails to find a better solution, it goes back to the original and decreases our probing interval. We do this entire thing so long as the sum of the dp's is larger than the threshold. Somewhere in here we say while some of dp is larger than 0.00001. It's hard to read, but I hope you can follow it.

This is Twiddle. Let me put this into pictures. We have three parameters--0, 0, 0. Then in the first iteration, we bump one of the parameters up and see if it improves the error. If that's the case, we retain it.

Then we go to the second parameter. We bump it up. It might not work. We bump it down and maybe retain that one, and so on. Now, as we keep bumping up, we might find that neither bumping up nor bumping down helps.

What we do instead is we retain the original solution but make our probing interval smaller than before by a factor of 0.9. In doing so, we can zoom in more and more into a detailed parameter until it finally converges. It's local hill climber, but it happens to be really, really efficient.

## Additional Content

## Understanding the Twiddle Algorithm

In this lecture, we talk about an algorithm called **Twiddle**, and the easiest way to think about it is this: Twiddle is a method for *systematically guessing better parameters* when you don’t know the right answer upfront.

Throughout the lecture, we assume we have a function written as `run(p)`.  This function takes a parameter vector `p` and returns a single number that tells us how good or bad those parameters are. Usually, this number is an error value — for example, an average cross-track error. Our goal is simple: **make that error as small as possible**.

### Starting from Zero

We begin with a parameter vector written on the board as:
```python
p = [0, 0, 0]
```
These are the parameters we want to tune. Starting from zero doesn’t mean zero is good — it just means we don’t know anything yet. Next, we define another vector:
```python
dp = [1, 1, 1]
```
This vector controls *how much* we are willing to change each parameter. You can think of `dp` as the size of our experimental steps. At the beginning, the steps are fairly large because we want to explore the space quickly. We then evaluate our starting point by calling:
```python
best_err = run(p)
```

This value becomes our reference point — the best error we’ve seen so far.

### When Do We Stop?

Twiddle doesn’t run forever. The lecture uses a stopping condition based on the step sizes:
```python
while sum(dp) > threshold
```

As long as the total amount we are willing to adjust the parameters is still significant, we keep going. Once all step sizes become very small, we stop. This is how Twiddle gradually shifts from coarse exploration to fine tuning.

### One Parameter at a Time

The key idea of Twiddle is that we don’t change everything at once. Instead, we focus on **one parameter at a time**, written in the lecture as:
```python
for i in range(len(p))
```

For each parameter, we try the same sequence of experiments.

### First Try: Increase the Parameter

We start by nudging the parameter upward:
```python
p[i] = p[i] + dp[i]
```

Then we evaluate the result by calling `run(p)` again. If the new error is **smaller than** `best_err`, that’s great news. It means this direction helped. So we:

- Accept the new parameter value  
- Update `best_err`  
- Increase the step size using `dp[i] *= 1.1`

This increase reflects growing confidence that moving in this direction is useful.

### Second Try: Go the Other Way

If increasing the parameter didn’t help, we try the opposite direction. Since we already moved up once, we now move down by twice the step size:
```python
p[i] = p[i] - 2 * dp[i]
```

Again, we compute the error. If the error improves this time, we keep the new value, update `best_err`, and once again increase `dp[i]` by multiplying it by **1.1**.

### When Neither Direction Works

Sometimes, neither increasing nor decreasing the parameter helps. When that happens, Twiddle makes a very important decision. We restore the parameter to its original value and shrink the step size:
```python
dp[i] *= 0.9
```

This tells us, "We’re probably close to the best value already — let’s search more carefully." This is the moment where Twiddle *zooms in*.

### What’s Really Happening Under the Hood

As this process repeats, Twiddle is constantly adjusting two things:

- The **parameters** `p`
- The **step sizes** `dp`

When progress is easy, step sizes grow. When progress is hard, step sizes shrink.

Over time, `dp` **becomes smaller and smaller**, and the parameter values settle into a stable solution. This is why Twiddle is often described as a **very efficient local hill-climbing algorithm**. It doesn’t use gradients, derivatives, or advanced math — just careful experimentation guided by feedback from `run(p)`.

### Big Picture Takeaway

Twiddle works because it follows a simple loop:

- Change one parameter  
- Measure the error  
- Keep what works  
- Undo what doesn’t  
- Adjust how boldly you explore next time  

Despite its simplicity, this approach is surprisingly powerful, especially in problems like controller tuning where gradients are difficult or impossible to compute. Once you see Twiddle this way, the algorithm becomes much less mysterious — it’s really just **smart, adaptive trial and error**.
