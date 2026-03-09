# Challenge 1 Solution

> Part of: **C++ Checkpoint**

## Additional Content

Here's my solution:

```cpp
#include

int main() {
  std::cout << "no more steering wheels" << std::endl;
  return 0;
}
```

`std` refers to namespace `std` and the `<<` operator passes sequences of characters to stdout. In fact, two sequences of characters get passed to stdout: `"no more steering wheels"` and `std::endl`, a newline character (`std::endl` also flushes the buffer).

You may be used to adding a `using namespace std` line after your `include` statements - however, under the [Google C++ style guide](https://google.github.io/styleguide/cppguide.html#Namespaces), you should not utilize *using-directives* to make all names from a namespace available. You could instead use `using std::cout;` and `using std::endl;` near the top so that you do not have to re-write `std::` before each instance of these - it does not make much of a difference here, but could be more helpful when you use them multiple times!

It's worth noting that `"no more steering wheels"` is not a string like a Python string, rather it's a `char []` - a sequence of characters.

Time for another! Let's control some flow.
