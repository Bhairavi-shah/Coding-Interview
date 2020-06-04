Array Slicing
=============

It involves taking a **subbset from an array** and allocating a new array with those elements

##### Examples

```python
  my_list[start_index:end_index]
```

```python
  my_list[start_index:]
```

Hidden time & space cost!
-------------------------

Slicing is not just _getting elements_, in reality you are:

    1. allocating a new list
    2. copying the elements from the original list to the new list

This takes (Where n is the number of elements in the resulting list):

- O(n) time
- O(n) space
