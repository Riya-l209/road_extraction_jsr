# 🚀 Day 4 - Rotate Array by D Elements (Left Rotation)

👩‍💻 **Language:** Java  
📚 **Platform:** GeeksforGeeks (GFG 160 Days Challenge)  
🧠 **Topic:** Arrays - Rotation

---

## 📘 Problem Statement

Given an array `arr[]`. Rotate the array to the left (**counter-clockwise**) by `d` steps, where `d` is a positive integer.  
Do the mentioned change in the **array in-place**.  
**Note:** Consider the array as **circular**.

---

## 🧾 Examples

#### ➤ Example 1:
Input: arr[] = [1, 2, 3, 4, 5], d = 2
Output: [3, 4, 5, 1, 2]
Explanation: After 2 rotations -> 3 4 5 1 2

shell
Copy
Edit

#### ➤ Example 2:
Input: arr[] = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20], d = 3
Output: [8, 10, 12, 14, 16, 18, 20, 2, 4, 6]
Explanation: After 3 rotations -> 8 10 12 14 16 18 20 2 4 6

shell
Copy
Edit

#### ➤ Example 3:
Input: arr[] = [7, 3, 9, 1], d = 9
Output: [3, 9, 1, 7]
Explanation: 9 % 4 = 1, effectively rotate by 1 => 3 9 1 7

pgsql
Copy
Edit

---

## 🔐 Constraints

- 1 ≤ `arr.length`, `d` ≤ 10⁵  
- 0 ≤ `arr[i]` ≤ 10⁵  

---

## 🧩 Approach: Reversal Algorithm

🔄 Rotate the array in **three steps**:

1. Reverse the first `d` elements  
2. Reverse the remaining `n-d` elements  
3. Reverse the whole array

➡️ Time Complexity: **O(n)**  
➡️ Space Complexity: **O(1)** (In-place)

---

## ☕ Java Code

```java
// User function template for Java

class Solution {
    // Function to rotate an array by d elements in counter-clockwise direction.
    void rotateArr(int arr[], int d) {
        int n = arr.length;
        d = d % n;  // Handle if d > n
        reverse(arr, 0, d - 1);
        reverse(arr, d, n - 1);
        reverse(arr, 0, n - 1);
    }

    void reverse(int arr[], int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
}

class Main {
    public static void main(String[] args) {
        int arr[] = {1, 2, 3, 4, 5};
        int d = 2;
        int n = arr.length;
        Solution sol = new Solution();
        sol.rotateArr(arr, d);
        for (int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
📝 My Takeaways
Practiced in-place operations using reverse technique.

Understood how to handle cases when d > n using modulo.

Gained confidence in manipulating array indices safely and efficiently.

#Java #GFG160DaysChallenge #Day4 #ArrayRotation #DSA #CodingDaily #LeetGFGGrind