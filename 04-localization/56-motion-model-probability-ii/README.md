# Motion Model Probability II

> Part of: **Markov Localization**

## Additional Content

| pseudo_position (x) | pre-pseudo_position | delta position | P(transition) |

$bel(x_{t-1})$

| P(position) |
|:------------:|:---------------:|:--------------:|:-------------:|:--------:|:-----------:|
|       7      |        1        |        6       |    1.49E-06   | 5.56E-02 |   8.27E-08  |
|       7      |        2        |        5       |    1.34E-04   | 5.56E-02 |   7.44E-06  |
|       7      |        3        |        4       |    4.43E-03   | 5.56E-02 |   2.46E-04  |
|       7      |        4        |        ?       |    5.40E-02   | 0.00E+00 |   0.00E+00  |
|       7      |        5        |        2       |    ?   | 0.00E+00 |   0.00E+00  |
|       7      |        6        |        1       |    3.99E-01   | 0.00E+00 |   0.00E+00  |
|       7      |        7        |        0       |    2.42E-01   | ? |   1.66E-03  |
|       7      |        8        |       -1       |    5.40E-02   | 1.79E-03 |   ?  |

pseudo_position - pre-pseudo_position = **7 - 4 = 3**

Show Solution

```
#include

#include "help_functions.h"

//Assign 2 to the value term
//This is 7 - 5 = 2
float value = 2;

float parameter = 1.0; //set as control parameter or observation measurement
float stdev = 1.0; //position or observation standard deviation

int main() {

    float prob = Helpers::normpdf(value, parameter, stdev);

    std::cout << prob << endl;

    return 0;
}
```

Show Solution

Our positon probability is the product of the transition probability and our belief state at t - 1.  Rearranging yields:

**1.66E-03/2.42E-01 = 6.86E-03**

Show Solution

Our positon probability is the product of the transition probability and our belief state for our pre-pseudo position.

**5.40E-02 * 1.79E-03 = 9.66E-05**

Show Solution

We have completed our table of discretized calculation for each

$i$

th positon probability value. To determine the final probability returned by the motion model, we must sum the probabilities.

By summing the discrete probabilities from the table, we obtain the total probability, which estimates the probability from a continuous function.

8.27E-08 + 7.44E-06 + 2.46E-04 + 0.00E+00 + 0.00E+00 + 0.00E+00 + 1.66E-03 + 9.66E-05 = 2.02E-03

Show Solution

Recall that the transition probability can be determined through ```norm_pdf(delta_position, control_parameter, position_stdev)```
In the next concept we will implement the motion model in C++.
## Reference Equations


- **Discretized Motion Model:**

$$\sum\limits_{i} p(x_t|x_{t-1}^{(i)}, u_t, m)bel(x_{t-1}^{(i)})$$

- **Transition Model:**

$$p(x_t|x_{t-1}^{(i)}, u_t, m)$$

- '**i**'**th Motion Model Probability:**

$$p(x_t|x_{t-1}^{(i)}  u_t, m) *bel(x_{t-1}^{(i)})$$
