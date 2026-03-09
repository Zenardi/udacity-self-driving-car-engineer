# Bayes' Rule

> Part of: **Markov Localization**

## Additional Content

Before we dive into deeper into Markov localization, we should review Bayes' Rule.  This will serve as a refresher for those familiar with Bayesian methods and we provide some additional resources for those less familiar.  

  Recall that Bayes' Rule enables us to determine the conditional probability of a state given evidence P(a|b) by relating it to the conditional probability of the evidence given the state P(b|a) in the form of:

$$P(a)*P(b|a) = P(b)*P(a|b)$$

which can be rearranged to:

$$P(a|b) = \frac{P(b|a) \, P(a)}{P(b)}$$

In other words the probability of state a, given evidence b, is the probability of evidence b, given state a, multiplied by the probability of state a, normalized by the total probability of b over all states.  

Let's move on to an example to illustrate the utility of Bayes' Rule.
## Bayes' Rule Applied

Let's say we have two bags of marbles, bag 1 and bag 2, filled with two types of marbles, red and blue.  Bag 1 contains 10 blue marbles and 30 red marbles, whereas bag 2 contains 20 of each color marble.  

If a friend were to choose a bag at random and then a marble at random, from that bag, how can we determine the probability that that marble came from a specific bag?  You guessed it - Bayes' Rule! 

In this scenario, our friend produces a red marble, in that case, what is the probability that the marble came from bag 1?  Rewriting this in terms of Bayes' Rule, our solution becomes:

$$P(Bag1 | Red) = \frac{P(Red | Bag1) \, P(Bag1)}{P(Red)}$$

Let's walk through the process in the following quizzes.
## Bayesian Methods Resources

- [Sebastian Discusses Bayes Rule](https://www.youtube.com/watch?v=sA5wv56qYc0)
- [More Bayes Rule Content from Udacity](https://classroom.udacity.com/courses/st101/lessons/48703346/concepts/483698470923)
- [Bayes Rule with Ratios](https://betterexplained.com/articles/understanding-bayes-theorem-with-ratios)
- [A Deep Dive into Bayesian Methods, for Programmers](http://greenteapress.com/wp/think-bayes/)
