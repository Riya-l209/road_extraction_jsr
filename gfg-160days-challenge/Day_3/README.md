## ✅ Day 3 - Reverse an Array

**🧠 Problem Link:**  
[Reverse an Array - GeeksforGeeks](https://www.geeksforgeeks.org/write-a-program-to-reverse-an-array-or-string/)

---

### 📝 Problem Statement:

You are given an array of integers `arr[]`. Your task is to **reverse the given array in place** (i.e., without using any extra space).

---

### 📌 Examples:

Input: [1, 4, 3, 2, 6, 5]
Output: [5, 6, 2, 3, 4, 1]

Input: [4, 5, 2]
Output: [2, 5, 4]

Input: [1]
Output: [1]


---

### 🔐 Constraints:

- 1 ≤ arr.length ≤ 10⁵  
- 0 ≤ arr[i] ≤ 10⁵

---

### 💡 Approach:

- Use **two-pointer** technique:
  - One pointer at the beginning (`start`)
  - Another at the end (`end`)
- Swap the elements at these pointers.
- Move `start` forward and `end` backward.
- Continue until `start < end`.

This way, the array is reversed **in-place** with **O(1)** space.


### 🔎 Time and Space Complexity:

- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

### 👨‍💻 Code (Java):
class Solution {
    void reverseArray(int[] arr) {
        int start = 0, end = arr.length - 1;

        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;

            start++;
            end--;
        }
    }

    public static void main(String[] args) {
        Solution sol = new Solution();

        int[] arr1 = {1, 4, 3, 2, 6, 5};
        sol.reverseArray(arr1);
        System.out.println(java.util.Arrays.toString(arr1));

        int[] arr2 = {4, 5, 2};
        sol.reverseArray(arr2);
        System.out.println(java.util.Arrays.toString(arr2));

        int[] arr3 = {1};
        sol.reverseArray(arr3);
        System.out.println(java.util.Arrays.toString(arr3));
    }
}

✅ Output:
[5, 6, 2, 3, 4, 1]
[2, 5, 4]
[1]

✨ What I Learned:
Mastered the two-pointer technique.
Practiced in-place array manipulation.
Learned to reverse arrays without using extra space.

