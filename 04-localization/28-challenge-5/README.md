# Challenge 5

> Part of: **C++ Checkpoint**

## Additional Content

## References

Lower level languages, like C++, give you control over the way your objects are stored and accessed in memory. As a comparison, let's start by looking at how Python hides memory access from you.

```
def dict_modifier(d, key):
  d.pop(key, None)

sample_dict = {'some_key': 'some value'}
dict_modifier(sample_dict, 'some_key')
print(sample_dict)  # {}
```

In this case, `dict_modifier` removes a key from the dictionary passed to it. In effect, it treats the dictionary argument as a reference.

You may want to draw the conclusion that Python functions always treat arguments as references, but that's not true.

```
def adder(n):
  n += 1

i = 1
adder(i)
print(i)  # 1
```

Python does not pass primitives as references. As a result, `adder` receives a copy of `i` and `i` remains unchanged outside the function.

To be fair, the way Python handles arguments is perfectly reasonable. But what's happening behind the scenes is not perfectly obvious from the syntax alone.

C++, on the other hand, makes you decide how you'd like to treat function arguments. It also gives you control over how you'd like to access objects in memory, whether that's by simply referring to their address in memory or by their actual value.
### Pass by Reference

In this last challenge, I want you to finish the `doubler` function that doubles an `int` passed to it as a reference. You'll need to finish defining the function's parameters and body.
