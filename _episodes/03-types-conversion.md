---
title: "Data Types and Type Conversion"
teaching: 10
exercises: 10
questions:
- "What kinds of data do programs store?"
- "How can I convert one type to another?"
objectives:
- "Explain key differences between integers and floating point numbers."
- "Explain key differences between numbers and character strings."
- "Use built-in functions to convert between integers, floating point numbers, and strings."
keypoints:
- "Every value has a type."
- "Use the built-in function `type` to find the type of a value."
- "Types control what operations can be done on values."
- "Strings can be added."
- "Strings have a length (but numbers don't)."
- "Must convert numbers to strings or vice versa when operating on them."
- "Can mix integers and floats freely in operations."
- "Variables only change value when something is assigned to them."
---
## Every value has a type.

*   Every value in a program has a specific type.
*   Integer (`int`): represents positive or negative whole numbers like 3 or -512.
*   Floating point number (`float`): represents real numbers like 3.14159 or -2.5.
*   Character string (usually called "string", `str`): text.
    *   Written in either single quotes or double quotes (as long as they match).
    *   The quote marks aren't printed when the string is displayed.

## Use the built-in function `type` to find the type of a value.

*   Use the built-in function `type` to find out what type a value has.
*   Works on variables as well.
    *   But remember: the *value* has the type --- the *variable* is just a label.

~~~
print(type(52))
~~~
{: .language-python}
~~~
<class 'int'>
~~~
{: .output}

~~~
fitness = 'average'
print(type(fitness))
~~~
{: .language-python}
~~~
<class 'str'>
~~~
{: .output}

## Types control what operations (or methods) can be performed on a given value.

*   A value's type determines what the program can do to it.

~~~
print(5 - 3)
~~~
{: .language-python}
~~~
2
~~~
{: .output}

~~~
print('hello' - 'h')
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-2-67f5626a1e07> in <module>()
----> 1 print('hello' - 'h')

TypeError: unsupported operand type(s) for -: 'str' and 'str'
~~~
{: .error}

## You can use the "+" operator on strings.

*   "Adding" character strings concatenates them.

~~~
full_name = 'Ahmed' + ' ' + 'Walsh'
print(full_name)
~~~
{: .language-python}
~~~
Ahmed Walsh
~~~
{: .output}

## Strings have a length (but numbers don't).

*   We saw earlier that the built-in function `len` counts the number of characters in a
string ('helium' has length 6).
*   But numbers don't have a length (not even zero).

~~~
print(len(52))
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-3-f769e8e8097d> in <module>()
----> 1 print(len(52))

TypeError: object of type 'int' has no len()
~~~
{: .error}

## <a name='convert-numbers-and-strings'></a> Must convert numbers to strings or vice versa when operating on them.

*   Cannot add numbers and strings.

~~~
print(1 + '2')
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-4-fe4f54a023c6> in <module>()
----> 1 print(1 + '2')

TypeError: unsupported operand type(s) for +: 'int' and 'str'
~~~
{: .error}

*   Not allowed because it's ambiguous: should `1 + '2'` be `3` or `'12'`?
*   Some types can be converted to other types by using the type name as a function.

~~~
print(1 + int('2'))
print(str(1) + '2')
~~~
{: .language-python}
~~~
3
12
~~~
{: .output}

## Can mix integers and floats freely in operations.

*   Integers and floating-point numbers can be mixed in arithmetic.
*   Python 3 automatically converts integers to floats as needed.
*   The result of the following calculation with an `int` and `float` is a `float`.

~~~
print('half is', 1 / 2.0)
print('three squared is', 3.0 ** 2)
~~~
{: .language-python}
~~~
half is 0.5
three squared is 9.0
~~~
{: .output}

## Variables only change value when something is assigned to them.

*   If we make one cell in a spreadsheet depend on another,
    and update the latter,
    the former updates automatically.
*   This does **not** happen in programming languages.

~~~
variable_one = 1
variable_two = 5 * variable_one
variable_one = 2
print('first is', variable_one, 'and second is', variable_two)
~~~
{: .language-python}
~~~
first is 2 and second is 5
~~~
{: .output}

*   The computer reads the value of `first` when doing the multiplication,
    creates a new value, and assigns it to `second`.
*   After that, `second` does not remember where it came from.

> ## Choose a Type
>
> What type of value (integer, floating point number, or character string)
> would you use to represent each of the following?  Try to come up with more than one good answer for each problem.  For example, in  # 1, when would counting days with a floating point variable make more sense than using an integer?  
>
> 1. Number of days since the start of the year.
> 2. Time elapsed from the start of the year until now in days.
> 3. Serial number of a piece of lab equipment.
> 4. A lab specimen's age
> 5. Current population of a city.
> 6. Average population of a city over time.
>
> > ## Solution
> >
> > The answers to the questions are:
> > 1. Integer, since the number of days would lie between 1 and 365. 
> > 2. Floating point, since fractional days are required
> > 3. Character string if serial number contains letters and numbers, otherwise integer if the serial number consists only of numerals
> > 4. This will vary! How do you define a specimen's age? whole days since collection (integer)? date and time (string)?
> > 5. Choose floating point to represent population as large aggregates (eg millions), or integer to represent population in units of individuals.
> > 6. Floating point number, since an average is likely to have a fractional part.
> {: .solution}
{: .challenge}

> ## Arithmetic with Different Types
>
> Which of the following will return the floating point number `2.0`?
> Note: there may be more than one right answer.
>
> ~~~
> first = 1.0
> second = "1"
> third = "1.1"
> ~~~
> {: .language-python}
>
> 1. `first + float(second)`
> 2. `float(second) + float(third)`
> 3. `first + int(third)`
> 4. `first + int(float(third))`
> 5. `int(first) + int(float(third))`
> 6. `2.0 * second`
>
> > ## Solution
> >
> > Answer: 1 and 4
> {: .solution}
{: .challenge}
