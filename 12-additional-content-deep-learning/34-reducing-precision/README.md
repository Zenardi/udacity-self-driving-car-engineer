# Reducing Precision

> Part of: **Inference Performance**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=bZPG5I_igR8)

## Summary

**Summary of Neural Network Precision and Quantization**

Neural networks are typically trained using single precision, 32-bit floating point numbers. However, research has shown that lower precision can be used for certain tasks, such as inferencing, with minimal impact on accuracy.

### Key Concepts

* **Single precision**: 32-bit floating point number with 23-bit significand, suitable for most neural network training.
* **Double precision**: 64-bit floats with 52 significant digits, not needed for neural nets due to high computational cost.
* **Half precision**: 16-bit floating point numbers with 11 significant bits, used for inferencing and achieving minimal changes in accuracy while reducing time and memory usage.
* **Quantization**: the process of constraining continuous values to a discrete range, introduced by converting floating point values to integer representations.

### Practical Notes

When training neural networks using lower precision, the main issue is the effect on back propagation. The error caused by lower precision is amplified at each stage of the backward pass through the network. However, this is only an issue during training, and for inferencing, reducing precision can be done without significant impact on accuracy.

To achieve quantization, floating point values are converted to a 256-unique-value integer representation, such as zero two two 55. This process introduces another type of optimization by constraining continuous values to a discrete range.

**Example Code**
```python
import numpy as np

# Convert floating point value to half precision (16-bit)
fp_value = 3.14
half_precision_value = np.float16(fp_value)

# Quantize floating point value to integer representation
quantized_value = int(np.round(fp_value) * 256)
```
Note: This code is for illustration purposes only and may not be directly applicable to your specific use case.

## Transcript

<v English>Neural networks are typically trained with single precision,</v> <v English>32-bit floating point number.</v> <v English>It has 23-bit significand,</v> <v English>that can do significant digits used in science disciplines.</v> <v English>Double precision or 64-bit floats have</v> <v English>52 significant digits but turns out that level of precision is not needed in neural nets.</v> <v English>So, most training is done in single precision.</v> <v English>But it turns out we don't even need single precision for all the task,</v> <v English>especially something like inferencing.</v> <v English>Using half precision or 16-bits with 11 significant at even lower positions,</v> <v English>results in minimal changes in accuracy.</v> <v English>But does produce savings in time and memory.</v> <v English>Essentially, you can increase the bandwidth to double with 16-bits compared to 32-bits.</v> <v English>Pushing precision to the limit,</v> <v English>is an active area of research.</v> <v English>In fact, some results have been published only using one bit weights.</v> <v English>The main issue when training neural network using</v> <v English>lower precision is the effect on back propagation.</v> <v English>The error caused by lower precision is amplified at</v> <v English>each stage of the backward pass through the whole network.</v> <v English>Backward passes only happen during training though.</v> <v English>So, for inferencing this is a non issue and we can happily reduce precision.</v> <v English>Typically, we convert floating point values to</v> <v English>an a bit integer representation for 256 unique values.</v> <v English>For example, zero two two 55.</v> <v English>This specific reduction in precision from floating points to</v> <v English>integers introduces another type of optimization.</v> <v English>The process of constraining values like this from a continuous range to a discrete range,</v> <v English>is known as quantization.</v>

## Additional Content

[Bandwidth](https://en.wikipedia.org/wiki/Bandwidth_computing) is  the rate of data transfer, bit rate, or throughput, typically measured in bits per second.
