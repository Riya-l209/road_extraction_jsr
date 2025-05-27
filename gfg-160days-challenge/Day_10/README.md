# Day 10: Maximum Product Subarray

## Problem Statement
Given an array `arr[]` that contains positive and negative integers (may contain 0 as well), find the **maximum product** that can be obtained from a **subarray** of `arr[]`.
> Note: The output is guaranteed to fit in a 32-bit integer.

---

### Examples

#### Example 1
**Input:**  
`arr[] = [-2, 6, -3, -10, 0, 2]`  
**Output:**  
`180`  
**Explanation:**  
The subarray with the maximum product is `{6, -3, -10}`.  
Product = `6 * (-3) * (-10) = 180`.

#### Example 2
**Input:**  
`arr[] = [-1, -3, -10, 0, 6]`  
**Output:**  
`30`  
**Explanation:**  
The subarray with the maximum product is `{-3, -10}`.  
Product = `(-3) * (-10) = 30`.

#### Example 3
**Input:**  
`arr[] = [2, 3, 4]`  
**Output:**  
`24`  
**Explanation:**  
All elements are positive, so the max product is the product of all elements: `2 * 3 * 4 = 24`.

---

## Approach

To solve this, we use the concept of **Kadane’s Algorithm**, but with a twist:
- Since we are dealing with both **negative and positive numbers**, and multiplication of two negative numbers gives a positive, we must track both:
  - **maxProd** (maximum product ending at current index)
  - **minProd** (minimum product ending at current index)

### Steps:
1. Initialize `maxProd`, `minProd`, and `result` to the first element.
2. Traverse the array from the second element.
3. At each index:
   - Calculate temporary maximum as previous `maxProd`.
   - Update `maxProd` = max(current element, maxProd * current element, minProd * current element)
   - Update `minProd` = min(current element, tempMax * current element, minProd * current element)
   - Update `result` = max(`result`, `maxProd`)

This keeps track of both ends, and updates the answer dynamically.

---

## Java Code

```java
class Solution {
    // Function to find maximum product subarray
    int maxProduct(int[] arr) {
        int n = arr.length;
        int maxProd = arr[0];
        int minProd = arr[0];
        int result = arr[0];

        for (int i = 1; i < n; i++) {
            int tempMax = maxProd;

            maxProd = Math.max(arr[i], Math.max(maxProd * arr[i], minProd * arr[i]));
            minProd = Math.min(arr[i], Math.min(tempMax * arr[i], minProd * arr[i]));

            result = Math.max(result, maxProd);
        }

        return result;
    }
}

Time & Space Complexity
Time Complexity: O(n)
Space Complexity: O(1) (only constant variables used)

