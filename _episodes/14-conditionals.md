---
title: "Conditionals"
teaching: 10
exercises: 15
questions:
- "How can programs do different things for different data?"
objectives:
- "Correctly write programs that use if and else statements and simple Boolean expressions (without logical operators)."
keypoints:
- "Use `if` statements to control whether or not a block of code is executed."
- "Conditionals are often used inside loops."
- "Use `else` to execute a block of code when an `if` condition is *not* true."
- "Use `elif` to specify additional tests."
---
## Use `if` statements to control whether or not a block of code is executed.

*   An `if` statement (more properly called a *conditional* statement)
    controls whether some block of code is executed or not.
*   Structure is similar to a `for` statement:
    *   First line opens with `if` and ends with a colon
    *   Body containing one or more statements is indented (usually by 4 spaces)

~~~
mass = 3.54
if mass > 3.0:
    print(mass, 'is large')

mass = 2.07
if mass > 3.0:
    print (mass, 'is large')
~~~
{: .language-python}
~~~
3.54 is large
~~~
{: .output}

## Conditionals are often used inside loops.

*   Not much point using a conditional when we know the value (as above).
*   But useful when we have a collection to process.

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 3.0:
        print(m, 'is large')
~~~
{: .language-python}
~~~
3.54 is large
9.22 is large
~~~
{: .output}

## Use `else` to execute a block of code when an `if` condition is *not* true.

*   `else` can be used following an `if`.
*   Allows us to specify an alternative to execute when the `if` *branch* isn't taken.

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 3.0:
        print(m, 'is large')
    else:
        print(m, 'is small')
~~~
{: .language-python}
~~~
3.54 is large
2.07 is small
9.22 is large
1.86 is small
1.71 is small
~~~
{: .output}

## Use `elif` to specify additional tests.

*   May want to provide several alternative choices, each with its own test.
*   Use `elif` (short for "else if") and a condition to specify these.
*   Always associated with an `if`.
*   Must come before the `else` (which is the "catch all").

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 9.0:
        print(m, 'is HUGE')
    elif m > 3.0:
        print(m, 'is large')
    else:
        print(m, 'is small')
~~~
{: .language-python}
~~~
3.54 is large
2.07 is small
9.22 is HUGE
1.86 is small
1.71 is small
~~~
{: .output}

> ## Compound Relations Using `and` or `or`
>
> Often, you want some combination of things to be true.  You can combine
> relations within a conditional using `and` and `or`.
> Let's look at an example with our gapminder data in mind to calculate what
> quartile a given life expectancy value will fall into. 
>
> ~~~
> expectancies = [62.5, 57.9, 81.0, -1]
> for exp in expectancies:
>     if exp > 0 and exp < 58.41:
>         # This observation is in the first quartile
>         quartile = 1
>     elif exp >= 58.41 and exp < 67.05:
>         # This observation is in the second quartile
>        quartile = 2
>     elif exp >= 67.05 and exp < 71.70:
>         # This observation is in the third quartile
>        quartile = 3
>     elif exp >= 71.70:
>         # This observation is in the fourth quartile
>        quartile = 4
>     else:
>         # This observation has bad data
>        quartile = None
>     print('life expectancy', exp, 'is in quartile', quartile)
> ~~~
> {: .language-python}
>
> ~~~
> life expectancy 62.5 is in quartile 2
> life expectancy 57.9 is in quartile 1
> liife expectancy 81.0 is in quartile 4
> life expectancy -1 is in quartile None
> ~~~
> {: .output}
{: .callout}

> ## Processing Small Files
>
> Modify this program so that it only processes files with fewer than 50 records.
>
> ~~~
> import glob
> import pandas as pd
> for filename in glob.glob('data/*.csv'):
>     contents = pd.read_csv(filename)
>     ____:
>         print(filename, len(contents))
> ~~~
> {: .language-python}
> > ## Solution
> >
> > ~~~
> > import glob
> > import pandas as pd
> > for filename in glob.glob('data/*.csv'):
> >     contents = pd.read_csv(filename)
> >     if len(contents) < 50:
> >         print(filename, len(contents))
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}
