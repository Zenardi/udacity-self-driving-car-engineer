# Challenge 4 Solution

> Part of: **C++ Checkpoint**

## Additional Content

Here's my solution:

```
#ifndef CAR_H
#define CAR_H

class Car {    
 public:
  Car();
  void wearAndTear();
  bool drive();
  void fix();
 private:
  bool in_working_condition_;
};

#endif  // CAR_H
```

The `Car` class is pretty straightforward. The trickiest part, I found, was making sure that the constructor was defined.

Note, the trailing `_` on `in_working_condition_` is common tactic for designating private properties in C++.

Ok! One more challenge to go.
