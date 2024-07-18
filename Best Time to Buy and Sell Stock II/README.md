# Best Time to Buy and Sell Stock II

## Problem Description

You are given an integer array `prices` where `prices[i]` is the price of a given stock on the `i`th day. On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day. Find and return the maximum profit you can achieve.

## Examples

### Example 1:
**Input:** `prices = [7, 1, 5, 3, 6, 4]`  
**Output:** `7`  
**Explanation:**  
- Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5 - 1 = 4.
- Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6 - 3 = 3.
- Total profit is 4 + 3 = 7.

### Example 2:
**Input:** `prices = [1, 2, 3, 4, 5]`  
**Output:** `4`  
**Explanation:**  
- Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5 - 1 = 4.
- Total profit is 4.

### Example 3:
**Input:** `prices = [7, 6, 4, 3, 1]`  
**Output:** `0`  
**Explanation:**  
- There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.

## Constraints
- `1 <= prices.length <= 3 * 10^4`
- `0 <= prices[i] <= 10^4`

## Solution

To solve this problem, we can use a greedy algorithm. The idea is to take advantage of every increase in stock price. Here are two C implementations of the solution:

### Method 1

This method uses a `buy` variable to track the buying price and calculates the profit whenever there is an opportunity to sell for a higher price.

```c
// This is one way to solve the problem, time about 2ms
int maxProfit(int* prices, int pricesSize) {
    int buy = *(prices);
    int max = 0;
    for(int j=1; j<pricesSize; j++) {
        if(buy < *(prices + j)) {
            max += *(prices + j) - buy;
        }
        buy = *(prices + j);
    }
    return max;
}
```

### Method 2

```c
int maxProfit(int* prices, int pricesSize) {
    int profit=0;
    for(int i=1;i<pricesSize;i++){
        if(prices[i]>prices[i-1]){
            profit+= prices[i]-prices[i-1];
        }
    }
    return profit;
}
```
