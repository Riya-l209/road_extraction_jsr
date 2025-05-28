# 📅 Day 11: Kadane’s Algorithm - Maximum Subarray Sum

## 📝 Problem Statement
**Kadane’s Algorithm** – Given an integer array `arr[]`, you need to find the **maximum sum of a subarray**.  
A subarray is a contiguous part of the array that may contain one or more elements.

---

## 🔗 Problem Link
[GeeksforGeeks - Kadane’s Algorithm (Maximum Subarray Sum)](https://www.geeksforgeeks.org/problems/kadanes-algorithm-1587115620/1)

---

## 🧠 Understanding the Problem
- You are given an array `arr[]` of integers, which may contain both positive and negative numbers.
- Your task is to find the maximum sum that can be obtained by summing a **contiguous subarray**.
- The subarray must contain **at least one** element.

---

## 📌 Constraints
- `1 ≤ arr.size() ≤ 10^5`
- `-10^9 ≤ arr[i] ≤ 10^4`

---

## 🧪 Examples

### Example 1
**Input:**  
`arr[] = [2, 3, -8, 7, -1, 2, 3]`  
**Output:**  
`11`  
**Explanation:**  
The subarray `[7, -1, 2, 3]` has the largest sum = `11`.

---

### Example 2
**Input:**  
`arr[] = [-2, -4]`  
**Output:**  
`-2`  
**Explanation:**  
The subarray `[-2]` has the largest sum `-2`.

---

### Example 3
**Input:**  
`arr[] = [5, 4, 1, 7, 8]`  
**Output:**  
`25`  
**Explanation:**  
The subarray `[5, 4, 1, 7, 8]` has the largest sum `25`.

---

## ✅ Approach: Kadane’s Algorithm
Kadane's Algorithm is used to solve this problem in linear time using dynamic programming.
### 🎯 Goal
Find the maximum sum that can be obtained from a **contiguous subarray**.

---

## 🧩 Steps Involved

1. Initialize two variables:
   - `currMax = arr[0]` → holds the **current subarray sum**
   - `maxSoFar = arr[0]` → holds the **maximum found so far**
2. Traverse the array from index `1` to `n - 1`
3. At each step:
   - Either extend the existing subarray OR start a new subarray from current index
   - `currMax = max(arr[i], currMax + arr[i])`
   - `maxSoFar = max(maxSoFar, currMax)`
4. Finally, return `maxSoFar`

---

## 💻 Java Code

```java
class Solution {
    int maxSubarraySum(int[] arr) {
        int maxSoFar = arr[0];
        int currMax = arr[0];

        for (int i = 1; i < arr.length; i++) {
            currMax = Math.max(arr[i], currMax + arr[i]);
            maxSoFar = Math.max(maxSoFar, currMax);
        }

        return maxSoFar;
    }
}

⏱️ Time and Space Complexity
Time Complexity: O(n)
Space Complexity: O(1)
Kadane’s algorithm is optimal and runs in linear time with constant space.

📤 Input Format
A single array of integers, arr[], where 1 <= arr.length <= 10^5.

📥 Output Format
A single integer, representing the maximum subarray sum.

🧪 Sample Test Case
Input:
arr = [2, 3, -8, 7, -1, 2, 3]
Output:
11
