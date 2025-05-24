# 💹 Day 7 - Stock Buy and Sell (Multiple Transactions Allowed)

**Difficulty:** Medium  
**Average Time:** 10 mins  
**Platform:** GeeksforGeeks  
**Points Earned:** 4 ✅

---

## 📘 Problem Statement:

The cost of stock on each day is given in an array `price[]`. Each day, you may **buy** and/or **sell** the stock, but:
- You must sell the stock **only if you have it**.
- You **cannot hold multiple stocks** at once.
- You **can buy and sell on the same day**.

> Find the **maximum profit** you can earn.

---

## 🧾 Example:

### Input:
```java
prices[] = [100, 180, 260, 310, 40, 535, 695]
Output:
865

Explanation:
Buy at 100, sell at 310 → Profit = 210
Buy at 40, sell at 695 → Profit = 655
Total = 210 + 655 = 865

📌 Constraints:
1 ≤ prices.length ≤ 10⁶
0 ≤ prices[i] ≤ 10⁴

🧠 Approach:
Traverse the price array.
If price is increasing, add the difference (today - yesterday) to the profit.
This simulates buying yesterday and selling today to gain the profit chunk.
Final profit is the sum of all such positive changes.

⏱️ Time and Space Complexity:
Time Complexity: O(n)
Space Complexity: O(1)

👨‍💻 Code (Java):
java
class Solution {
    public int maximumProfit(int[] prices) {
        int profit = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1]) {
                profit += prices[i] - prices[i - 1];
            }
        }
        return profit;
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        int[] prices1 = {100, 180, 260, 310, 40, 535, 695};
        int[] prices2 = {4, 2, 2, 2, 4};
        System.out.println(sol.maximumProfit(prices1)); // Output: 865
        System.out.println(sol.maximumProfit(prices2)); // Output: 2
    }
}

✅ Output for Test Cases:
Input:  [100, 180, 260, 310, 40, 535, 695]
Output: 865

Input:  [4, 2, 2, 2, 4]
Output: 2

📚 What I Learned:
Learned how to implement profit-maximization logic using greedy strategy.
Practiced condition-based addition to track potential gains.
Improved loop logic for stock market-based problems.

