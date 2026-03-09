# Motion Model Probabiity I

> Part of: **Markov Localization**

## Additional Content

Now we will practice implementing the motion model to determine P(location) for our Bayesian filter.   We discussed the derivation of the model in **Recursive Structure
** and **Implementation Details for Motion Model**.

Recall that we derived the following recursive structure for the motion model:

$$\int p(x_t|x_{t-1}, u_t, m)bel(x_{t-1})dx_{t-1}$$

and that we will implement this in the discretized form:

$$\sum\limits_{i} p(x_t|x_{t-1}^{(i)}, u_t, m)bel(x_{t-1}^{(i)})$$

Let's consider again what the summation above is doing - calculating the probability that the vehicle is now at a given location,

$x_t$

.

How is the summation doing that? It's looking at each prior location where the vehicle could have been,

$x_{t-1}$

. Then the summation iterates over every possible prior location,

$x_{t-1}^{(1)}...x_{t-1}^{(n)}$

. For each possible prior location in that list,

$x_{t-1}^{(i)}$

, the summation yields the **total probability** that the vehicle really did start at that prior location __and__ that it wound up at

$x_t$

.

That now raises the question, how do we calculate the individual probability that the vehicle really did start at that prior location __and__ that it wound up at

$x_t$

, for each possible starting position

$x_{t-1}$

?

That's where each individual element of the summation contributes. The likelihood of starting at

$x_{t-1}$

and arriving at

$x_{t}$

is simply

$p(x_t|x_{t-1}) * p(x_{t-1})$

.

We can say the same thing, using different notation and incorporating all of our knowledge about the world, by writing:

$p(x_t|x_{t-1}^{(i)}, u_t, m) * bel(x_{t-1}^{(i)})$

From the equation above we can see that our final position probability is the sum of n discretized motion model calculations, where each calculation is the product of the 'i'th transition probability,

$p(x_t|x_{t-1}^{(i)}, u_t, m)$

,
 and 'i'th belief state,

$bel(x_{t-1}^{(i)})$

.  Let's try out a single, discreet calculation.  

'**i**'**th Motion Model Probability:**

$$p(x_t|x_{t-1}^{(i)}, u_t, m) * bel(x_{t-1}^{(i)})$$

**2.22E-2** - remember to enter two decimal places!

Show Solution

In the next concept, we will practice determining other values relevant to the motion model.
