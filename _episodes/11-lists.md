---
title: "Lists"
teaching: 10
exercises: 10
questions:
- "How can I store multiple values?"
objectives:
- "Explain why programs need collections of values."
- "Write programs that create flat lists, index them, and modify them through assignment and method calls."
keypoints:
- "A list stores many values in a single structure."
- "Use an item's index to fetch it from a list."
- "Lists' values can be replaced by assigning to them."
- "Appending items to a list lengthens it."
- "Indexing beyond the end of the collection is an error."
---
We have been working with one dataset at a time. With programming however,
we have the ability to reproduce the same work on multiple sets of data.
Let's look at some concepts that will allow us to later group together a
collection of file names for us to repeat analysis on.

## A list stores many values in a single structure.

*   Doing calculations with a hundred variables called `pressure_001`, `pressure_002`, etc.,
    would be at least as slow as doing them by hand.
*   Use a *list* to store many values together.
    *   Contained within square brackets `[...]`.
    *   Values separated by commas `,`.
*   Use `len` to find out how many values are in a list.

~~~
pressures = [0.273, 0.275, 0.277, 0.275, 0.276]
print('pressures:', pressures)
print('length:', len(pressures))
~~~
{: .language-python}
~~~
pressures: [0.273, 0.275, 0.277, 0.275, 0.276]
length: 5
~~~
{: .output}

## Use an item's index to fetch it from a list.
*    First item starts at 0.
*    Items can be referenced counting from the end with negative numbers.

~~~
print('first item:', pressures[0])
print('fifth item:', pressures[4])
print('last item:', pressures[-1])
~~~
{: .language-python}
~~~
zeroth item: 0.273
fourth item: 0.276
last item: 0.276
~~~
{: .output}

## Indexing beyond the end of the collection is an error.

*   Python reports an `IndexError` if we attempt to access a value that doesn't exist.
    *   This is a kind of [runtime error]({{ page.root }}/04-built-in/#runtime-error).
    *   Cannot be detected as the code is parsed
        because the index might be calculated based on data.

~~~
print('100th item:', pressures[99])
~~~
{: .language-python}
~~~
IndexError: string index out of range
~~~
{: .output}

## Lists' values can be replaced by assigning to them.

*   Use an index expression on the left of assignment to replace a value.

~~~
pressures[0] = 0.265
print('pressures is now:', pressures)
~~~
{: .language-python}
~~~
pressures is now: [0.265, 0.275, 0.277, 0.275, 0.276]
~~~
{: .output}

## Appending items to a list lengthens it.

*   Use `list_name.append` to add items to the end of a list.

~~~
pressures.append(0.269)
print('pressures:', pressures)
~~~
{: .language-python}
~~~
pressures: [0.265, 0.275, 0.277, 0.275, 0.276, 0.269]
~~~
{: .output}

*   `append` is a *method* of lists.
    *   Like a function, but tied to a particular object.
*   Use `object_name.method_name` to call methods.
    *   Deliberately resembles the way we refer to things in a library.
*   There are many other methods of lists.
    *   Use `help(list)` to view.
