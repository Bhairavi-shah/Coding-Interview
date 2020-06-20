Overlapping Subproblems
=======================

A problem has overlapping subproblems if finding its solution involves solving the same subproblem multiple times.

Eg. Fibonacci sequence (where each number is the sum of the two previous ones - 0, 1, 1, 2, 3, 5, 8, ...)

```python
def fib(n):
    if n == 0 or n == 1:
        return n
    return fib(n - 1) + fib(n - 2)
```

fib(n-1) and fib(n-2) are subproblems of fib(n)
