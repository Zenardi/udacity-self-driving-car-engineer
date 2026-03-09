# Exercise Solution: Simpson's Rule

> Part of: **Motion Planning**

## Additional Content

Refer to the code below to check the solution to the exercise you just completed!
## TODO - What is Theta(s)?
```
double calc_theta(const double s, const std::array

& a) {
  // TODO - What is Theta(s)?
  // theta(s) = a3*s^4/4 + a2*s^3/3 + a1*s^2/2 + a0*s
  return (((a[3] * s / 4 + a[2] / 3) * s + a[1] / 2) * s + a[0]) * s;
}
```

## TODO - What is s_i (or x_i on Simpsons Rule equation)
```
std::vector generate_f_s0_sn(const double delta_s,
                                     const std::array& a,
                                     const std::size_t n) {
  std::vector f_s(n + 1);
  for (size_t i = 0; i <= n; ++i) {
    // TODO - What is s_i (or x_i on Simpsons Rule equation)
    // f(x) = dx / 3.0 * (f(x0) + 4.0 * f(x1) + 2.0 * f(x2) + 4.0 * f(x3) + 2.0
    // * f(x4) + ... + func[n]);
    // dx = sf/n;
    // xi = i*dx;
    // HINT: s_i = i * delta_s;
    double s_i = i * delta_s;
    double theta_i = calc_theta(s_i, a);
    f_s[i] = std::cos(theta_i);
  }
  return f_s;
}
```
## TODO - Put together Simpson's Rule.
```
double IntegrateBySimpson(const std::vector& func, const double dx,
                          const std::size_t n) {
  if (n == 0) {
    return 0.0;
  }

  double sum_even = 0.0;
  double sum_odd = 0.0;
  for (std::size_t i = 1; i < n; ++i) {
    if ((i & 1) != 0) {
      sum_odd += func[i];
    } else {
      sum_even += func[i];
    }
  }

  // TODO - Put together Simpson's Rule.
  // HINT: f(x) = dx / 3.0 * (4.0 * sum_odd + 2.0 * sum_even + func[0] +
  // func[n]);
  return dx / 3.0 * (4.0 * sum_odd + 2.0 * sum_even + func[0] + func[n]);
}
```
