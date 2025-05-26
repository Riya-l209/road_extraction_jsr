# ✨ Day 9 - 160 Days of Code (GFG) ✨

## Problem: Minimize the Heights II  
**Link:** [Minimize the Heights II - GFG](https://www.geeksforgeeks.org/problems/minimize-the-heights-ii/1)  
**Difficulty:** Medium  
**Points:** 4  
**Avg Time to Solve:** 25 mins  
**Status:** ✅ Solved

---

## 📘 Problem Statement:
Given an array `arr[]` representing the heights of `N` towers and an integer `K`, you need to **modify each tower height exactly once** by either:
- Increasing it by `K`, or
- Decreasing it by `K`  
(while ensuring that no resulting height is negative)

**Objective:**  
Minimize the difference between the maximum and minimum heights of the towers after modification.

---

## 🔍 Examples:

### Example 1:
Input: K = 2, arr[] = [1, 5, 8, 10]
Output: 5
Explanation: Modified array: [3, 3, 6, 8]
Max = 8, Min = 3 => Difference = 5

### Example 2:
Input: K = 3, arr[] = [3, 9, 12, 16, 20]
Output: 11

---

## ✅ Java Solution:
```java
class Solution {
    int getMinDiff(int[] arr, int k) {
        int n = arr.length;
        java.util.Arrays.sort(arr);
        int ans = arr[n - 1] - arr[0];
        int small = arr[0] + k;
        int big = arr[n - 1] - k;

        for (int i = 1; i < n; i++) {
            if (arr[i] - k < 0) continue;

            int min = Math.min(small, arr[i] - k);
            int max = Math.max(big, arr[i - 1] + k);
            ans = Math.min(ans, max - min);
        }

        return ans;
    }
}

✨ Key Takeaways:
Sorting helps to evaluate increasing/decreasing patterns clearly.
Focused on smart boundary comparisons instead of brute force.
The greedy approach helped reduce unnecessary recalculations.

