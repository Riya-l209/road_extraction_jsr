# 💻 Day 3 - Reverse an Array

**Difficulty:** Easy  
**Average Time:** 5 mins  
**Platform:** GeeksforGeeks  
**Points Earned:** 2 ✅

---

## 📘 Problem Statement:

You are given an array of integers `arr[]`. Your task is to **reverse the given array**.

> 🔒 Note: Modify the array **in place** without using extra space.

---

## 🔍 Examples:

### Example 1:
Input: arr = [1, 4, 3, 2, 6, 5]
Output: [5, 6, 2, 3, 4, 1]

shell
Copy
Edit

### Example 2:
Input: arr = [4, 5, 2]
Output: [2, 5, 4]

shell
Copy
Edit

### Example 3:
Input: arr = [1]
Output: [1]

yaml
Copy
Edit

---

## 📌 Constraints:

- 1 ≤ arr.length ≤ 10⁵  
- 0 ≤ arr[i] ≤ 10⁵

---

## 🧠 Approach:

- Use the **two-pointer technique**:
  - Initialize `left` at index 0 and `right` at the last index.
  - Swap `arr[left]` and `arr[right]`.
  - Increment `left`, decrement `right`.
  - Repeat until `left < right`.

This performs the reversal **in-place** using **constant space**.

---

## ⏱️ Time and Space Complexity:

- **Time Complexity:** O(n)  
- **Space Complexity:** O(1)

---

## 👨‍💻 Code (Java):

```java
class Solution {
    public void reverseArray(int arr[]) {
        // code here
        int left = 0, right = arr.length - 1;
        while (left < right) {
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--;
        }
    }
}
✅ Output for Test Cases:
java
Copy
Edit
Input:  [1, 4, 3, 2, 6, 5]
Output: [5, 6, 2, 3, 4, 1]

Input:  [4, 5, 2]
Output: [2, 5, 4]

Input:  [1]
Output: [1]
📚 What I Learned:
How to reverse an array in-place using two-pointer method.

Importance of modifying arrays without using extra memory.

Practiced classic array problems that are commonly asked in interviews.