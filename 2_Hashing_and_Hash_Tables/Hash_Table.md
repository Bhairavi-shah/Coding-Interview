Hash Table
==========

- It is a data structure
- aka. hash, hash map, map, unordered map, dictionary
- It organizes data so you can quickly look up values for a given key

### Advantages
1. Fast lookups
2. Flexible keys

### Disadvantages
1. Slow worst-case lookups
2. Unordered
3. Single-directional lookups
4. Not cache-friendly

|               | Average Case    | Worst Case    |
| ------------- |:-------------:|:-------------:|
| space         | O(n)          | O(n)          |
| lookup        | O(1)          | O(n)          |
| insert        | O(1)          | O(n)          |
| delete        | O(1)          | O(n)          |

##### Example

```python
#Called dictionaries in python
light_bulb_to_hours_of_light = {
    'incandescent': 1200,
    'compact fluorescent': 10000,
    'LED': 50000,
}
```

Hash maps are built on arrays
-----------------------------

- Keys are called "indices"
- In arrays keys are always sequential
- Hash map has flexible keys

A function called a **hashing function** converts a key into an array index

Hash collisions
---------------

- When two or more keys map to the same index

#### Strategies to deal with them :

1. Each array slot can hold a pointer to a linked list, holding the values for all the keys that hash to that index
2. Use better hashing functions

Sets
----

Hash map except it only stores keys, without values

##### Example

```python
light_bulbs = set()

light_bulbs.add('incandescent')
light_bulbs.add('compact fluorescent')
light_bulbs.add('LED')

'LED' in light_bulbs  # True
'halogen' in light_bulbs  # False
```
