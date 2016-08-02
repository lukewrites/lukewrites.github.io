<!--
.. title: The difference between list.sort and sorted(list) in Python 3
.. slug: the-difference-between-listsort-and-sortedlist-in-python-3
.. date: 2016-07-20 21:08:50 UTC-07:00
.. tags:
.. category: Python
.. link:
.. description: Why does python have a li.sort() method and a sorted(li) function? They have different uses.
.. type: text
-->

The other week for my [algorithms class](http://coursera.org/learn/algorithmic-toolbox/) I needed to find the minimum dot product of a list. My first try at a solution, which threw an error, was this:

```python
def min_dot_product(a, b, n):
    a = sorted(a)
    b = sorted(b, reverse=True)
    res = 0
    for i in range(n):
        res += a[i] * b[i]
    return res
```

Python has two different ways of sorting a list: `list.sort([reverse=False])` and `sorted(list[, reverse=False])`. Why a method and a function to do the same thing? Let's look:

```python
li = [5, 1, 4, 3, 2]
li.sort()
li
>>> [1, 2, 3, 4, 5]
li.sort(reverse=True)
li
>>> [5, 4, 3, 2, 1]
```
`list.sort()` sorts the list and **returns None**.

On the other hand, `sorted(list)` sorts and **returns the list**

```python
li = [5, 1, 4, 3, 2]
sorted(li, reverse=True)
>>> [5, 4, 3, 2, 1]
```

I've contributed the above to [SO's Python documentation on lists and list methods](http://stackoverflow.com/documentation/python/209/list/2035/list-methods-and-supported-operators#t=201607281859094153184).
