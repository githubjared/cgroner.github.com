---
layout: post
title: An Introduction to List Comprehensions in Python
category: Python
last_changed: 2017-08-08
meta_desc: An introduction to using list comprehension syntax in the Python programming language.
permalink: /Python/2011/11/09/An-Introduction-to-List-Comprehensions-in-Python.html
---

## The basics.

Let's start with a simple list.

{% highlight python %}
>>> my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> my_list
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
{% endhighlight %}

Quite often, we'll need to build a new list from the elements of an existing list. For example, let's say we want to make a list containing all elements of `my_list`, each multiplied by 2. A common way to do this is by iterating through the existing list and building the new list:

{% highlight python %}
>>> new_list = []
>>> for x in my_list:
...   new_list.append(x * 2)
... 
>>> new_list
[2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
{% endhighlight %}

Now let's take a look at how to do this using Python's list comprehension syntax.

{% highlight python %}
>>> new_list = [x * 2 for x in my_list]
>>> new_list
[2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
{% endhighlight %}

## Syntax.

The syntax for list comprehension is based on [set builder notation](http://en.wikipedia.org/wiki/Set-builder_notation). Given the form `[Y for X in LIST]`, `Y` is commonly referred to as the _output function_ , `X` is the _variable_, and `LIST` is the _input set_. This statement says to do `Y` on each `X` in `LIST`.

For an example of using a different _output function_ , let's say say we want a new list that contains each number in `my_list` as a _string_ type...

{% highlight python %}
>>> [str(x) for x in my_list]
['1', '2', '3', '4', '5', '6', '7', '8', '9', '10']
{% endhighlight %}

You may be asking yourself why we wouldn't just use `map()` here:

{% highlight python %}
>>> map(str, my_list)
['1', '2', '3', '4', '5', '6', '7', '8', '9', '10']
{% endhighlight %}

In this example, `map` looks like a good alternative. However, for slightly more complicated requirements, list comprehension can be a bit more concise. For example, when we'd like to specify a _predicate_ .

## The predicate.

Consider our previous example, where we want to create a list of string types for each element in `my_list`, except this time we only want the elements which are even numbers. A typical way to do this would be:

{% highlight python %}
>>> new_list = []
>>> for x in my_list:
...   if (x % 2) == 0:
...     new_list.append(str(x))
... 
>>> new_list
['2', '4', '6', '8', '10']
{% endhighlight %}

In order to use `map()` here we would need to first `filter` the list to exclude the odd numbers.

Using the list comprehension syntax would look like this:

{% highlight python %}
>>> new_list = [str(x) for x in my_list if (x % 2) == 0]
>>> new_list
['2', '4', '6', '8', '10']
{% endhighlight %}

This version introduces the _predicate_, an expression after the list which acts as a filter on which elements get passed to the output function. 

Neat, clear and concise.

## Loops of loops.

Finally, it's worth mentioning that you can use list comprehensions to iterate on more than one list. For example:

{% highlight python %}
>>> list_a = ['A', 'B']
>>> list_b = [1, 2]
>>> [(x, y) for x in list_a for y in list_b]
[('A', 1), ('A', 2), ('B', 1), ('B', 2)]
{% endhighlight %}

Just like you would expect in `for` loops, the last loop moves the fastest. Also note that this method returns a list of `tuples`. If you'd like nested lists, you can also nest one list comprehension within another.

{% highlight python %}
>>> list_a = ['A', 'B']
>>> list_b = ['C', 'D']
>>> [[x+y for x in list_a] for y in list_b]
[['AC', 'BC'], ['AD', 'BD']]
{% endhighlight %}

## Summary.

List comprehension in Python can often provide a neat, clear, and concise syntax for creating lists from other lists. However, one should always be aware that, particularly for complex transformations or predicates, the concise and terse syntax can quickly become very difficult to read. In these cases, it's often beneficial to revert to traditional looping constructs.


## Further reading.

* [Set Builder Notation](http://en.wikipedia.org/wiki/Set-builder_notation)
* [PEP 202 -- List Comprehensions](http://www.python.org/dev/peps/pep-0202/)
* [Python Patterns - An Optimization Anecdote](https://www.python.org/doc/essays/list2str/)
* [Python Performance Tips / Loops](http://wiki.python.org/moin/PythonSpeed/PerformanceTips#Loops)
