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
