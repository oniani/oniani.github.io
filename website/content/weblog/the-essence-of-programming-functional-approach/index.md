+++
title = "The Essence of Programming - Functional Approach"
date = 2018-11-25
+++

This blogpost is a general overview of a rather
underappreciated programming methodology called
functional programming.

<!-- more -->

This blogpost is a general overview of a rather underappreciated programming
methodology called functional programming. Throughout the blogpost, I will
occasionally use the purely functional programming language Haskell as well
as an imperative-style programming language Python. There is also a few lines
of C++. I will be assuming the knowledge of basic programming concepts such as
variable assignment, arithmetic operations, conditional statements, functions,
loops, and recursion.

It is important to note that the blogpost is just an introduction to the
paradigms in functional programming and does not cover any of them in great
detail.

<br>

---

**Table of Contents**

- [What is Functional Programming?](#what-is-functional-programming)
- [Classes VS Functions](#classes-vs-functions)
- [Natural Results](#natural-results)
- [Math, Sets, and Haskell](#math-sets-and-haskell)
- [State Changes and Functional Programming](#state-changes-and-functional-programming)
- [Control Flow](#control-flow)
  - [1. Functional Languages Are Declarative](#1-functional-languages-are-declarative)
  - [2. Functional Programming And Lambda Calculus](#2-functional-programming-and-lambda-calculus)
  - [3. Getting Rid of Loops](#3-getting-rid-of-loops)
- [Purely Functional Languages](#purely-functional-languages)
- [Conclusion](#conclusion)
- [How to Get Started with Functional Programming?](#how-to-get-started-with-functional-programming)

---

<br>

### [What is Functional Programming?](#what-is-functional-programming)

![New keyboard](new-keyboard.png)

As mentioned above, functional programming is just an approach to programming.
Particularly, it refers to programming using functions, hence the name
_functional programming_. To better understand what it means for a programming
language to be functional, let's make a short side-by-side comparison of
functional and, wildly popular, imperative style of programming languages and
then discuss the differences in detail.

|                         Imperative language                          |                    Functional language                     |
| :------------------------------------------------------------------: | :--------------------------------------------------------: |
|        Classes and/or structures are the first-class objects         |           Functions are the first-class objects            |
|                     State changes are important                      |        State changes are limited (or non-existent)         |
| The primary control flows include loops, conditionals, and functions | The primary control flows are function calls and recursion |

### [Classes VS Functions](#classes-vs-functions)

The first comparison shows that, generally speaking, in the imperative
languages (_Python, Java, Lua, Nim etc._), variables (instances of classes
and/or structures) dominate over all other objects. Thus, imperative paradigm
makes a clear distinction between variables and functions. On the other hand,
in functional programming languages, functions are the first-class citizens
making virtually everything else rank below them.

Imperative programming languages treat variables as data while functions are
generally used just to manipulate variables. When programming in a functional
language, we say that functions are very similar to variables. In fact, we say
that they are no different than variables as they not only manipulate the data,
but also represent the data themselves. Thus, in the functional world, we say
that the piece of code like a function is also data.

I will give you a concise proof of why functions are data. Remember the table
representations of functions you've learned at some point in the elementary
school? That's the proof! Any function can be represented as a table of values.
For instance, consider a function $f(x) = 2x$. The following will be a table
representation of the function.

| $x$ | $f(x)$ |
| :-: | :----: |
|  0  |   0    |
|  1  |   2    |
|  2  |   4    |
|  3  |   6    |
|  4  |   8    |
|  5  |   10   |
|  6  |   12   |
| ... |  ...   |

Looks more like data? That's because it is the data! We have effectively
generated a 2-column table where each of the cells has a certain value.
Reminds of SQL tables or pandas data frames?

### [Natural Results](#natural-results)

Because functions are so important, there are natural results and outcomes
which are shared among most of functional languages.

Let's write a Haskell function to find the factorial of a positive integer.

```haskell
-- | A function to find the factorial of a positive integer
factorial x = product [1..x]  -- easy as that
```

The function builds a list of integers from 1 up to x and then calculates
the product of these elements. This way we effectively get a product
$1 \times 2 \times 3 .. \times \ x$ which is the same as $x!$.
Since we now have a function, we can call it with the actual parameters!

```haskell
print (factorial 1)  -- prints out 1
print (factorial 6)  -- prints out 720
print (factorial 9)  -- prints out 362880
```

As we see, something that in imperative languages would need importing modules,
for loops or while loops can be writte as a one-liner in Haskell. This is one
of the outcomes of obsession over functions. Most functional languages have a
rich pool of predefined functions that help manipulate data. In the example
above, we also see a very interesting notation. Namely, `[1..x]` which builds
up a list of integers from 1 up to $x$ ($x$ must also be an integer such that
$x \geq 1$). Thus, another outcome is that data structures and collections can
be created very easily, usually just in a single line of code, leaving more
time for the programmer to deal with functions and the logic. These are some
of the reasons why functional languages are so concise.

### [Math, Sets, and Haskell](#math-sets-and-haskell)

Notice that in the factorial function above, I excluded the case when the
function is called with $0$ ($0! = 1$). It was done on purpose so that now
we are able to add some other notation and explain the whole function in
detail. Below is a better and more complete version of the function.

```haskell
-- | A function to find the factorial of a number
factorial :: Integer -> Integer
factorial 0 = 1
factorial x = product [1..x]
```

`::` - prompts that it is a function declaration

`Integer` - type that can hold any number no matter how big, up to the limit of
the machine's memory (so yes, this means you never have arithmetic overflows).

`->` - tells either what is the type of the next formal parameter or what is
the type of the output

Looks similar to something you have seen before? If you have taken any
undergraduate math class, there is a big chance that you've encountered
the following notation:

$$f : A \rightarrow B : x \mapsto y$$

The notation above describes/defines a simple function that takes an input
from set $A$ and maps it to the output in the set $B$.

Here is the complete definition of the factorial function that we saw above:

$$f : \mathbb{Z}^+\cup \{0\} \rightarrow \mathbb{Z}^+ : x \mapsto x!$$

Haskell defines it the similar manner.

`factorial :: Integer -> Integer` says that `factorial`
is a function that takes an element from the set of integers and maps it to
some other element in the set of integers. As opposed to math, however, Haskell
does not use $\mapsto$ notation and instead has the statements below it.

```haskell
factorial 0 = 1
factorial x = product [1..x]
```

The code above is equivalent to saying that if the element is 0, map it to 1
and in all other cases, map it to the product from 1 up to the element.

### [State Changes and Functional Programming](#state-changes-and-functional-programming)

Functional languages have a limited notion of state and typically, avoid the
shared mutable state at any cost. **Purely** (see [Purely Functional Languages](#purely-functional-languages))
functional languages like Haskell, do not have any state at all. Since there
are no changes in state, there are no variables. Instead, functional languages
offer functions and immutable variables.

To make it clear, let's look at two examples below. One is from Python and the
other is from Haskell.

Python example

```python
# Define a variable 'my_number' and assign it to 3
my_number = 3

# Increment the variable 'my_number' by 1 and reassign it to the result
my_number += 1

print(my_number)  # Prints out 4
```

Let's repeat the same steps in Haskell.

```haskell
myNumber = 3    -- Define a variable 'myNumber' and assign it to 3
myNumber += 1   -- Haskell gags here (infinite loop)

print myNumber  -- This statement is not reachable
```

Looking at the code above, you might have already noticed that Haskell
does not allow us to change the state of the program. Now you might be
wondering how could one increment variables.

Here is a short answer:

```haskell
myNumber = 3                  -- Define a variable 'myNumber' and assign it to 3
myOtherNumber = myNumber + 1  -- Define a variable 'myOtherNumber' and assign it to 'myNumber'
myNumber = myOtherNumber      -- Redefine 'myNumber' and set it to 'myOtherNumber'
print myNumber                -- Prints out 4
```

**Longer and better answer**

![Let's recurse, shall we?](recurse-shall-we.png)

You do not really need such increments or decrements in functional programming
languages. You can easily overcome this hindrance through functions and
recursion. Therefore, instead of mutating objects, we use recursion to
gradually get to the target.

Here is the example of how one could translate a well-known accumulator pattern
from Python to Haskell.

Here is a classic Python accumulator pattern.

```python
# An accumulator pattern approach for finding
# the sum of the first 100 positive integers.

total = 0
for integer in range(1, 100):
    total += integer

print(total)  # Prints out 5050
```

Here is what it looks like in Haskell.

```haskell
accumulator 1 = 1                        -- The base case for the recursion
accumulator x = x + accumulator (x - 1)  -- The recursive case


main = print (accumulator 100)  -- Prints out 5050
```

In the code excerpt above, we did not use any loops. In fact, we could not use
any loops because functional languages do not support loops. Instead, we
defined a function, used the recursion and calculated the sum of the values
through function calls.

**<span style="color:purple">_Side note_</span>**

In this particular case, we do not even need to implement the recursive
accumulator pattern. All we need to do is use the already predefined `sum`
function and so-called texas range list notation that we have already
seen (`[1..x]`).

```haskell
print (sum [1..100])  -- Prints out 5050
```

### [Control Flow](#control-flow)

As we have already seen, there are no for loops or while loops in functional
programming languages and there are good reasons why. Let's list a few of them
and continue our discussion by elaborating on those reasons.

1. Functional languages are declarative.
2. Most of functional languages are heavily influenced by lambda calculus.
3. If you were to implement a functional programming language,
   you would yourself get rid of loops.

### [1. Functional Languages Are Declarative](#1-functional-languages-are-declarative)

For those who are new to the idea of declarative languages, let's first
discuss what it means for a language to be declarative. Here is a simple
definition:

> Declarative programming is a method to abstract away the control flow for
> logic required for performing an action, and instead involves stating what
> the task or desired outcome is.

The examples of declarative languages are SQL, Haskell, Prolog etc.

_Example 1_: Consider the SQL querying language. In SQL, one doesn't
describe what how to get the data. One just tells SQL what data is needed,
and SQL engine figures out the best way to get it.

_Example 2_: A better example might be comparing two implementations
of a simple function. Let's implement them in both Python and Haskell.

The function takes a list of integers and returns the sum of odd integers in it.

```python
def odd_sum(list_of_integers):
    """Return the sum of all odd integers in the list."""
    total = 0
    for integer in list_of_integers:
        if integer % 2 == 1:
            total += integer
    return total


print(odd_sum([1, 2, 3, 4, 5]))  # Prints out 9
```

Let's do a shallow analysis of the `odd_sum` function. As seen above, it
starts by declaring a variable `total` which is initially set to 0. Then,
we iterate over the list and through each iteration, we check if the
integer is odd and if it is, we add it to `total`. In the end, we return
the `total` variable.

Now, that we have analyzed the function a bit, notice that in the for
loop, through each iteration, we are giving Python directions when to
add the integer to `total` (only if it is odd). Thus, **we tell Python what
to do step-by-step**. This is an important characteristic that distinguishes
non-declarative languages from declarative ones.

Let's now look at the Haskell example.

```haskell
oddSum x = sum (filter odd x)

main = print (oddSum [1,2,3,4,5])  -- Prints out 9
```

Notice what we did here. First we defined a function `oddSum` which takes
a list. Then we used the function `filter` (happened to be predefined) in
conjunction with another predefined function `odd` (returns true if the value
is odd an false otherwise) to get the list of odd integers. Finally, we summed
up all the odd integers and got the result.

See the difference? In Python, we used a for loop and through each iteration,
we told Python whether to add the integer it to `total` or not. In Haskell,
however, we gave a whole list to the function and told it to just remove
all of the even integers from the list and then to sum up the rest (if you
eliminate all the even integers, you are obviously left with all the odd
integers). In other words, in the Haskell example, we do not care how the
functions `sum` and `filter` work internally, we only care about the fact that
they do their job - sum up the odd numbers in the list and return the value.

### [2. Functional Programming And Lambda Calculus](#2-functional-programming-and-lambda-calculus)

![Half-Life video game series](half-life-lambda.jpg)

Lambda calculus (also written as $\lambda$-calculus) is a branch of mathematics
which was developed by [Alonzo Church](https://en.wikipedia.org/wiki/Alonzo_Church)
in the 1930s. It is a formal system for expressing computation and an alternative
to what's called [Turing machine](https://en.wikipedia.org/wiki/Turing_machine) which
was introduced by [Alan Turing](https://en.wikipedia.org/wiki/Alan_Turing).
Turing machines involve loops and other non-declarative approaches (Turing machines
are the inspiration for programming languages like Java, Python, etc).
A few years later, Church and Turing collaboratively wrote a paper which is now
know as the [computability thesis](https://en.wikipedia.org/wiki/Church%E2%80%93Turing_thesis)
and proved that all the computation that was done using Turing machines could
effectively be done in lambda calculus as well. Hence, simply put, lambda calculus
has the power equivalent to that of Turing machines. Not too long after, people
decided to base programming languages on the ideas in lambda calculus (it was
just as powerful as Turing machines so why not?!). This led to shared characteristics
among functional languages such as lack of loops. Virtually all functional
programming languages have no loops because lambda calculus has no loops.
One could certainly add loops, but they would have been redundant. Instead,
functional languages use a mathematical idea of recursion. This is the part
of the reason why loops are not that appreciated in the functional world.

### [3. Getting Rid of Loops](#3-getting-rid-of-loops)

![For loop VS Runtime stack](loop-recursion_stack.png)

Despite the fact that sometimes they are very useful, loops must not be a part
of a functional programming language. There are several reasons for this.

1. Loops promote and advocate the idea of "imperativeness" (prompting the language what to do).
2. Loops usually involve mutating values which is, once again, against functional virtues.
3. Even if we did not use it imperatively and not mutate values, it would create unnecessary
   redundance in a language with the emphasis on recursion (which is just as powerful as a
   regular loop!)

### [Purely Functional Languages](#purely-functional-languages)

You might have seen word _pure_ in the beginning of the blogpost where I
mentioned that Haskell is _purely_ functional programming language. However, I
never defined what it means for a functional language to be pure. So let's do
it now!

Those who read the [Math, Sets, and Haskell](#math-sets-and-haskell), remember
the math notation for functions? I will use them to take the mystery out of
this concept of being _pure_!

Suppose we have a function $f : \mathbb{Z} \rightarrow \mathbb{Z}$. Then by
just looking at the function, we see that it takes an input from a set of
integers and its output is also in the set of integers. In other words,
function $f$ cannot take inputs like -1.9, 0.2, 12.7 etc. as well as it cannot
give an output like 12.6, 71.9, -9.1 etc. Its input(s) and output(s) could
**<u>only</u>** be integers.

Now, let's actually make this dull function $f$ do something. Consider the
function $f : \mathbb{Z} \rightarrow \mathbb{Z} : x \mapsto 2x$. Thus, we have
a function which does a fairly straightforward thing: takes an integer and maps
it to twice its value (which will also be an integer). Let's now look at the
Haskell implementation of this function

```haskell
-- | A function that takes an input and outputs twice its value
f :: Integer -> Integer
f x = 2 * x
```

The function above says that the input (corresponds to the `Integer` before the
arrow) is always an integer and the output (corresponds to the `integer` after
the arrow) is also an integer. **Hence, we always know what type is the input
and what type is the output.** In fact, we also know that the if we call a
function with say 5, we will always get the same result. Namely, `f 5 = 10`.
Hence, we got that input(s) and output(s) are always integers and the function
called with same actual parameters always return the same value! This is what
makes Haskell a purely functional language. **At any given point in time, we
always know what is the type of input and what is type of output. Besides,
we know that the function called with the same actual parameter(s), always
returns the same value**. Such functions virtually never produce side effects
since we already know what to expect for a given input. **Such functions are
called pure!**

To further demystify this idea, let's look at the following piece of code
from a C++ programming language.

```cpp
/*
 * An example of a function that is pretending to be pure.
 *
 */

#include <iostream>

using namespace std;

int not_so_pure_function(int value) {
    return value + rand() % 3;
}

int main() {
    cout << "Returns: " << not_so_pure_function(7) << endl;  // Prints out 8
    cout << "Returns: " << not_so_pure_function(7) << endl;  // Prints out 8
    cout << "Returns: " << not_so_pure_function(7) << endl;  // Prints out 7
}
```

Here, we defined a function that takes an integer input and it seems like the
output is also an integer. We now might be lured into thinking that function
`not_so_pure_function` gives the same output for the same input, but that is
clearly not the case here (that is why it's called `not_so_pure_function`).
Let's take a closer look at what the function does. It takes an integer value
and returns the value plus some random number which is 0, 1 or 2. When we first
called the function with the actual parameter 7, we got 8 as an output. The
second time, we got 8 again. The third time however, we got 7. Hence, for the
third time, the output was not the same. Therefore, the function is not pure.

You now might wondering why I could not do the same trick in Haskell. In fact,
I certainly can. However, in Haskell, such function would not have a type `Int`.
It would have a type `IO Int`. `IO` is usually associated with file input / output
and it is reasonable that it is associated with functions that are not always
"truthful" as File I/O could in fact be one of the nastiest experiences for a
programmer. So many things can go wrong! (e.g., writing to a file which was
deleted, reading from a file on a USB which was ejected, writing a file that
was moved to some other directory etc). Thus, when we deal with uncertainty
(which usually comes with side effects), Haskell warns us by using the `IO`
notation.

Here is how `not_so_pure_function` could be made _pure_ in Haskell.

```haskell
{-
Example of a function that if called with the same argument,
does not always return the same result.
-}

import System.Random (randomRIO)


purifiedFunction :: Int -> IO Int
purifiedFunction value = do
    randomValue <- randomRIO (0,2)
    return (value + randomValue)


main = do
    x <- purifiedFunction 7
    print x                  -- Prints out 9
    x <- purifiedFunction 7
    print x                  -- Prints out 7
    x <- purifiedFunction 7
    print x                  -- Prints out 9
```

Look at the Haskell code above. You can disregard all the notational fluff.
Just look at the return type of the function `purifiedFunction`. It is `IO Int`!
In other words, Haskell informs us that the function might have side effects.
This is exactly why Haskell is pure.

Finally, we can have sort of a definition of a pure functional language.

**<span style="color:RED">NOTE:</span>** Pure might mean a completely different
thing in non-functional languages.

> A functional language is pure if and only if the user is informed of all
> the side effects in a language or there are no side effects at all.

Actually, Haskell did not allow random values back in 1990s when its development
was first launched. Because of this, Haskell was considered useless for all
practical purposes. Eventually, developers and the Haskell committee decided
to change the direction of Haskell. In lieu of getting rid of all the side
effects, they decided to control the side effects and created a more "regulated"
programming environment.

### [Conclusion](#conclusion)

Functional programming languages are different from imperative ones. Most of
them are based on ideas in lambda calculus. Functional languages are the proper
subset of declarative languages. There are no loops and recursion is used instead.
Changes in state are non-existent and therefore, all the variables are immutable.
Functional languages have a bunch of predefined functions to make it easy for a
programmer to solve problems. Most of functional languages are also very concise
minimizing the time spent on coding and leaving more time for the logic.
Pure functional languages are the proper subset of functional languages.
Purely functional languages inform the user about the side effects in advance.

<br>

---

<br>

### [How to Get Started with Functional Programming?](#how-to-get-started-with-functional-programming)

![Haskell logo](haskell-logo.png)

There are a lot of functional languages. You will obviously have to decide
which one to learn first. My recommendation would be learning Haskell.
It is a purely functional programming language which has most of (if not all)
the functional ideas in it. Besides, SPJ ([Simon Payton Jones](https://en.wikipedia.org/wiki/Simon_Peyton_Jones))
dedicates most of his time on extending the language and adding new features
to it. So if there is something new and interesting in the world of functional
programming, Haskell will probably get it (and probably sooner than other
functional or imperative languages).

After learning one functional language, it is fairly easy ("easy" is relative,
but being familiar with one functional language automatically makes you
somewhat familiar with others) to transition to the other. Hence, once you have
a good grasp of functional ideas in Haskell, you can then move to languages
like Clojure, Scheme, F# etc.

To get started, visit the [Haskell documentation](https://www.haskell.org/documentation)
page which is full of various educational resources.
