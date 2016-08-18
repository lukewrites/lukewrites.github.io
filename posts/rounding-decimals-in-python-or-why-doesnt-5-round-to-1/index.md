<!--
.. title: Rounding decimals in Python (or: Why doesn't .5 round to 1?)
.. slug: rounding-decimals-in-python-or-why-doesnt-5-round-to-1
.. date: 2016-07-28 11:37:30 UTC-07:00
.. tags:
.. category: Python
.. link:
.. description: Why doesn't Python round .5 up to the nearest whole number? Here's why and here's how to do it.
.. type: text
-->

Doing my morning Hacker Rank puzzle this morning, I discovered Python 3 doesn't round numbers ending in .5 the way I'd expect:

```python3
int(12.5)
>>> 12
int(13.5)
>>> 14
round(12.5)
>>> 12
round(13.5)
>>> 14
```

<banging head against the wall gif goes here>

As always, [Stack Overflow had the answer](http://stackoverflow.com/a/10093820/3389827): Python rounds .5 down _sometimes_ because of [Banker's Rounding](https://en.wikipedia.org/wiki/Rounding#Round_half_to_even), also known by the much more informative name "Round Half To Even". Python will round `.5` numbers to the nearest even whole.

In the problem I was solving (giving a rounded total cost of a meal), this didn't work, so I had to use `decimal.Decimal`'s `quantize` method to round up:

```python
from decimal import Decimal

mc = float(input())  # these unpythonic variable names came from HackerRank
tp = int(input())
tax = int(input())

def totalCost(mc, tp, tax):
    total = Decimal(mc + (tp / 100 * float(mc)) + ((tax / 100 * float(mc)))).quantize(Decimal('1'))
    print("The total meal cost is {} dollars.".format(total))

totalCost(mc, tp, tax)
```

I'm over 80 characters in that line, so there's the potential for refactoring.
