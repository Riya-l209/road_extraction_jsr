## ✅ Day 2 - Move All Zeroes to End

**🧠 Problem Link:**  
[Move All Zeroes to End - GeeksforGeeks](https://www.geeksforgeeks.org/move-zeroes-end-array/)

---

### 📝 Problem Statement:

You are given an array `arr[]` of non-negative integers. Your task is to **move all the zeros in the array to the right end** while maintaining the **relative order** of the non-zero elements.

This operation must be performed **in-place**, meaning you should **not use extra space** for another array.

---

### 📌 Examples:

Input: [1, 2, 0, 4, 3, 0, 5, 0]
Output: [1, 2, 4, 3, 5, 0, 0, 0]

Input: [10, 20, 30]
Output: [10, 20, 30]

Input: [0, 0]
Output: [0, 0]

yaml
Copy
Edit

---

### 💡 Approach:

- Use a variable `count` to track the position of the next non-zero element.
- Traverse the array:
  - If the current element is not zero, place it at `arr[count]` and increment `count`.
- After placing all non-zero elements, fill the remaining positions in the array with 0s.
- This maintains the relative order of non-zero elements and moves all zeros to the end in-place.

---

### 🔎 Time and Space Complexity:

- **Time Complexity:** O(n)
- **Space Complexity:** O(1) – done in-place

---

### 👨‍💻 Code (Java):

```java
class Solution {
    void pushZerosToEnd(int[] arr) {
        int n = arr.length;
        int count = 0;

        for (int i = 0; i < n; i++) {
            if (arr[i] != 0) {
                arr[count++] = arr[i];
            }
        }

        while (count < n) {
            arr[count++] = 0;
        }
    }

    public static void main(String[] args) {
        Solution sol = new Solution();

        int[] arr1 = {1, 2, 0, 4, 3, 0, 5, 0};
        sol.pushZerosToEnd(arr1);
        System.out.println(java.util.Arrays.toString(arr1));

        int[] arr2 = {10, 20, 30};
        sol.pushZerosToEnd(arr2);
        System.out.println(java.util.Arrays.toString(arr2));

        int[] arr3 = {0, 0};
        sol.pushZerosToEnd(arr3);
        System.out.println(java.util.Arrays.toString(arr3));
    }
}
✅ Output:
csharp
Copy
Edit
[1, 2, 4, 3, 5, 0, 0, 0]
[10, 20, 30]
[0, 0]
✨ What I Learned:
Efficient in-place algorithms

How to preserve the relative order of elements while rearranging

Mastered array traversal and conditional placement logic