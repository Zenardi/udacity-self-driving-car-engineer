# Kalman Filter Code

> Part of: **Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=3xBycKfnCOQ)

## Summary

**Kalman Filter Implementation**
=====================================

This README file provides a summary of the key concepts and practical steps involved in implementing a Kalman filter for 1D.

### Key Concepts

* **Recursive Formula**: The update function implements a recursive formula to calculate the new estimate (`mu`) and uncertainty (`sigma`) based on the previous values, measurement, and motion.
* **Measurement Update**: The measurement is used to update the estimate and uncertainty using the following equation: `mu = mu + K \* (z - H \* mu)`
* **Motion Update**: The prediction function uses a simple addition equation to predict the next position based on the current position and motion.
* **Uncertainty Calculation**: The uncertainty is calculated using the measurement and motion uncertainties, as well as the previous uncertainty.

### Practical Notes

* To implement the Kalman filter, you need to define two functions: `update` and `predict`. The `update` function takes in the measurement, motion, and current estimate and uncertainty, while the `predict` function takes in the current position and motion.
* You can use a recursive formula to update the estimate and uncertainty based on the previous values, measurement, and motion.
* In the example code provided, the author uses a constant measurement uncertainty of 4 and motion uncertainty of 2. You can adjust these values to see how they affect the final prediction.

**Example Code**
```python
def update(z, H, mu, sigma, R):
    K = sigma / (sigma + R)
    mu = mu + K * (z - H * mu)
    sigma = (1 - K) * sigma
    return mu, sigma

def predict(mu, motion):
    return mu + motion

# Example usage:
measurements = [5, 6, 7, 9, 10]
motions = [1, 1, 2, 1, 1]

mu, sigma = 0, 10000
for i in range(len(measurements)):
    mu, sigma = update(measurements[i], 1, mu, sigma, 4)
    mu = predict(mu, motions[i])
print("Final prediction:", mu)
```

## Transcript

So now let's put everything together. Let's write a main program that takes these 2 functions, update and predict, and feeds into a sequence of measurements and motions. In the example I've chosen here are the measurements of 5., 6., 7., 9., and 10. The motions are 1., 1., 2., 1., 1. This all would work out really well if the initial estimate was 5, but we're setting it to 0 with a very large uncertainty of 10,000. Let's assume the measurement uncertainty is constant 4, and the motion uncertainty is constant 2. When you run this, your first estimate for position should basically become 5-- 4.99, and the reason is your initial uncertainty is so large, the estimate is dominated by the first measurement. Your uncertainty shrinks to 3.99, which is slightly better than the measurement uncertainty. You then predict that you add 1, but the uncertainty increases to 5.99, which is the motion uncertainty of 2. You update again based on the measurement 6, you get your estimate of 5.99, which is almost 6. You move 1 again. You measure 7. You move 2. You measure 9. You move 1. You measure 10, and you move a final 1. And out comes as the final result, a prediction of 10.99 for the position, which is your 10 position moved by 1, and the uncertainty--residual uncertainty of 4. Can you implement this so you get the exactly same outputs as I've gotten over here?

This piece of code implements the entire Kalman filter.

It goes through all the measurement elements and quietly assumes there are as many measurements as motions indexed by n. It updates the mu and sigma using this recursive formula over here. If we plug in the nth measurement and the measurement uncertainty, it does the same with the motion, the prediction part over here. It updates the mu and sigma recursively using the nth motion and the motion uncertainty, and it prints all of those out. If I hit the Run button, I find that my first measurement update gets me effectively 5.0.

It's 4.98. And that makes sense because we had a huge initial uncertainty, and [inaudible] of 5 with a relatively small measurement uncertainty. And in fact the resulting sigma square term is 3.98, which is better than 4 and 1,000, slightly better than 4. We're slightly more certain than the measurement itself. We now apply the motion of 1.

We get to 5.9. Our uncertainty increases by exactly 2, from 3.9 to 5.98. And then the next update comes in at 6, and it gives us a measurement of 5.99 and now a reduced uncertainty of 2.39. And then we go to move to the right again by 1, which makes the prediction 6.99. Uncertainty goes up.

We measure 7. We get to 6.99, almost 7. Uncertainty goes down. We move 2 to the right, measure 9, 1 to the right, measure 10, and move 1 again. The final thing is the motion.

And if you look at the end result, our estimate is almost exactly 11, which is the result of 10 + 1. And the uncertainty is 4.0 after the motion and 2.0 after the measurement. This code that you just wrote implements a full Kalman filter for 1D. If you look at this, we have an update function that implements what actually is a relatively simple equation, and a prediction function which is an even simpler equation of just addition. And then you apply it to a measurement sequence and a motion sequence with certain uncertainties associated, and this little piece of code over here gives you a full Kalman filter in 1D.

I find this really amazing. Let's plug in some other values. Suppose you're really certain about the initial position. It's wrong. It's 0.

It should be 5, but it's 0. And now we assume a really small uncertainty. Guess what's going to happen to the final prediction? As I hit the Run button, we find this has an effect on the final estimate. It's not 11.

It's only 10.5. And the way this takes place is initially, after our first measurement update, we believe in the position of 0. This is 1.24 to the - 10th, but a really small uncertainty, even smaller than this one over here. We apply our motion update. We add a 1.

We have a higher uncertainty. And now when the next measurement comes in, 6, we are now more inclined to believe the measurement because uncertainty is now basically 2 as opposed to 0.001. We update our position to be 2.666, which is now a jump away from 1, and we reduce our uncertainty. Motion comes in, 3.66. Uncertainty goes up.

We now are willing to update even more. As you see the 7, we're willing to go to 5.1, but not quite all the way because we feel fairly confident on our wrong prior estimate. And this confidence makes it all the way to the end when we predict 10.5 as opposed to 11 with an uncertainty of 3.98. We've corrected some of it. We were able to drag it into the right direction but not all the way because our false initial belief has such a strong weight in the overall equation.

### Solution

[Watch on YouTube](https://www.youtube.com/watch?v=X7cixvcogl8)

