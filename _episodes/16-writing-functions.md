---
title: "Writing Functions"
teaching: 10
exercises: 15
questions:
- "How can I create my own functions?"
objectives:
- "Explain and identify the difference between function definition and function call."
- "Write a function that takes a small, fixed number of arguments and produces a single result."
keypoints:
- "Break programs down into functions to make them easier to understand."
- "Define a function using `def` with a name, parameters, and a block of code."
- "Defining a function does not run it."
- "Arguments in call are matched to parameters in definition."
- "Functions may return a result to their caller using `return`."
---
## Break programs down into functions to make them easier to understand.

*   Functions serve to break larger/more complicated code into smaller easier to understand pieces.
    *   *Encapsulate* complexity so that we can treat it as a single "thing".
*   Also enables *re-use*.
    *   Write one time, use many times.

~~~
def print_date(year, month, day):
    joined = str(year) + '/' + str(month) + '/' + str(day)
    print(joined)
~~~
{: .language-python}

## Define a function using `def` with a name, parameters, and a block of code.

*   Begin the definition of a new function with `def`.
*   Followed by the name of the function.
    *   Must obey the same rules as variable names.
*   Then *parameters* in parentheses.
    *   Empty parentheses if the function doesn't take any inputs.
*   Then a colon.
*   Then an indented block of code.

## Defining a function does not run it.

*   Like assigning a value to a variable.
*   Must call the function to execute the code it contains.

~~~
print_date(1871, 3, 19)
~~~
{: .language-python}
~~~
1871/3/19
~~~
{: .output}

## Arguments in call are matched to parameters in definition.

*   Functions are most useful when they can operate on different data.
*   Specify *parameters* when defining a function.
    *   These become variables when the function is executed.
    *   Are assigned the arguments in the call (i.e., the values passed to the function).
    *   If you don't name the arguments when using them in the call, the arguments will be matched to
parameters in the order the parameters are defined in the function.

Or, we can name the arguments when we call the function, which allows us to
specify them in any order:
~~~
print_date(month=3, day=19, year=1871)
~~~
{: .language-python}
~~~
1871/3/19
~~~
{: .output}

## Functions may return a result to their caller using `return`.

*   Every function returns something.
*   A function that doesn't explicitly `return` a value automatically returns `None`.
    `None` is a Python object that stands in anytime there is no value.

~~~
result = print_date(1871, 3, 19)
print('result of call is:', result)
~~~
{: .language-python}
~~~
1871/3/19
result of call is: None
~~~
{: .output}

*   Use `return ...` to give a value back to the caller.
*   May occur anywhere in the function.
*   But functions are easier to understand if `return` occurs:
    *   At the start to handle special cases.
    *   At the very end, with a final result.

~~~
def print_date(year, month, day):
    joined = str(year) + '/' + str(month) + '/' + str(day)
    return joined

result = print_date(1871, 3, 19)
print('result of call is:', result)
~~~
{: .language-python}
~~~
result of call is: 1871/3/19
~~~
{: .output}

> ## Using Functions in Pandas
>
> If we convert our life expectency quartile `for` loop code into a function. Pandas has
> an efficient way of running it for our data by its way of
> *applying* a function to a dataframe or a portion of a dataframe.  Here
> is an example:
>
> ~~~
> import pandas as pd
> def calculate_life_quartile(exp):
>     if exp > 0 and exp < 58.41:
>         # This observation is in the first quartile
>         return 1
>     elif exp >= 58.41 and exp < 67.05:
>         # second quartile
>        return 2
>     elif exp >= 67.05 and exp < 71.70:
>         # third quartile
>        return 3
>     elif exp >= 71.70:
>         # fourth quartile
>        return 4
>     else:
>         # bad data
>        return None
>
> data = pd.read_csv('data/gapminder_all.csv')
> data['life_qrtl'] = data['lifeExp_1952'].apply(calculate_life_quartile)
> ~~~
> {: .language-python}
>
> There is a lot in that second line, so let's take it piece by piece.
> On the right side of the `=` we start with `data['lifeExp']`, which is the
> column in the dataframe called `data` labeled `lifeExp`.  We use the
> `apply()` to do what it says, apply the `calculate_life_quartile` to the
> value of this column for every row in the dataframe.
{: .callout}

