# Glossary

> Part of: **Kalman Filters**

## Additional Content

## Glossary

**Gaussian:** A continuous function over a space of locations where the area underneath sums up to 1, giving the probability of being in a given location (based on a mean, $\mu$ , and variance, $\sigma^2$). Gaussians have unimodal distributions (i.e. one "peak").

**Kalman Filter:** A tracking method that uses gaussians with a predict and update cycle (with measurements and motion) to estimate location.
### Gaussian Equations

#### Gaussian Equation

$\Large f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} \times \exp^{-1/2 \frac{(x - \mu)^2}{\sigma^2}}$

The mean is represented by $\mu$ ("mu") while the variance is represented by $\sigma^2$ ("sigma squared").

#### Measurement Update

$\Large \mu^\prime = \frac{1}{\sigma^2 + r^2} \times (r^2 \times \mu + \sigma^2 \times \nu)$

$\Large \sigma^{2\prime} = \frac{1}{\frac{1}{\sigma^2} + \frac{1}{r^2}}$

Where $\mu^\prime$ ("mu prime") is the new mean, $\sigma^{2\prime}$ ("sigma squared prime") is the new variance, $r^2$ ("r squared") is the measurement variance, and $\nu$ ("nu") is the measurement mean ( $\mu$ and $\sigma^2$ are the mean and variance of the prior, respectively).

#### Motion Update

$\Large \mu^\prime = \mu + u$

$\Large \sigma^{2\prime} = \sigma^2 + r^2$

Where $u$ ("u") is the motion, and $r^2$ ("r squared") in this case is the variance of the motion (and $\mu^\prime$ and $\sigma^{2\prime}$ are the mean and variance after motion, respectively).

### Kalman Filter Definitions and Equations

#### Definitions

- $\large x$ = estimate
- $\large P$ = uncertainty covariance
- $\large F$ = state transition matrix 
- $\large u$ = motion vector 
- $\large z$ = measurement 
- $\large H$ = measurement function 
- $\large R$ = measurement noise 
- $\large I$ = identity matrix

#### Prediction Equations

$\large x^\prime = Fx+u$

$\large P^\prime = F \cdot P \cdot F^T$

#### Measurement Equations

$\large y = z - H \cdot x$

$\large S = H \cdot P \cdot H^T + R$

$\large K = P \cdot H^T \cdot S^{-1}$

$\large x^\prime = x + (K \cdot y)$

$\large P^\prime = (I - K \cdot H) \cdot P$
