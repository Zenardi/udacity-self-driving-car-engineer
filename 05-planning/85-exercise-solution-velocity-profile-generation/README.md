# Exercise Solution: Velocity Profile Generation 

> Part of: **Motion Planning**

## Additional Content

Refer to the code below to check the solution to the exercise you just completed!
## TODO - calc final speed: Calculate the final distance.
Make sure you handle negative discriminant and make v_f = 0 in that case. If the discriminant is inf or nan return
infinity.

```
double calc_final_speed(const double v_i, const double a, const double d) {
  double v_f{0.0};  
  double disc = v_i * v_i + 2 * a * d;
  if (disc <= 0.0) {
    v_f = 0.0;
  } else if (disc == std::numeric_limits

::infinity() ||
             std::isnan(disc)) {
    v_f = std::numeric_limits::infinity();
  } else {
    v_f = std::sqrt(disc);
  }  
  return v_f;
}
```
## TODO - calc distance: use one of the common rectilinear accelerated equations of motion to calculate the distance traveled while going from v_i (initial velocity) to v_f (final velocity) at a constant acceleration/deceleration "a".

d = (v_f^2 - v_i^2) / (2 * a)

Make sure you handle div by 0

```
double calc_distance(const double v_i, const double v_f, const double a) {
  double d{0.0};
    if (std::abs(a) < DBL_EPSILON) {
    d = std::numeric_limits::infinity();
  } else {
    d = std::abs((v_f * v_f - v_i * v_i) / (2 * a));
  }  
  return d;
}
```
