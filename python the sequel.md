# More python with modules and stuff

## Random

This module implements pseudo-random number generators for various distributions.

For integers, uniform selection from a range. For sequences, uniform selection of a random element, a function to generate a random permutation of a list in-place, and a function for random sampling without replacement.

Almost all module functions depend on the basic function `random()`, which generates a random float uniformly in the semi-open range. Python uses the Mersenne Twister as the core generator. It produces 53-bit precision floats and has a period of 2\*\*19937-1. The underlying implementation in C is both fast and threadsafe. The Mersenne Twister is one of the most extensively tested random number generators in existence. However, being completely deterministic, it is not suitable for all purposes, and is completely unsuitable for cryptographic purposes.

The functions supplied by this module are actually bound methods of a hidden instance of the random.

### Random class

You can instantiate your own instances of Random to get generators that don’t share state. This is especially useful for multi-threaded programs, creating a different instance of Random for each thread, and using the `jumpahead()` method to make it likely that the generated sequences seen by each thread don’t overlap.

Class Random can also be subclassed if you want to use a different basic generator of your own devising: in that case, override the `random()`, `seed()`, `getstate()`, `setstate()` and `jumpahead()` methods. Optionally, a new generator can supply a `getrandbits()` method — this allows `randrange()` to produce selections over an arbitrarily large range.

Taken from the python docs at [https://docs.python.org/2/library/random.html](https://docs.python.org/2/library/random.html)

### Basic Usage

```py
>>> random.random()        # Random float x, 0.0 <= x < 1.0
0.37444887175646646
>>> random.uniform(1, 10)  # Random float x, 1.0 <= x < 10.0
1.1800146073117523
>>> random.randint(1, 10)  # Integer from 1 to 10, endpoints included
7
>>> random.randrange(0, 101, 2)  # Even integer from 0 to 100
26
>>> random.choice('abcdefghij')  # Choose a random element
'c'

>>> items = [1, 2, 3, 4, 5, 6, 7]
>>> random.shuffle(items)
>>> items
[7, 3, 2, 5, 6, 4, 1]

>>> random.sample([1, 2, 3, 4, 5],  3)  # Choose 3 elements
[4, 1, 5]
```

## Maths

Math operators in python.

| Title            | Operator                | Description                                          |
| ---------------- | ----------------------- | ---------------------------------------------------- |
| Addition         | `+`                     | Takes two arguments, adds two numbers                |
| Subtraction      | `-`                     | Two arguments, subtracts                             |
| Multiplication   | `*`                     | Two args, multiplies                                 |
| Division         | `/`                     | 2 args, divides                                      |
| Integer Devision | `//`                    | Division, but returns integers                       |
| Modulo           | `%`                     | 2 args, returns the remainder from division.         |
| Indices          | `**`                    | 2 args, makes something go to the power of something |
| Pi               | `import math` `math.pi` | Returns the value of pi                              |

## Time

This module provides various time-related functions. For related functionality, see also the datetime and calendar modules.

Although this module is always available, not all functions are available on all platforms. Most of the functions defined in this module call platform C library functions with the same name. It may sometimes be helpful to consult the platform documentation, because the semantics of these functions varies among platforms.

An explanation of some terminology and conventions is in order.

- The epoch is the point where the time starts. On January 1st of that year, at 0 hours, the “time since the epoch” is zero. For Unix, the epoch is 1970. To find out what the epoch is, look at gmtime(0).
- The functions in this module do not handle dates and times before the epoch or far in the future. The cut-off point in the future is determined by the C library; for Unix, it is typically in 2038.
- Year 2000 (Y2K) issues: Python depends on the platform’s C library, which generally doesn’t have year 2000 issues, since all dates and times are represented internally as seconds since the epoch. Functions accepting a struct_time (see below) generally require a 4-digit year. For backward compatibility, 2-digit years are supported if the module variable accept2dyear is a non-zero integer; this variable is initialized to 1 unless the environment variable PYTHONY2K is set to a non-empty string, in which case it is initialized to 0. Thus, you can set PYTHONY2K to a non-empty string in the environment to require 4-digit years for all year input. When 2-digit years are accepted, they are converted according to the POSIX or X/Open standard: values 69-99 are mapped to 1969-1999, and values 0–68 are mapped to 2000–2068. Values 100–1899 are always illegal.
- UTC is Coordinated Universal Time (formerly known as Greenwich Mean Time, or GMT). The acronym UTC is not a mistake but a compromise between English and French.

**Use the following functions to convert between time representations:**

| From | To | Use |
| ---- | -- | --- |
| seconds since the epoch | `struct_time` in UTC | `gmtime()` |
| seconds since the epoch | `struct_time` in local time | `localtime()` |
| `struct_time` in UTC | seconds since the epoch | `calendar.timegm()` |
| `struct_time` in local time | seconds since the epoch | `mktime()` |