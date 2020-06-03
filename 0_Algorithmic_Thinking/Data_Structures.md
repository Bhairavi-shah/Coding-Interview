Data Structures
===============

1. Random Access Memory
2. Binary Numbers
3. Fixed-Width Integers
4. Arrays
5. Strings
6. Pointers
7. Dynamic Arrays
8. Linked Lists
9. Hash Tables

### Storage

- aka. **Persistent storage** or **disk**
- keep files like mp3s, videos, word documents, executable programs or apps
- Slower
- More Space
- ~500GB storage for a modern laptop
  
Random Access Memory (RAM)
----------------------------

- Variables are stored in RAM (allocated by functions)
- aka. **Working memory** or **memory**
- Faster
- Less Space
- ~16GB RAM for a modern laptop

**Imagine RAM as a** :
  - really tall bookcase 
  - with a lot of shelves (billions)
  - numered starting from the top (0 onwards) - **called address**
  - Each shelf **8 bits** => **1 byte**
  - Each bit => a swicth that can be turned "on" or "off", we say **0 or 1**

**Processor** is connected to a **memory controller**

### Memory Controller

- does the actual reading & writing to and from RAM
- Has a direct connection to each shelf of RAM
- Random Access Memory => we can access the bits at any Random adress in Memory right away (direct connection)
- Sends a handful of nearby memory addresses to the processor too, which get stored in cache memory

### Hard Drives

- no direct connection
- there's a reader - called a **head** - that moves along the surface of a spinning storage disc
- Reading bytes that are far apart takes longer because you have to wait for the head to physically move along the disc

#### Cache Memory
- in the processor
- stores a copy of stuff recently read from RAM
- (actually it has a series of caches - we picture them all lumped together as one)

Binary Numbers
--------------

### Decimal
- Base 10 number system - 0,1,2,3,4,5,6,7,8,9 (digits)
- places in Base 10 are sequential powers of 10
- ie,  
    10<sup>0</sup> = 1  
    10<sup>1</sup> = 10  
    10<sup>2</sup> = 100  
    10<sup>3</sup> = 1000
    etc.

```
Eg : (101)<sub>10</sub>
        100s place => 1  
        10s  place => 0
        1s   place => 1 
    100*(1) + 10*(0) + 1*(1) = 101 (value)
```
#### Binary
- Base 2 number system - 0,1 (bits)
- places in Base 2 are sequential powers of 2
- ie,  
    2<sup>0</sup> = 1  
    2<sup>1</sup> = 2  
    2<sup>2</sup> = 4  
    2<sup>3</sup> = 8
    etc.

```
Eg : (101)<sub>2</sub>
        4s place => 1  
        2s place => 0
        1s place => 1 
    4*(1) + 2*(0) + 1*(1) = 5 (value)
```

### Hexadecimal or Hex
- Base 16 number system - 0,1,2,3,4,5,6,7,8,9,a,b,c,d,e,f 
- Often prefixed with "0x" or "#"


### Unsigned Integers

- non-negative, whole numbers
- stored normally as in example above

### Fractions

- store 2 numbers:
    1. numerator
    2. denominator

### Signed Numbers

- store 2 numbers:
    1. number with decimal point taken out
    2. position where the decimal point goes

### Signed Numbers

- Reserve the leftmost bit for expressing sign of the number
- 0 for positive
- 1 for negative


Fixed-width integers or Fixed-length integers
---------------------------------------------


- Number of bits they take up doesn't change.
- 2<sup>8</ sup> = 256 numbers can be expressed with 1 byte (8bits)
- We use 4-8 bytes usually for storing integers

#### Integer Overflow

If we have a number 255 ie, 1111 1111 in binary and we add 1 to it, we get 1 0000 0000 requiring a 9th bit but we have just 8bits!


Arrays
------

- storing several numbers
- elements of an array are numbered - **index**

```
    address of nth item in array = address of array start + ( n * size of each item in bytes )
```

This formula works only if :  

    1. each item in the array is the same size
    2. array is uninterruptem (contiguous) in memory

#### Advantages:
1. fast lookups, O(1) time
     
#### Constraints:
1. every item must be same size
2. uninterrupted free space in RAM

Strings
-------

- used to store words
- a series of characters (letters, punctuation, etc.) is called a **string**
- we use **character encoding** to map characters to numbers

###### ASCII - Common character encoding scheme

Pointers
--------

- used to storing an array of string
- used to point to other locations

##### Example - Store a bunch of baby names
- Each name is a string - which is an array of encoded letters
- we want to store an array of such strings
- Since, it is difficult to get continuous storage for all these names, we can :
  - store strings (array of letters wherever space is available)
  - store address of all the locations **(pointers)** where the strings are stored as another array (contiguous)
- pointers are marked with a "*" at the beginning

#### Advantages:
1. items don't have to be same length
2. we don't need enough uninterrupted free memory to store all our strings next to each other
     
#### Constraints:
1. Pointers in this array are not cache-friendly => Slower


Dynamic Arrays
--------------

Array programmed to resize itself when it runs out of space OR space allocated during runtime.

### Working

1. When you allocate a dynamic array, an underlying static array is created (size depending on implementation).
2. the point when capacity < size required:
   1. Make a new, bigger array (usually twice as big)
       ##### why not extend the existing array? Because, the memory might already be taken
   2. Copy each element from old array into new array
   3. Free up old array
   4. Append new item

#### Advantages:
1. don't have to specify the size ahead of time

#### Constraints:
1. Appends can be expensive - Single doubling will take O(n) time since we have to copy all n items from old array

Linked Lists
------------

What if each character in our string were a two-index array with:

1. the character itself
2. a pointer to the next character

We would call each of these two-item arrays a **node** and we'd call this series of nodes a **linked list**.

The first node of a linked list is called the **head**, and the last node is usually called the **tail**.

#### Advantages:
1. faster prepends than dynamic arrays

#### Constraints:
1. slower lookups => O(i) time lookups - much slower than O(1)
2. not cache-friendly

Hash tables or Hash map
-----------------------

- Key, value pairs
- The process we used to translate a key into an array index is called a hashing function.

###### hash collision - same key for two different values

#### Advantages:
1. Fast lookups by key

#### Constraints:
1. Looking up the key for a given value still takes O(n) time
2. Hash Collisions
3. Some lookups could be a bit slow


**Each data structure has tradeoffs. You can't have it all.**