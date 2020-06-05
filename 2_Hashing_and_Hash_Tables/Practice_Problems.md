Question 1
==========

    You've built an inflight entertainment system with on-demand movie streaming.

    Users on longer flights like to start a second movie right when their first one ends, but they complain that the plane usually lands before they can see the ending. So you're building a feature for choosing two movies whose total runtimes will equal the exact flight length.

    Write a function that takes an integer flight_length (in minutes) and a list of integers movie_lengths (in minutes) and returns a boolean indicating whether there are two numbers in movie_lengths whose sum equals flight_length.

    When building your function:

    Assume your users will watch exactly two movies
    Don't make your users watch the same movie twice
    Optimize for runtime over memory

Solution 1
==========

```python
def can_two_movies_fill_flight(movie_lengths, flight_length):
    # Movie lengths we've seen so far
    movie_lengths_seen = set()

    for first_movie_length in movie_lengths:
        matching_second_movie_length = flight_length - first_movie_length
        if matching_second_movie_length in movie_lengths_seen:
            return True
        movie_lengths_seen.add(first_movie_length)

    # We never found a match, so return False
    return False
```

Question 2
==========

    Write an efficient function that checks whether any permutation ↴ of an input string is a palindrome. ↴

###### You can assume the input string only contains lowercase letters.

##### Examples:

    "civic" should return True
    "ivicc" should return True
    "civil" should return False
    "livci" should return False

Solution 2
==========

```python
def has_palindrome_permutation(the_string):
    # Track characters we've seen an odd number of times
    unpaired_characters = set()

    for char in the_string:
        if char in unpaired_characters:
            unpaired_characters.remove(char)
        else:
            unpaired_characters.add(char)

    # The string has a palindrome permutation if it
    # has one or zero characters without a pair
    return len(unpaired_characters) <= 1

print(has_palindrome_permutation("civic"))
#Prints True

print(has_palindrome_permutation("ivicc"))
#Prints True

print(has_palindrome_permutation("civil"))
#Prints False

print(has_palindrome_permutation("livci"))
#Prints False

```

Question 3
==========

    You want to build a word cloud, an infographic where the size of a word corresponds to how often it appears in the body of text.

    To do this, you'll need data. Write code that takes a long string and builds its word cloud data in a dictionary, where the keys are words and the values are the number of times the words occurred.

##### Think about capitalized words. For example, look at these sentences:

    'After beating the eggs, Dana read the next step:'
    'Add milk and eggs, then add flour and sugar.'

##### What do we want to do with "After", "Dana", and "add"? In this example, your final dictionary should include one "Add" or "add" with a value of 22. Make reasonable (not necessarily perfect) decisions about cases like "After" and "Dana".

###### Assume the input will only contain words and standard punctuation.

Solution 3
==========

```python
def get_count_dict(sentence):
    punc = ".,-()':!?"
    for p in punc:
        sentence = sentence.replace(p,' ')
    sentence = sentence.lower()    
    words = sentence.split(" ")
    count = {}
    for word in words:
        if word not in count.keys():
            count[word] = 1
        else:
            count[word] += 1
    try:
        count.pop('')    
    except KeyError:
        pass
    return(count)
    
print(get_count_dict("We came, we saw, we conquered...then we ate Bill's (Mille-Feuille) cake."))
#Prints {'we': 4, 'came': 1, 'saw': 1, 'conquered': 1, 'then': 1, 'ate': 1, 'bill': 1, 's': 1, 'mille': 1, 'feuille': 1, 'cake': 1}
```

Question 4
==========

    You created a game that is more popular than Angry Birds.

    Each round, players receive a score between 0 and 100, which you use to rank them from highest to lowest. So far you're using an algorithm that sorts in O(n\lg{n})O(nlgn) time, but players are complaining that their rankings aren't updated fast enough. You need a faster sorting algorithm.

    Write a function that takes:

    1. a list of unsorted_scores
    2. the highest_possible_score in the game
    and returns a sorted list of scores in less than O(n\lg{n})O(nlgn) time.

##### For example:

```python
unsorted_scores = [37, 89, 41, 65, 91, 53]
HIGHEST_POSSIBLE_SCORE = 100

sort_scores(unsorted_scores, HIGHEST_POSSIBLE_SCORE)
# Returns [91, 89, 65, 53, 41, 37]
```

Solution 4
==========

#### We use counting sort.

```python
def sort_scores(unsorted_scores, highest_possible_score):
    # List of 0s at indices 0..highest_possible_score
    score_counts = [0] * (highest_possible_score+1)

    # Populate score_counts
    for score in unsorted_scores:
        score_counts[score] += 1

    # Populate the final sorted list
    sorted_scores = []

    # For each item in score_counts
    for score in xrange(len(score_counts) - 1, -1, -1):
        count = score_counts[score]

        # For the number of times the item occurs
        for time in xrange(count):
            # Add it to the sorted list
            sorted_scores.append(score)

    return sorted_scores

print(sort_scores([37, 89, 41, 65, 91, 53], 100))
#Prints [91, 89, 65, 53, 41, 37]

```