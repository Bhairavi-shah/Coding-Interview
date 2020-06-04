In-Place Algorithms 
===================

An **in-place** function/algorithm, **modifies data structures or objects outside of its own stack frame**.

Because of this, the changes made by the function remain after the call completes.

They are aka **destructive** algorithms, because the original input is destroyed/modified during the function call

in-place function
-----------------

- without creating a new copy of the input but they can be creating additional variables that are O(1) space
- Used only when space constrained, or when original input is not required anymore, not even for debugging

##### Example
```python
def square_list_in_place(int_list):
    for index, element in enumerate(int_list):
        int_list[index] *= element
        # no need to return anything - we modified
        # int_list in place
```
### Advantage
- save time and space

### Disadvantage
- input is "destroyed" or "altered" which can affect code outside the function
##### Example
```python
original_list = [2, 3, 4, 5]
square_list_in_place(original_list)

print "original list: %s" % original_list
# Prints: original list: [4, 9, 16, 25], confusingly!
```


out-of-place function
---------------------

- copy any data structures or objects before manipulating and changing them (Hence, changes are not visible to other functions)

##### Example
```python
def square_list_out_of_place(int_list):
    # We allocate a new list with the length of the input list
    squared_list = [None] * len(int_list)

    for index, element in enumerate(int_list):
        squared_list[index] = element ** 2

    return squared_list
```
### Advantage
- considered safer, because no side-effects