> ## Encapsulation
>
> Fill in the blanks to create a function that takes a single filename as an argument,
> loads the data in the file named by the argument,
> and returns the minimum value in that data.
>
> ~~~
> import pandas as pd
>
> def min_in_data(____):
>     data = ____
>     return ____
> ~~~
> {: .language-python}
> > ## Solution
> >
> > ~~~
> > import pandas as pd
> > 
> > def min_in_data(filename):
> >     data = pd.read_csv(filename)
> >     return data.min()
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Encapsulating Data Analysis
>
> Assume that the following code has been executed:
>
> ~~~
> import pandas as pd
>
> df = pd.read_csv('data/gapminder_gdp_asia.csv', index_col=0)
> japan = df.loc['Japan']
> ~~~
> {: .language-python}
>
> 1. Complete the statements below to obtain the average GDP for Japan
>    across the years reported for the 1980s.
>
>    ~~~
>    year = 1983
>    gdp_decade = 'gdpPercap_' + str(year // ____)
>    avg = (japan.loc[gdp_decade + ___] + japan.loc[gdp_decade + ___]) / 2
>    ~~~
>    {: .language-python}
>
> 2. Abstract the code above into a single function.
>
>    ~~~
>    def avg_gdp_in_decade(country, continent, year):
>        df = pd.read_csv('data/gapminder_gdp_'+___+'.csv',delimiter=',',index_col=0)
>        ____
>        ____
>        ____
>        return avg
>    ~~~
>    {: .language-python}
>
> 3. How would you generalize this function
>    if you did not know beforehand which specific years occurred as columns in the data?
>    For instance, what if we also had data from years ending in 1 and 9 for each decade?
>    (Hint: use the columns to filter out the ones that correspond to the decade,
>    instead of enumerating them in the code.)
>
> > ## Solution
> >
> > 1. The average GDP for Japan across the years reported for the 1980s is computed with:
> >
> >    ~~~
> >    year = 1983
> >    gdp_decade = 'gdpPercap_' + str(year // 10)
> >    avg = (japan.loc[gdp_decade + '2'] + japan.loc[gdp_decade + '7']) / 2
> >    ~~~
> >    {: .language-python}
> >
> > 2. That code as a function is:
> >
> >    ~~~
> >    def avg_gdp_in_decade(country, continent, year):
> >        df = pd.read_csv('data/gapminder_gdp_' + continent + '.csv', index_col=0)
> >        c = df.loc[country]
> >        gdp_decade = 'gdpPercap_' + str(year // 10)
> >        avg = (c.loc[gdp_decade + '2'] + c.loc[gdp_decade + '7'])/2
> >        return avg
> >    ~~~
> >    {: .language-python}
> >
> > 3. To obtain the average for the relevant years, we need to loop over them:
> >
> >    ~~~
> >    def avg_gdp_in_decade(country, continent, year):
> >        df = pd.read_csv('data/gapminder_gdp_' + continent + '.csv', index_col=0)
> >        c = df.loc[country]
> >        gdp_decade = 'gdpPercap_' + str(year // 10)
> >        total = 0.0
> >        num_years = 0
> >        for yr_header in c.index: # c's index contains reported years
> >            if yr_header.startswith(gdp_decade):
> >                total = total + c.loc[yr_header]
> >                num_years = num_years + 1
> >        return total/num_years
> >    ~~~
> >    {: .language-python}
> >
> > The function can now be called by:
> >
> > ~~~
> > avg_gdp_in_decade('Japan','asia',1983)
> > ~~~
> > {: .language-python}
> > 
> > ~~~
> > 20880.023800000003
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}
