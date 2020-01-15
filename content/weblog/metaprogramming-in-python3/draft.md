+++
title = "Metaprogramming in Python3"
date = 2019-06-12
+++

In a nutshell, metaprogramming is a code that manipulates code.

Wikipedia describes it as follows:

> Metaprogramming is a programming technique in which computer programs have
> the ability to treat other programs as their data.

One could think of metaprogramming as writing code generators. As a side note,
functional programming is not considered metaprogramming despite the fact the
functions are considered data.

In Python3, there are a number of ways to do this. The most basic idea that is
also very useful is that of decorators.

Below is a minimal example of a decorator.

```python
from functools import wraps
from typing import Callable

def decorate(func: Callable) -> Callable:
    @wraps(func)
    def wrapper(*args, **kwargs) -> Callable:
        # Do some stuff...
        return func(*args, **kwargs)

    return wrapper
```

The idea of a decorator, as seen above, is very simple. It takes a function,
does some stuff, and then replicates the previous behavior of the function.
Therefore, it does a bit more than the actual function. The thing to bare in
mind is that decorators are a way to reduce code repetition.

Consider an example below.

```python
def hello(name: str):
    return f"Hello, {name}!"

def bye(name: str):
    return f"Bye, {name}!"

if __name__ == "__main__":
    print(hello("Sally"))
    print(hello("Garry"))
```

Suppose that we now want to redesign these functions to print a string
"Hi I am function hello" or "Hi I am function bye" depending on a function,
before the return statements. The most obvious solution to this problem is to
hardcode it.

```python
def hello(name: str):
    print("Hi from the function `hello`")
    return f"Hello, {name}!"

def bye(name: str):
    print("Hi from the function `bye`")
    return f"Bye, {name}!"

if __name__ == "__main__":
    print(hello("Sally"))
    print(hello("Garry"))
```

This, however, can be inconvenient if we had more than just 2 functions even
the behavior to replicate was more complex.

A common solution to this problem is to define a decorator.

```python
from functools import wraps
from typing import Callable

def hi_func(func: Callable) -> Callable:
    @wraps(func)
    def wrapper(*args, **kwargs) -> Callable:
        print(f"Hi from the function `{func.__name__}`")
        return func(*args, **kwargs)

    return wrapper

@hi_func
def hello(name: str):
    return f"Hello, {name}!"

@hi_func
def bye(name: str):
    return f"Bye, {name}!"

if __name__ == "__main__":
    print(hello("Sally"))
    print(hello("Garry"))
```
