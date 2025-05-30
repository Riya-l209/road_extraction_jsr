# 📅 Day 13: Smallest Positive Missing Number

## 📝 Problem Statement

You are given an **integer array** `arr[]`. Your task is to **find the smallest positive number** that is **missing** from the array.

> ✅ Note: Positive numbers start from 1. The array can have negative numbers and zero too.

---

## 🔗 Problem Link

[GeeksforGeeks - Smallest Positive Missing Number](https://www.geeksforgeeks.org/problems/smallest-positive-missing-number-1587115621/1)

---

## 📌 Constraints

- `1 ≤ N ≤ 10^5`  
- `-10^6 ≤ arr[i] ≤ 10^6`

---

## 🧪 Examples

### Example 1
**Input:**  
`arr[] = [2, -3, 4, 1, 7]`  
**Output:**  
`3`  
**Explanation:**  
The array has 1, 2, 4, 7 — but **3** is missing.

---

### Example 2
**Input:**  
`arr[] = [5, 3, 2, 5, 1]`  
**Output:**  
`4`  
**Explanation:**  
The array has 1, 2, 3, 5 — but **4** is missing.

---

### Example 3
**Input:**  
`arr[] = [-8, 0, -1, -4, -3]`  
**Output:**  
`1`  
**Explanation:**  
There is no positive number in the array — smallest missing is **1**.

---

## ✅ Approach: Index Mapping Using Cyclic Sort Logic

We aim to place every number `x` (where `1 <= x <= n`) to its correct index `x-1`. After rearrangement:
- If `arr[i] != i + 1`, then the missing number is `i + 1`.

---

## 🧠 Intuition

- If a number is **between 1 and n**, try to put it at index `arr[i] - 1`.
- This results in a **partially sorted array** where each value is at its “expected” index.
- Once done, a **linear scan** reveals the smallest missing positive number.

---

## 🧩 Steps Involved

1. Iterate over the array:
   - While the current element is in range `[1, n]` and **not in its correct place**:
     - Swap it with its correct index value (`arr[arr[i]-1]`)
   - Repeat until no further change possible.

2. Traverse array again:
   - If `arr[i] != i+1`, return `i+1`.

3. If all are in place, return `n+1`.

---

## 💻 Java Code

```java
class Solution {
    int missingNumber(int[] arr) {
        int n = arr.length;
        
        for (int i = 0; i < n; i++) {
            while (arr[i] > 0 && arr[i] <= n && arr[arr[i] - 1] != arr[i]) {
                int temp = arr[i];
                arr[i] = arr[temp - 1];
                arr[temp - 1] = temp;
            }
        }

        for (int i = 0; i < n; i++) {
            if (arr[i] != i + 1) {
                return i + 1;
            }
        }

        return n + 1;
    }
}
