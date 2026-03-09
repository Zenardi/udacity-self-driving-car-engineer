# Additional Cost Considerations

> Part of: **Model Predictive Control**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=lsdZtPPOhtk)

## Summary

**Summary of Cost Function Extensions**

This summary covers the extension of the cost function to include both state and control input variables. This allows for more nuanced optimization, including penalizing not only the magnitude of the control input but also its change rate.

### Key Concepts

* **Cost function extensions**: The cost function can be extended to include control input variables in addition to state variables.
* **Penalizing control input magnitude**: Including the magnitude of the control input in the cost function allows for penalization of sharp turns or other high-magnitude control actions.
* **Temporal smoothness**: Capturing the change rate of the control input adds temporal smoothness to the optimization process.
* **Change rate calculation**: The difference between the next control input state and the current one is used to calculate the change rate.

### Practical Notes

To extend the cost function, you can add the magnitude of the control input as follows:

```python
cost_function = ... + magnitude_penalty * |u|
```

Where `|u|` represents the magnitude of the control input `u`. Additionally, you need to capture the change rate of the control input by calculating the difference between the next and current control states. This can be done using a term like:

```python
change_rate_penalty = penalty * (next_u - u)
```

This additional term helps to add temporal smoothness to the optimization process.

## Transcript

<v English>The cost function is not limited to the state.</v> <v English>We could also include the control input.</v> <v English>The reason we would do this is to allow us to</v> <v English>penalize the magnitude of the input as well as the change rate.</v> <v English>If we want to change lanes, for example,</v> <v English>we would have a large cross-tracker that would</v> <v English>want to penalize turning the wheel really sharply.</v> <v English>This would yield a smoother lane change.</v> <v English>We could add the control input magnitude like this.</v> <v English>We still need to capture the change rate of</v> <v English>the control input to add some temporal smoothness.</v> <v English>This additional term in the cost function captures the difference between</v> <v English>the next control input state and</v> <v English>the current one so we have further control over the inputs.</v>

## Additional Content

## Code Snippets

```cpp
for (int t = 0; t < N-1; ++t) {
  cost += pow(delta[t], 2);
}
```


```cpp
for (int t = 0; t < N-1; ++t) {
  cost += pow(delta[t+1] - delta[t], 2);
  cost += pow(a[t+1] - a[t], 2);
}
```
