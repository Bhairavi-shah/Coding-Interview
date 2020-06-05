Question 1
==========

    Your company built an in-house calendar tool called HiCal. You want to add a feature to see the times in a day when everyone is available.

##### To do this, you’ll need to know when any team is having a meeting. In HiCal, a meeting is stored as a tuple of integers (start_time, end_time). These integers represent the number of 30-minute blocks past 9:00am.

##### For example:

```python    
(2, 3)  # Meeting from 10:00 – 10:30 am
(6, 9)  # Meeting from 12:00 – 1:30 pm
```

##### Write a function merge_ranges() that takes a list of multiple meeting time ranges and returns a list of condensed ranges.

##### For example, given:

```python
[(0, 1), (3, 5), (4, 8), (10, 12), (9, 10)]
```

##### your function would return:

```python
[(0, 1), (3, 8), (9, 12)]
```

###### Do not assume the meetings are in order. The meeting times are coming from multiple teams.

    Write a solution that's efficient even when we can't put a nice upper bound on the numbers representing our time ranges. Here we've simplified our times down to the number of 30-minute slots past 9:00 am. But we want the function to work even for very large numbers, like Unix timestamps. In any case, the spirit of the challenge is to merge meetings where start_time and end_time don't have an upper bound.

Solution 1
==========

```python
def merge_ranges(l):
    res = [l[0],]
    for i in range(1, len(l)):
        f = 0
        for j in range(len(res)):
            temp = sorted(list(range(l[i][0], l[i][1]+1))+list(range(res[j][0], res[j][1]+1)))
            if len(temp) != len(set(temp)):
                f = 1
                del(res[j])
                res += [(temp[0],temp[-1]),]                
        if f == 0:
            res+= [l[i]]
    return(res)            

#Sample input/output
merge_ranges([(0, 1), (3, 5), (4, 8), (10, 12), (9, 10)])
#Prints [(0, 1), (3, 8), (9, 12)]

merge_ranges([(1, 2), (2, 3)])
#Prints [(1, 3)]

merge_ranges([(1, 5), (2, 3)])
#Prints [(1, 5)]

merge_ranges([(1, 10), (2, 6), (3, 5), (7, 9)])
#Prints [(1, 10)]
```

Question 2
==========

    Write a function that takes a list of characters and reverses the letters in place.

Solution 2
==========

```python
def reverse(l):
    for i in range(len(l)//2):
        l[i],l[len(l)-1-i] = l[len(l)-1-i], l[i]
    return(l)

#Sample input/output
reverse(['a','b','c'])
[#Prints 'c', 'b', 'a']

reverse(['m','a','l','a','y','a','l','a','m'])
#Prints ['m','a','l','a','y','a','l','a','m']
```

Question 3
==========

    You're working on a secret team solving coded transmissions.

    Your team is scrambling to decipher a recent message, worried it's a plot to break into a major European National Cake Vault. The message has been mostly deciphered, but all the words are backward! Your colleagues have handed off the last step to you.

    Write a function reverse_words() that takes a message as a list of characters and reverses the order of the words in place.

##### Example

```python
message = [ 'c', 'a', 'k', 'e', ' ',
            'p', 'o', 'u', 'n', 'd', ' ',
            's', 't', 'e', 'a', 'l' ]

reverse_words(message)
#Prints ['s', 't', 'e', 'a', 'l', ' ',
#        'p', 'o', 'u', 'n', 'd', ' ',
#        'c', 'a', 'k', 'e']

''.join(message)
#Prints 'steal pound cake'
```

Solution 3
==========

