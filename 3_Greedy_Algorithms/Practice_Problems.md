Question 1
==========

    Apple Stocks - How much money could have been made yesterday if I'd been trading Apple stocks all day.

    So I grabbed Apple's stock prices from yesterday and put them in a list called stock_prices, where:

    The indices are the time (in minutes) past trade opening time, which was 9:30am local time.
    The values are the price (in US dollars) of one share of Apple stock at that time.
    So if the stock cost $500 at 10:30am, that means stock_prices[60] = 500.

    Write an efficient function that takes stock_prices and returns the best profit I could have made from one purchase and one sale of one share of Apple stock yesterday.

###### Note: No "shorting"—you need to buy before you can sell. Also, you can't buy and sell in the same time step—at least 1 minute has to pass.

Solution 1
==========

```python
def get_max_profit(stock_prices):
    profit = 0
    start_at = []
    stop_at = []
    for i in range(len(stock_prices)-1):
        if stock_prices[i] < stock_prices[i+1] and len(start_at) == len(stop_at):
            start_at += [i, ]
            continue
        if stock_prices[i] > stock_prices[i+1] and len(start_at) != len(stop_at):
            stop_at += [i, ]
    for i in range(len(start_at)):
        profit += stock_prices[stop_at[i]] - stock_prices[start_at[i]]
    return profit
            
        
print(get_max_profit([10, 7, 5, 8, 11, 9]))
#Prints 6

print(get_max_profit([10, 7, 5, 8, 11, 9, 2, 5, 3]))
#Prints 9
```

Question 2
==========

    Given a list of integers, find the highest product you can get from three of the integers.

    The input list_of_ints will always have at least three integers.

Solution 2
==========

```python
def highest_product_of_3(list_of_ints):
    if len(list_of_ints) < 3:
        raise ValueError('Less than 3 items!')

    highest = max(list_of_ints[0], list_of_ints[1])
    lowest  = min(list_of_ints[0], list_of_ints[1])
    highest_product_of_2 = list_of_ints[0] * list_of_ints[1]
    lowest_product_of_2  = list_of_ints[0] * list_of_ints[1]

    highest_product_of_3 = list_of_ints[0] * list_of_ints[1] * list_of_ints[2]

    for i in xrange(2, len(list_of_ints)):
        current = list_of_ints[i]
        highest_product_of_3 = max(highest_product_of_3, current * highest_product_of_2,current * lowest_product_of_2)
        highest_product_of_2 = max(highest_product_of_2, current * highest, current * lowest)
        lowest_product_of_2 = min(lowest_product_of_2, current * highest, current * lowest)
        highest = max(highest, current)
        lowest = min(lowest, current)
    return highest_product_of_3

print(get_max_triproduct([1,2,3])) 
#Prints 6 #ie, 3*2*1

print(get_max_triproduct([1,2,3,4,5])) 
#Prints 60 #ie, 5*4*3

print(get_max_triproduct([63, 20, 10, 2, 30])) 
#Prints 37800 #ie, 63*30*20
```