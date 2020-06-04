Array
=====

An array organizes items sequentially, one after another in memory.

Each position in the array has an **index**, starting at 0.

|               | Worst Case    |
| ------------- |:-------------:|
| space         | O(n)          |
| lookup        | O(1)          |
| append        | O(1)          |
| insert        | O(n)          |
| delete        | O(n)          |

#### Strengths
1. **Fast lookups**, regardless of array length
2. **Fast appends**

#### Weaknesses
1. **Fixed size**
2. **Costly inserts and deletes**

```java
// instantiate an array that holds 10 integers
int gasPrices[] = new int[10];

gasPrices[0] = 346;
gasPrices[1] = 360;
gasPrices[2] = 354;
```

Insertion
---------

- If we want to insert, we have to shift all other elements to make space for the new element.

- Worst case: Insertion at 0th index, we have to move all elements in the array => **O(n)** time


Deletion
--------

- Once we delete the element, we have to shift all elements after it.

- In the worst case, we're deleting the 0th item in the array, so we have to shift everything else in the array => **O(n)** time
