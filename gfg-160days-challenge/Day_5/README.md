# 🚀 GFG 160-Day Challenge — Day 4

## 🧠 Problem: Next Permutation

**Difficulty**: Medium  
**Link**: [Next Permutation on GeeksforGeeks](https://practice.geeksforgeeks.org/problems/next-permutation5226/1)

### 📝 Problem Statement

Given an array of integers `arr[]` representing a permutation, implement the next permutation that rearranges the numbers into the lexicographically next greater permutation.

If no such permutation exists, rearrange the numbers into the **lowest possible order** (i.e., sorted in ascending order).

---

### 📚 Examples

#### Example 1:
Input: arr[] = {2, 4, 1, 7, 5, 0}
Output: {2, 4, 5, 0, 1, 7}

#### Example 2:
Input: arr[] = {3, 2, 1}
Output: {1, 2, 3}


#### Example 3:
Input: arr[] = {1, 2, 3}
Output: {1, 3, 2]

---

## 💡 Approach

To find the **next permutation**, we follow these steps:
1. **Find the first decreasing element** from the right (let’s call its index `i`).  
   This is the element which breaks the increasing trend from the end.
2. **Find the element just larger than `arr[i]`** from the right side (index `j`), and swap `arr[i]` and `arr[j]`.
3. **Reverse the sub-array from `i+1` to the end of the array** to get the smallest sequence.
4. If no such `i` exists, the array is in descending order and we simply reverse the entire array to get the lowest permutation.

---

## 🧑‍💻 Java Code

```java
class Solution {
    void nextPermutation(int[] arr) {
        int n = arr.length;
        int i = n - 2;

        // Step 1: Find the first element from the right that is smaller than next
        while (i >= 0 && arr[i] >= arr[i + 1]) {
            i--;
        }

        if (i >= 0) {
            int j = n - 1;
            // Step 2: Find the element just larger than arr[i] and swap
            while (arr[j] <= arr[i]) {
                j--;
            }
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }

        // Step 3: Reverse the suffix starting at i+1
        int left = i + 1, right = n - 1;
        while (left < right) {
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--;
        }
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        int[] arr = {2, 4, 1, 7, 5, 0};
        sol.nextPermutation(arr);

        System.out.print("Next Permutation: ");
        for (int num : arr)
            System.out.print(num + " ");
        System.out.println();
    }
}

🛠️ How to Run
👉 Requirements
Java installed

▶️ Compile and Run

javac Solution.java
java Solution
✅ Output

Next Permutation: 2 4 5 0 1 7
