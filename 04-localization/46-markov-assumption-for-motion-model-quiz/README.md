# Markov Assumption for Motion Model: Quiz

> Part of: **Markov Localization**

## Additional Content

### Markov Assumption for Motion Model Quiz
What do you think about these two assumptions:

(a) Since we (hypothetically) know in which state the system is at time step t-1, the past observations $z_{1:t-1}$ and controls $u_{1:t-1}$ would not provide us additional information to estimate the posterior for $x_t$ , because they were already used to estimate $x_{t-1}$ . This means, we can simplify $p(x_t|x_{t-1}, z_{1:t-1}, u_{1:t},m)$ to $p(x_t|x_{t-1}, u_t, m)$ . 

(b) Since $u_t$ is “in the future” with reference to $x_{t-1}, u_t$ does not tell us much about $x_{t-1}$ . This means the term $p(x_{t-1}|z_{1:t-1}, u_{1:t}, m)$ can be simplified to $p(x_{t-1}|z_{1:t-1}, u_{1:t-1}, m)$ .
