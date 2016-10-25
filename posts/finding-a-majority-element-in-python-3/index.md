<!-- 
.. title: Finding a Majority Element in Python 3
.. slug: finding-a-majority-element-in-python-3
.. date: 2016-10-24 23:05:17 UTC-07:00
.. tags: 
.. category: Python
.. link: 
.. description: Find a majority element in a list of numbers using collections.Counter
.. type: text
-->

Doing more data structure work; asked to find if an array of numbers has a _majority element_ – that is, an element that appears more than 50% of the time in the array.

My assignment is to write a greedy algorithm to do this…but wouldn't it be easier to just use the `collections` module?

```python
from collections import Counter

def majority_element_finder(numbers):
	return Counter(numbers).most_common()[0][1] > (len(numbers) // 2)
```

The `most_common([n])` returns a list of tuples of the elements in `numbers` along with the number of times each appears. This is listed in decreasing order. We want to take the first element's (`[0]`) count ('[1]'), and see if it's greater than half the length of the list.