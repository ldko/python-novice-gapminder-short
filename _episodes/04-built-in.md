---
title: "Built-in Functions and Help"
teaching: 15
exercises: 10
questions:
- "How can I find out what built-in functions do?"
objectives:
- "Use help to display documentation for built-in functions."
keypoints:
- "Functions may only work for certain (combinations of) arguments."
- "Functions may have default values for some arguments."
- "Use the built-in function `help` to get help for a function."
- "The Jupyter Notebook has two ways to get help."
---
## A function may take zero or more arguments.

*   We have seen some functions already (`print`, `len`, `type`, `int`, `str`)
    --- now let's take a closer look.
*   An *argument* is a value passed into a function.
*   `len` takes exactly one.
*   `int`, `str`, and `float` create a new value from an existing one.
*   `print` takes zero or more.
*   `print` with no arguments prints a blank line.

## Commonly-used built-in function `round` and its arguments.

*   `round` will round off a floating-point number.
*   Functions may have default values for some arguments.
*   By default, rounds to zero decimal places.

~~~
round(3.712)
~~~
{: .language-python}
~~~
4
~~~
{: .output}

*   We can specify the number of decimal places we want.

~~~
round(3.712, 1)
~~~
{: .language-python}
~~~
3.7
~~~
{: .output}

## Argument's types matter.

~~~
round(3.712, 1.5)
~~~
{: .language-python}
~~~
TypeError                                 Traceback (most recent call last)
<ipython-input-43-95f04cdcdc64> in <module>
----> 1 round(3.712, 1.5)

TypeError: 'float' object cannot be interpreted as an integer
~~~
{: .output}

## Use the built-in function `help` to get help for a function.

*   Every built-in function has online documentation.

~~~
help(round)
~~~
{: .language-python}
~~~
Help on built-in function round in module builtins:

round(number, ndigits=None)
    Round a number to a given precision in decimal digits.
    
    The return value is an integer if ndigits is omitted or None.  Otherwise
    the return value has the same type as the number.  ndigits may be negative.
~~~
{: .output}

## The Jupyter Notebook has two ways to get help.

*   Option 1: Place the cursor near where the function is invoked in a cell
    (i.e., the function name or its parameters),
    * Hold down <kbd>Shift</kbd>, and press <kbd>Tab</kbd>.
    * Do this several times to expand the information returned.
*   Option 2: Type the function name in a cell with a question mark after it. Then run the cell.

> ## Explore the Python docs!
>
> The [official Python documentation](https://docs.python.org/3/) is arguably the most complete
> source of information about the language. It is available in different languages and contains a lot of useful
> resources. The [Built-in Functions page](https://docs.python.org/3/library/functions.html) contains a catalogue of
> all of these functions, including the ones that we've covered in this lesson. Some of these are more advanced and
> unnecessary at the moment, but others are very simple and useful.
{: .callout}
