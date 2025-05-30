# 📅 Day 12: Max Circular Subarray Sum

## 📝 Problem Statement

Given an array of integers `arr[]` in a **circular** fashion, find the **maximum subarray sum**. The array is considered **circular**, which means the subarray can **wrap around** from the end to the beginning of the array.

---

## 🔗 Problem Link

[GeeksforGeeks - Max Circular Subarray Sum](https://www.geeksforgeeks.org/problems/max-circular-subarray-sum-1587115620/1)

---

## 📌 Constraints

- `1 ≤ N ≤ 10^5`
- `-10^5 ≤ Arr[i] ≤ 10^5`

---

## 🧪 Examples

### Example 1
**Input:**  
`arr[] = [8, -8, 9, -9, 10, -11, 12]`  
**Output:**  
`22`  
**Explanation:**  
Max circular subarray is `[12, 8, -8, 9, -9, 10]` which gives sum = `22`.

---

### Example 2  
**Input:**  
`arr[] = [10, -3, -4, 7, 6, 5, -4, -1]`  
**Output:**  
`23`  
**Explanation:**  
Max circular subarray is `[7, 6, 5, -4, -1, 10]` with sum = `23`.

---

### Example 3  
**Input:**  
`arr[] = [-1, 40, -14, 7, 6, 5, -4, -1]`  
**Output:**  
`52`  
**Explanation:**  
Max circular subarray is `[7, 6, 5, -4, -1, -1, 40]` = `52`.

---

## ✅ Approach: Modified Kadane’s Algorithm (for Circular Arrays)

### 🎯 Goal

We want to find the **maximum sum subarray** either:
1. In a **normal way** (without wrap around), or
2. In a **circular fashion** (wrap around end-to-start)

We'll calculate both and return the **maximum** of the two.

---

## 🧠 Intuition

- The **normal maximum subarray sum** can be found using **Kadane’s Algorithm**.
- For **circular max subarray**, we use this trick:
  > Circular max sum = `Total Sum of Array - Minimum Subarray Sum`

This is because **excluding** the minimum subarray from the total gives the maximum circular subarray.

---

## 🧩 Steps Involved

1. Initialize:
   - `totalSum = 0`
   - `maxSum = arr[0]`, `curMax = 0`
   - `minSum = arr[0]`, `curMin = 0`

2. Traverse the array:
   - Update `curMax = max(arr[i], curMax + arr[i])`
   - Update `maxSum = max(maxSum, curMax)`
   - Update `curMin = min(arr[i], curMin + arr[i])`
   - Update `minSum = min(minSum, curMin)`
   - Add `arr[i]` to `totalSum`

3. If all elements are negative (`maxSum < 0`), return `maxSum`.

4. Otherwise, return `max(maxSum, totalSum - minSum)`

---

## 💻 Java Code

```java
class Solution {
    int circularSubarraySum(int a[]) {
        int totalSum = 0;
        int maxSum = a[0], curMax = 0;
        int minSum = a[0], curMin = 0;

        for (int i = 0; i < a.length; i++) {
            curMax = Math.max(a[i], curMax + a[i]);
            maxSum = Math.max(maxSum, curMax);

            curMin = Math.min(a[i], curMin + a[i]);
            minSum = Math.min(minSum, curMin);

            totalSum += a[i];
        }

        if (maxSum < 0) {
            return maxSum;
        }

        return Math.max(maxSum, totalSum - minSum);
    }
}