```python
def reverse_words(message):
    # First we reverse all the characters in the entire message
    reverse_characters(message, 0, len(message)-1)

    # This gives us the right word order
    # but with each word backward

    # Now we'll make the words forward again
    # by reversing each word's characters

    # We hold the index of the *start* of the current word
    # as we look for the *end* of the current word
    current_word_start_index = 0

    for i in xrange(len(message) + 1):
        # Found the end of the current word!
        if (i == len(message)) or (message[i] == ' '):
            reverse_characters(message, current_word_start_index, i - 1)
            # If we haven't exhausted the message our
            # next word's start is one character ahead
            current_word_start_index = i + 1


def reverse_characters(message, left_index, right_index):
    # Walk towards the middle, from both sides
    while left_index < right_index:
        # Swap the left char and right char
        message[left_index], message[right_index] = \
            message[right_index], message[left_index]
        left_index  += 1
        right_index -= 1
    
#Sample input/output
reverse_words([ 'c', 'a', 'k', 'e', ' ',
                      'p', 'o', 'u', 'n', 'd', ' ',
                      's', 't', 'e', 'a', 'l' ])
#Prints ['s', 't', 'e', 'a', 'l', ' ', 'p', 'o', 'u', 'n', 'd', ' ', 'c', 'a', 'k', 'e', ' ']

''.join(reverse_words([ 'c', 'a', 'k', 'e', ' ',
                              'p', 'o', 'u', 'n', 'd', ' ',
                              's', 't', 'e', 'a', 'l' ]))
#Prints 'steal pound cake'

```

Question 4
==========

    In order to win the prize for most cookies sold, my friend Alice and I are going to merge our Girl Scout Cookies orders and enter as one unit.

    Each order is represented by an "order id" (an integer).

    We have our lists of orders sorted numerically already, in lists. Write a function to merge our lists of orders into one sorted list.

##### For example:

```python
my_list     = [3, 4, 6, 10, 11, 15]
alices_list = [1, 5, 8, 12, 14, 19]

print merge_lists(my_list, alices_list)
#Prints [1, 3, 4, 5, 6, 8, 10, 11, 12, 14, 15, 19]
```

Solution 4
==========
```python
def merge_lists(my_list, alices_list):
    return sorted(list(set(my_list +alices_list)))

my_list     = [3, 4, 6, 10, 11, 15]
alices_list = [1, 5, 8, 12, 14, 19]

merge_lists(my_list, alices_list)
#Prints [1, 3, 4, 5, 6, 8, 10, 11, 12, 14, 15, 19]
```

Question 5
==========

    My cake shop is so popular, I'm adding some tables and hiring wait staff so folks can have a cute sit-down cake-eating experience.

    I have two registers: one for take-out orders, and the other for the other folks eating inside the cafe. All the customer orders get combined into one list for the kitchen, where they should be handled first-come, first-served.

    Recently, some customers have been complaining that people who placed orders after them are getting their food first. Yikes—that's not good for business!

    To investigate their claims, one afternoon I sat behind the registers with my laptop and recorded:

    The take-out orders as they were entered into the system and given to the kitchen. (take_out_orders)
    The dine-in orders as they were entered into the system and given to the kitchen. (dine_in_orders)
    
    Each customer order (from either register) as it was finished by the kitchen. (served_orders)
    Given all three lists, write a function to check that my service is first-come, first-served. All food should come out in the same order customers requested it.

    We'll represent each customer order as a unique integer.


##### As an example,

```python
Take Out Orders: [1, 3, 5]
Dine In Orders: [2, 4, 6]
Served Orders: [1, 2, 4, 6, 5, 3]
```
##### would not be first-come, first-served, since order 3 was requested before order 5 but order 5 was served first.

##### But,

```python
Take Out Orders: [17, 8, 24]
Dine In Orders: [12, 19, 2]
Served Orders: [17, 8, 12, 19, 24, 2]
```

##### would be first-come, first-served.

Solution 5
==========

```python
def check_order(take_out, dine_in, served):
    if [x for x in served if x in take_out] == take_out and [x for x in served if x in dine_in] == dine_in:
        print("It is first-come, first-served")
    else:
        print("It is not first-come, first-served")
        
check_order([1, 3, 5], [2, 4, 6], [1, 2, 4, 6, 5, 3])
#Prints 'It is not first-come, first-served'

check_order([17, 8, 24], [12, 19, 2], [17, 8, 12, 19, 24, 2])
#Prints 'It is first-come, first-served'
```

