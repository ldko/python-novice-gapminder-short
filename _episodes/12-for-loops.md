---
title: "For Loops"
teaching: 10
exercises: 15
questions:
- "How can I make a program do many things?"
objectives:
- "Explain what for loops are normally used for."
keypoints:
- "A *for loop* executes commands once for each value in a collection."
- "A `for` loop is made up of a collection, a loop variable, and a body."
- "The first line of the `for` loop must end with a colon, and the body must be indented."
- "Indentation is always meaningful in Python."
- "Loop variables can be called anything (but it is strongly advised to have a meaningful name to the looping variable)."
- "The body of a loop can contain many statements."
---
## A *for loop* executes commands once for each value in a collection.

*   Doing calculations on the values in a list one by one
    is as painful as working with `pressure_001`, `pressure_002`, etc.
*   A *for loop* tells Python to execute some statements once for each value in a list,
    a character string,
    or some other collection.
*   "for each thing in this group, do these operations"

~~~
for number in [2, 3, 5]:
    print(number)
~~~
{: .language-python}

*   This `for` loop is equivalent to:

~~~
print(2)
print(3)
print(5)
~~~
{: .language-python}

*   And the `for` loop's output is:

~~~
2
3
5
~~~
{: .output}

## A `for` loop is made up of a collection, a loop variable, and a body.

~~~
for number in [2, 3, 5]:
    print(number)
~~~
{: .language-python}

*   The collection, `[2, 3, 5]`, is what the loop is being run on.
*   The body, `print(number)`, specifies what to do for each value in the collection.
*   The loop variable, `number`, is what changes for each *iteration* of the loop.
    *   The "current thing".

## The first line of the `for` loop must end with a colon, and the body must be indented.

*   The colon at the end of the first line signals the start of a *block* of statements.
*   Python uses indentation rather than `{}` or `begin`/`end` to show *nesting*.
    *   Any consistent indentation is legal, but almost everyone uses four spaces.

~~~
for number in [2, 3, 5]:
print(number)
~~~
{: .language-python}
~~~
IndentationError: expected an indented block
~~~
{: .error}

*   Indentation is always meaningful in Python.

~~~
firstName = "Jon"
  lastName = "Smith"
~~~
{: .language-python}
~~~
  File "<ipython-input-7-f65f2962bf9c>", line 2
    lastName = "Smith"
    ^
IndentationError: unexpected indent
~~~
{: .error}

*   This error can be fixed by removing the extra spaces
    at the beginning of the second line.

## Loop variables can be called anything.

*   As with all variables, loop variables are:
    *   Created on demand.
    *   Meaningless: their names can be anything at all.

~~~
for kitten in [2, 3, 5]:
    print(kitten)
~~~
{: .language-python}

## The body of a loop can contain many statements.

*   But no loop should be more than a few lines long.
*   Hard for human beings to keep larger chunks of code in mind.

~~~
for number in [2, 3, 5]:
    squared = number ** 2
    print(number, squared)
~~~
{: .language-python}
~~~
2 4
3 9
5 25
~~~
{: .output}

> ## Reversing a String
>
> Fill in the blanks in the program below so that it prints "nit"
> (the reverse of the original character string "tin").
>
> ~~~
> original = "tin"
> result = ____
> for char in original:
>     result = ____
> print(result)
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > original = "tin"
> > result = ""
> > for char in original:
> >     result = char + result
> > print(result)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Practice Accumulating
>
> Fill in the blanks in each of the programs below
> to produce the indicated result.
>
> ~~~
> # Total length of the strings in the list: ["red", "green", "blue"] => 12
> total = 0
> for word in ["red", "green", "blue"]:
>     ____ = ____ + len(word)
> print(total)
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > total = 0
> > for word in ["red", "green", "blue"]:
> >     total = total + len(word)
> > print(total)
> > ~~~
> > {: .language-python}
> {: .solution}
>
> ~~~
> # List of word lengths: ["red", "green", "blue"] => [3, 5, 4]
> lengths = ____
> for word in ["red", "green", "blue"]:
>     lengths.____(____)
> print(lengths)
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > lengths = []
> > for word in ["red", "green", "blue"]:
> >     lengths.append(len(word))
> > print(lengths)
> > ~~~
> > {: .language-python}
> {: .solution}
>
> ~~~
> # Concatenate all words: ["red", "green", "blue"] => "redgreenblue"
> words = ["red", "green", "blue"]
> result = ____
> for ____ in ____:
>     ____
> print(result)
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > words = ["red", "green", "blue"]
> > result = ""
> > for word in words:
> >     result = result + word
> > print(result)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Cumulative Sum
>
> Reorder and properly indent the lines of code below
> so that they print a list with the cumulative sum of data.
> The result should be `[1, 3, 5, 10]`.
>
> ~~~
> cumulative.append(total)
> for number in data:
> cumulative = []
> total = total + number
> total = 0
> print(cumulative)
> data = [1,2,2,5]
> ~~~
> {: .language-python}
> > ## Solution
> > ~~~
> > total = 0
> > data = [1,2,2,5]
> > cumulative = []
> > for number in data:
> >     total = total + number
> >     cumulative.append(total)
> > print(cumulative)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}
