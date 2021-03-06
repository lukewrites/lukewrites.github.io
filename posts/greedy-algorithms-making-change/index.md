<!--
.. title: Greedy Algorithms: Making Change
.. slug: greedy-algorithms-making-change
.. date: 2016-07-17 17:40:32 UTC-07:00
.. tags:
.. category: Algorithms
.. link:
.. description: Three ways to solve a "greedy" problem…two of which are greedy algorithms.
.. type: text
-->

In this week's installment of my Coursera class on Algorithms, we've been introduced to "greedy" algorithms. One of the homework requires us to solve a tried and tested greedy problem: determining the least number of coins needed to change money.

My first answer to this question wasn't actually a greedy algorithm…but it was only one line:

```python
def get_change(num):
    return (num % 5 + ((num - (num % 5)) % 10 // 5) + ((num - (num % 10)) // 10))
```

Which adds up the constituent ones, fives, and tens of the number. [Here's the code on PythonTutor](http://www.pythontutor.com/visualize.html#code=def+get_change(num%29%3A%0A++++return+(num+%25+5+%2B+((num+-+(num+%25+5%29%29+%25+10+//+5%29+%2B+((num+-+(num+%25+10%29%29+//+10%29%29%0A++++%0Aget_change(6%29&mode=display&origin=opt-frontend.js&cumulative=false&heapPrimitives=false&textReferences=false&py=3&rawInputLstJSON=%5B%5D&curInstr=4)). While this code passed all the tests, it is neither readable nor greedy. So, back to the drawing board.

Next, I wrote a function that took two variables: the amount (`num`) and number of coins (`coins`):

```python
def get_change(m, coins):

    while m:
        if m - 10 >= 0:
            m -= 10
            coins += 1
            return get_change(m, coins)
        if m - 5 >= 0:
            m -= 5
            coins += 1
            return get_change(m, coins)
        if m - 1 >= 0:
            m -= 1
            coins += 1
            return get_change(m, coins)

    return coins
```

Ho there, recursion! The program keeps calling itself, stating the amount of money (`m`) remaining and the number of coins each time. This also wound up being about twice as fast as my first version of the code: in the online grader, the first version of the code took .04 seconds, while the second iteration took just .02 seconds. Pretty good! [Here's the code on PythonTutor](http://www.pythontutor.com/visualize.html#code=def+get_change(m%29%3A%0A++++coins+%3D+0%0A%0A++++while+m%3A%0A++++++++if+m+-+10+%3E%3D0%3A%0A++++++++++++m+-%3D+10%0A++++++++++++coins+%2B%3D+1%0A++++++++++++return+get_change(m%29%0A++++++++if+m+-+5+%3E%3D+0%3A%0A++++++++++++m+-%3D+5%0A++++++++++++coins+%2B%3D+1%0A++++++++++++return+get_change(m%29%0A++++++++if+m+-+1+%3E%3D+0%3A%0A++++++++++++m+-%3D+1%0A++++++++++++coins+%2B%3D+1%0A++++++++++++return+get_change(m%29%0A%0A++++return+coins%0A++++%0Aget_change(6%29&mode=display&origin=opt-frontend.js&cumulative=false&heapPrimitives=false&textReferences=false&py=3&rawInputLstJSON=%5B%5D&curInstr=0)); it takes 26 steps to find how many coins are needed to change six cents.

That's fine, but I wanted to see if I could do it without that second variable. And whaddayaknow, I could.

```python
def get_change(m):

    coins = 0

    while m:
        while m - 10 >= 0:
            m -= 10
            coins += 1
        while m - 5 >= 0:
            m -= 5
            coins += 1
        while m - 1 >= 0:
            m -= 1
            coins += 1

    return coins
```

That just seems much cleaner and more readable, doesn't it? [Looking at it on PythonTutor](http://www.pythontutor.com/visualize.html#code=def+get_change(m%29%3A%0A%0A++++coins+%3D+0%0A%0A++++while+m%3A%0A++++++++while+m+-+10+%3E%3D+0%3A%0A++++++++++++m+-%3D+10%0A++++++++++++coins+%2B%3D+1%0A++++++++while+m+-+5+%3E%3D+0%3A%0A++++++++++++m+-%3D+5%0A++++++++++++coins+%2B%3D+1%0A++++++++while+m+-+1+%3E%3D+0%3A%0A++++++++++++m+-%3D+1%0A++++++++++++coins+%2B%3D+1%0A%0A++++return+coins%0A++++%0Aget_change(6%29&mode=display&origin=opt-frontend.js&cumulative=false&heapPrimitives=false&textReferences=false&py=3&rawInputLstJSON=%5B%5D&curInstr=0)), it only takes 17 steps to solve `get_change(6)` – much more efficient than my second attempt! In the online grader this third iteration ran slightly more efficiently, using 4 MB less memory than the second iteration taking the same amount of time.

###What I Would Do Next
Next steps for the above? If I were to come back to this assignment, I'd work to make the code reusable. Right now it is built to work with pennies, nickels, and dimes. It would be an idea to allow the user to enter an amount and a list of coin values that could be used to determine how many coins are needed to make change.
