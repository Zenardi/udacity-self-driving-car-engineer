# Sigma Point Prediction

> Part of: **Unscented Kalman Filters**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=zeMy0dth3yI)

## Summary

**Sigma Point Prediction**
==========================

This project involves predicting sigma points using a process model. The goal is to implement the prediction step in C++ code.

### Key Concepts

* **Augmented Sigma Points**: A matrix of predicted sigma points, where each column represents a single sigma point.
* **Process Model**: A mathematical model that takes an input vector (a 7-dimensional augmented vector) and returns a predicted state vector (a 5-dimensional vector).
* **Sigma Point Prediction**: The process of inserting every sigma point into the process model to generate predicted values.

### Practical Notes

To implement the prediction step in C++:

1. Define the process model as a function that takes a 7-dimensional augmented vector as input and returns a 5-dimensional predicted state vector.
2. Create a matrix `calligraphic Xk+1|k` to store every predicted sigma point as a column.
3. Ensure the input to the process model is a 7-dimensional augmented vector, which includes five state dimensions and two noise dimensions.
4. The output of the process model should be a 5-dimensional vector.

**Example Code**
```cpp
// Define the process model function
vector<double> processModel(const vector<double>& input) {
    // Implement your process model here
}

// Create a matrix to store predicted sigma points
int numSigmaPoints = 15;
matrixXd calligraphicXkPlus1K(numRows, numSigmaPoints);

// Predict sigma points using the process model
for (int i = 0; i < numSigmaPoints; ++i) {
    vector<double> input = augmentedVector(i); // Get the ith augmented vector
    vector<double> predictedState = processModel(input);
    calligraphicXkPlus1K.col(i) = predictedState;
}
```

## Transcript

<v English>You have now successfully mastered</v>
<v English>the generation of Sigma Points,</v> <v English>and even implemented an example in C++.</v> <v English>Really great job, and you know what?</v> <v English>This was the most difficult and</v> <v English>complicated part, all the remaining</v>
<v English>steps will be much simpler.</v> <v English>Let's move on the prediction</v>
<v English>of Sigma Points.</v> <v English>What we have now is this matrix</v>
<v English>of augmented Sigma Points.</v> <v English>For the prediction step,</v> <v English>we simply insert every Sigma Point</v>
<v English>into the process model.</v> <v English>Again, we store every predicted</v>
<v English>Sigma Point as a column of a matrix,</v> <v English>we call this matrix calligraphic Xk+1|k.</v> <v English>When you will bring this to C++ code,</v> <v English>the main thing you have to do</v>
<v English>is implement this process model.</v> <v English>One thing you should also consider,</v>
<v English>the input to the process model</v> <v English>is a seven dimensional Augmented vector,</v>
<v English>which makes sense.</v> <v English>These are five state dimensions and</v>
<v English>two noise dimensions.</v> <v English>The output is a five dimensional vector,</v> <v English>because this is what the process</v>
<v English>model returns, that means</v> <v English>the matrix with the predicted Sigma</v>
<v English>Points has five rows and 15 columns.</v> <v English>All right,</v> <v English>that's everything you need to know</v>
<v English>about the prediction of Sigma Points.</v> <v English>Let's see if you can</v>
<v English>implement this in C++.</v>
