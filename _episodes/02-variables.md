---
title: "Variables and Assignment"
teaching: 10
exercises: 10
questions:
- "How can I store data in programs?"
objectives:
- "Write programs that assign scalar values to variables and perform calculations with those values."
- "Correctly trace value changes in programs that use scalar assignment."
keypoints:
- "Use variables to store values."
- "Use `print` to display values."
- "Variables persist between cells."
- "Variables must be created before they are used."
- "Variables can be used in calculations."
- "Python is case-sensitive."
- "Use meaningful variable names."
---
## Use variables to store values.

*   **Variables** are names for values.
*   In Python the `=` symbol assigns the value on the right to the name on the left.
*   The variable is created when a value is assigned to it.
*   Here, Python assigns an age to a variable `age`
    and a name in quotes to a variable `first_name`.

    ~~~
    age = 42
    first_name = 'Ahmed'
    ~~~
    {: .language-python}

*   Variable names
    * can **only** contain letters, digits, and underscore `_` (typically used to separate words
      in long variable names)
    * cannot start with a digit
    * are **case sensitive** (age, Age and AGE are three different variables)
    *   There are conventions for using upper-case letters at the start of variable names so we
        will use lower-case letters for now.
*   Variable names that start with underscores like `__alistairs_real_age` have a special meaning
    so we won't do that until we understand the convention.

## Use meaningful variable names.

*   Python doesn't care what you call variables as long as they obey the rules
    (alphanumeric characters and the underscore).

~~~
flabadab = 42
ewr_422_yY = 'Ahmed'
~~~
{: .language-python}

*   Use meaningful variable names to help other people understand what the program does.
*   The most important "other person" is your future self.

## Use comments to add documentation to programs.

*    If you want to add information to explain what your code is doing, you can use the `#` to
     indicate a comment.
~~~
# This sentence isn't executed by Python.
flabadab = 42   #  current age - anything after '#' is ignored.
~~~
{: .language-python}

*    While using meaningful variable names helps avoid needing to explain with comments,
     if it is difficult to come up with a relatively short relevant variable name, this can help.

## Use `print` to display values.

*   Python has a built-in function called `print` that prints things as text.
*   Call the function (i.e., tell Python to run it) by using its name.
*   Provide values to the function (i.e., the things to print) in parentheses.
*   To add a string to the printout, wrap the string in single or double quotes.
*   The values passed to the function are called **arguments**

~~~
print(first_name, 'is', age, 'years old')
~~~
{: .language-python}
~~~
Ahmed is 42 years old
~~~
{: .output}

*   `print` automatically puts a single space between items to separate them.
*   And wraps around to a new line at the end.

## Variables must be created before they are used.

*   If a variable doesn't exist yet, or if the name has been mis-spelled,
    Python reports an error. (Unlike some languages, which "guess" a default value.)

~~~
print(last_name)
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-1-c1fbb4e96102> in <module>()
----> 1 print(last_name)

NameError: name 'last_name' is not defined
~~~
{: .error}

*   The last line of an error message is usually the most informative.

## Syntax errors are another common error seen.
*   Python reports a syntax error when it can't understand the source of a program.
*   Won't even try to run the program if it can't be parsed.

~~~
# Forgetting an end quote causes a syntax error.
last_name = 'Feng
~~~
{: .language-python}
~~~
  File "<ipython-input-56-f42768451d55>", line 2
    name = 'Feng
                ^
SyntaxError: EOL while scanning string literal
~~~
{: .error}

*   Look more closely at the error message to see what went wrong.

> ## Variables Persist Between Cells
>
> Be aware that it is the *order* of execution of cells that is important in a Jupyter notebook, not the order
> in which they appear. Python will remember *all* the code that was run previously, including any variables you have
> defined, irrespective of the order in the notebook. Therefore if you define variables lower down the notebook and then
> (re)run cells further up, those defined further down will still be present. As an example, create two cells with the
> following content, in this order:
>
> ~~~
> print(myval)
> ~~~
> {: .language-python}
>
> ~~~
> myval = 1
> ~~~
> {: .language-python}
>
> If you execute this in order, the first cell will give an error. However, if you run the first cell *after* the second
> cell it will print out `1`. To prevent confusion, it can be helpful to use the `Kernel` -> `Restart & Run All` option which
> clears the interpreter and runs everything from a clean slate going top to bottom.
{: .callout}

## Variables can be used in calculations.

*   We can use variables in calculations just as if they were values.
    *   Remember, we assigned the value `42` to `age` a few lines ago.

~~~
age = age + 3
print('Age in three years:', age)
~~~
{: .language-python}
~~~
Age in three years: 45
~~~
{: .output}

> ## Predicting Values
>
> What is the final value of `position` in the program below?
> (Try to predict the value without running the program,
> then check your prediction.)
>
> ~~~
> initial = 'left'
> position = initial
> initial = 'right'
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > print(position)
> > ~~~
> > {: .language-python}
> > ~~~
> > left
> > ~~~
> > {: .output}
> >
> > The `initial` variable is assigned the value `'left'`.
> > In the second line, the `position` variable also receives
> > the string value `'left'`. In third line, the `initial` variable is given the
> > value `'right'`, but the `position` variable retains its string value
> > of `'left'`.
> {: .solution}
{: .challenge}

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
