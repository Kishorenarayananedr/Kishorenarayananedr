n = int(input())
prices = [int(x) for x in input().split()]
a = maximum_profit(n, prices)
print(a)
def maximum_profit(n, prices):
    if n <= 1:
        return 0  # If there's only 1 day or no days, no profit can be made.

    min_price = float('inf')
    max_profit = 0

    for price in prices:
        # Update the minimum price encountered so far.
        if price < min_price:
            min_price = price
        
        # Calculate the potential profit if selling at the current price.
        profit = price - min_price
        
        # Update the maximum profit.
        if profit > max_profit:
            max_profit = profit

    return max_profit
