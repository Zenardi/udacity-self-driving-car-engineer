# Quantization Conversion

> Part of: **Inference Performance**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=0kbFQerI86k)

## Summary

**Converting Floating Point Values to Integers**
=============================================

This summary covers the basics of converting floating point values to integers, specifically focusing on linear conversion and its applications.

### Key Concepts
* **Linear Conversion**: A simple method for converting floating point values to integers by assigning fixed ranges to specific integer values.
* **Weight Range**: Neural network weights typically fall within a relatively small range, making them suitable for linear conversion.
* **Mapping Values**: Assigning specific integer values to corresponding ranges of floating point numbers (e.g., -8 to 0, 1 to 128, and 10 to 255).

### Practical Notes
To perform a linear conversion:

```python
# Example mapping function
def map_value(value):
    if value < -8:
        return 0
    elif value > 10:
        return 255
    else:
        # Calculate the corresponding integer value based on the range
        # For example, if weights range from -8 to 10 and we want to assign
        # values between 1 and 128, we can use a linear scale:
        scaled_value = (value + 8) / 18 * 127 + 1
        return int(scaled_value)
```

By applying this linear conversion technique, you can save significant processing power (up to 75% in some cases). Additionally, converting back to floating point numbers is straightforward.

## Transcript

<v English>There are a variety of ways to convert our floating point values to integers.</v> <v English>The simplest is a linear conversion.</v> <v English>A convenient characteristics of</v> <v English>neural network weights is they inhibit a relatively small range.</v> <v English>For example, in that layer,</v> <v English>weights might range from -8 to 10.</v> <v English>To perform a linear conversion we would assign -8 to 0,</v> <v English>1 to 128 and 10 to 255,</v> <v English>and all the values in between accordingly.</v> <v English>Notice it's easy to convert back to a floating point number if need be as well.</v> <v English>With just this small change,</v> <v English>we save 75% in this pace.</v>
