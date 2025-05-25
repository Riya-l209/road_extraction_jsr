# ✅ Day 8 - GFG 160 Days Challenge

**Problem:** [Stock Buy and Sell - Max one Transaction Allowed](https://www.geeksforgeeks.org/problems/stock-buy-and-sell-1587115621/1)  
**Difficulty:** Easy  
**Points:** 2  
**Average Time:** 10 mins

---

## 🧠 Problem Statement
Given an array `prices[]` of length `n`, representing the prices of the stocks on different days.  
The task is to find the maximum profit possible by buying and selling stocks on different days **when only one transaction is allowed**.  
One transaction means 1 buy + 1 sell.  
**Note:** Stock must be bought before it is sold.

---

## ✨ Example 1:
Input: prices[] = [7, 10, 1, 3, 6, 9, 2]
Output: 8
Explanation: Buy at 1, sell at 9 => 9 - 1 = 8.

## ✨ Example 2:
Input: prices[] = [7, 6, 4, 3, 1]
Output: 0
Explanation: No profit possible.

---

## ✅ My Java Solution
```java
class Solution {
    public int maximumProfit(int prices[]) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;

        for (int price : prices) {
            if (price < minPrice) {
                minPrice = price;
            } else if (price - minPrice > maxProfit) {
                maxProfit = price - minPrice;
            }
        }

        return maxProfit;
    }
}

✅ What I Learned:
Use a greedy strategy for maximum efficiency.
Keep track of the minimum price so far to calculate the profit in a single pass.
Simple condition checks help avoid unnecessary loops.