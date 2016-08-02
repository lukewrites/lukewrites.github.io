<!--
.. title: Fun with Python 3's print function
.. slug: fun-with-python-3s-print-function
.. date: 2016-07-20 10:17:23 UTC-07:00
.. tags:
.. category: Python
.. link:
.. description: Python3's `print` function can do more than just output text.
.. type: text
-->

# Fun with the `print` function

Most Pythonistas learn early on that the `print` function can evaluate statements:

```python
print(2>3)
>>> False
print(7+5==12)
>>> True
```

However, I didn't know that `print` can return different strings based upon whether or not the following statement is true or false. The format is:
```python
print(['output for False', 'output for True']['statement_to_evaluate'])
```

For example:

```python
print(['no', 'yes'][2 > 3])
>>> no

print(['Go back to math class', 'You know math!'][7 + 5 == 12])
>>> You know math!
```
