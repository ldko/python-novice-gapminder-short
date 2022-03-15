---
title: "Programming Style"
teaching: 15
exercises: 15
questions:
- "How can I make my programs more readable?"
- "How do most programmers format their code?"
- "How can programs check their own operation?"
objectives:
- "Provide sound justifications for basic rules of coding style."
- "Refactor one-page programs to make them more readable and justify the changes."
- "Use Python community coding standards (PEP-8)."
keypoints:
- "Follow standard Python style in your code."
- "Use docstrings to provide builtin help."
---

## Coding style

A consistent coding style helps others (including our future selves) read and understand code more easily. Code is read much more often than it is written, and as the [Zen of Python](https://www.python.org/dev/peps/pep-0020) states, "Readability counts".
Python proposed a standard style through one of its first Python Enhancement Proposals (PEP), [PEP8](https://www.python.org/dev/peps/pep-0008).

Some points worth highlighting:
*   document your code and ensure that assumptions, internal algorithms, expected inputs, expected outputs, etc., are clear
*   use clear, semantically meaningful variable names
*   use white-space, *not* tabs, to indent lines (tabs can cause problems across different text editors, operating systems, and version control systems)


## Follow standard Python style in your code.

*   [PEP8](https://www.python.org/dev/peps/pep-0008):
    a style guide for Python that discusses topics such as how to name variables,
    how to indent your code,
    how to structure your `import` statements,
    etc.
    Adhering to PEP8 makes it easier for other Python developers to read and understand your code, and to understand what their contributions should look like.
*   To check your code for compliance with PEP8, you can use the [pycodestyle application](https://pypi.org/project/pycodestyle/) and tools like the [black code formatter](https://github.com/psf/black) can automatically format your code to conform to PEP8 and pycodestyle (a Jupyter notebook formatter also exists [nb_black](https://github.com/dnanhkhoa/nb_black)).
*   Some groups and organizations follow different style guidelines besides PEP8. For example, the [Google style guide on Python](https://google.github.io/styleguide/pyguide.html) makes slightly different recommendations. Google wrote an application that can help you format your code in either their style or PEP8 called [yapf](https://github.com/google/yapf/).
*   With respect to coding style, the key is *consistency*. Choose a style for your project be it PEP8, the Google style, or something else and do your best to ensure that you and anyone else you are collaborating with sticks to it. Consistency within a project is often more impactful than the particular style used. A consistent style will make your software easier to read and understand for others and for your future self.

## Use docstrings to provide builtin help.

If the first thing in a function is a character string that is not assigned directly to a variable, Python attaches it to the function, accessible via the builtin help function. This string that provides documentation is also known as a *docstring*.

~~~
def average(values):
    "Return average of values, or None if no values are supplied."

    if len(values) == 0:
        return None
    return sum(values) / len(values)

help(average)
~~~
{: .language-python}
~~~
Help on function average in module __main__:

average(values)
    Return average of values, or None if no values are supplied.
~~~
{: .output}

> ## Multiline Strings
>
> Often use *multiline strings* for documentation.
> These start and end with three quote characters (either single or double)
> and end with three matching characters.
>
> ~~~
> """This string spans
> multiple lines.
>
> Blank lines are allowed."""
> ~~~
> {: .language-python}
{: .callout}

> ## Document This
>
> Turn the comment in the following function into a docstring
> and check that `help` displays it properly.
>
> ~~~
> def middle(a, b, c):
>     # Return the middle value of three.
>     # Assumes the values can actually be compared.
>     values = [a, b, c]
>     values.sort()
>     return values[1]
> ~~~
> {: .language-python}
> > ## Solution
> >
> > ~~~
> > def middle(a, b, c):
> >     '''Return the middle value of three.
> >     Assumes the values can actually be compared.'''
> >     values = [a, b, c]
> >     values.sort()
> >     return values[1]
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}
