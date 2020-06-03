Asymptotic Notation
===================

Time Complexity
---------------

- time cost
- used for measuring how long an algorithm takes to run
- used to compare efficiency of different approaches to a problem

Big O Notation
--------------

How quickly it grows relative to the inpput, as the input gets arbitrarily large.

Used to measure both, time complexity and space complexity.

##### Examples

###### Eg1 : O(1) or **constant time**
###### Would require only one step no matter what size of items is
```python
    def print_first_item(items):
        print(items[0])
```

###### Eg2 : O(n) or **linear time**
###### Loops 'n' times
```python
    def print_all_items(items):
        for item in items:
            print(item)
```
###### Eg3 : O(n<sup>2</sup>) or **quadratic time**
```python
    def print_all_possible_ordered_pairs(items):
        for first_item in items:
            for second_item in items:
                print(first_item, second_item)
```

When calculating big O complexity, constants are ruled out.

eg. O(2n) would become O(n)  
    O(1+n/2+100) would also be O(n)

This is because, we're looking at what happens **as n gets arbitrarily large**.

So, we drop the less significant terms - we talk about the **worst case**.

Space Complexity
================

- optimizing memory
- memory cost
- total size (relative to the size of the input) of any new variables we're allocating

##### Examples

###### Eg1 : O(1) or we use a fixed number of variables
```python
    def say_hi(n):
        for time in xrange(n):
            print("hi")
```

###### Eg2 : O(n)
```python
    def list_of_hi_times(n):
        hi_list = []
        for time in xrange(n):
            hi_list.append("hi")
        return hi_list
```