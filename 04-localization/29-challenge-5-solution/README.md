# Challenge 5 Solution

> Part of: **C++ Checkpoint**

## Additional Content

Here's my solution:

`Doubler.h`
```
#ifndef DOUBLER_H
#define DOUBLER_H

void Doubler(int& n);

#endif  // DOUBLER_H
```

`Doubler.cpp`
```
#include "Doubler.h"

void Doubler(int& n) {
  n *= 2;
}
```

The tricky part here was making sure to use the `&` operator to pass `n` as a reference.
