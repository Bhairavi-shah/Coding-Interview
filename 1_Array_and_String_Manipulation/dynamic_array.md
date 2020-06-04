Dynamic Array
=============

aka :

    1. array list
    2. growable array
    3. resizable array
    4. mutable array

A dynamic array is an array with a big improvement: automatic resizing.

A dynamic array expands as you add more elements. So you don't need to determine the size ahead of time.

### Advantages

1. Fast lookups  
2. Variable size
3. Cache-friendly

### Disadvantages

1. Slow worst-case appends
2. Costly inserts and deletes
  
|               | Average Case    | Worst Case    |
| ------------- |:-------------:|:-------------:|
| space         | O(n)          | O(n)          |
| lookup        | O(1)          | O(1)          |
| append        | O(1)          | O(n)          |
| insert        | O(n)          | O(n)          |
| delete        | O(n)          | O(n)          |

