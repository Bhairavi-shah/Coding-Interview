Binary Search Algorithm
=======================

- A binary search algorithm finds an item in a sorted list in O(lg(n)) time
  
### Steps:

1. Start with the middle number: is it bigger or smaller than our target number?
   Since the list is sorted, this tells us if the target would be in the left half or the right half of our list. 
2. We've effectively divided the problem in half
   We can "rule out" the whole half of the list that we know doesn't contain the target number
3. Repeat the same approach (of starting in the middle) on the new half-size problem
   Then do it again and again, until we either find the number or "rule out" the whole set

```python
def binary_search(target, nums):
    floor_index = -1
    ceiling_index = len(nums)

    while floor_index + 1 < ceiling_index:
        distance = ceiling_index - floor_index
        half_distance = distance / 2
        guess_index = floor_index + half_distance
        guess_value = nums[guess_index]
        if guess_value == target:
            return True
        if guess_value > target:
            ceiling_index = guess_index
        else:
            floor_index = guess_index
    return False
```
