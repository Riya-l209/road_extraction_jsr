# 🔁 Check If Two Strings Are Rotations of Each Other

## 🧩 Problem Statement

You are given two strings `s1` and `s2` of **equal length**. Determine if `s2` is a **rotation** of `s1`.

### 🔹 Rotations

A string is said to be a rotation of another if it can be obtained by performing any number of **left or right rotations**.

---

## ✅ Examples

### Example 1:
Input: s1 = "abcd", s2 = "cdab"
Output: true
Explanation: After 2 right rotations, s1 becomes "cdab".

### Example 2:
Input: s1 = "aab", s2 = "aba"
Output: true
Explanation: After 1 left rotation, s1 becomes "aba".


### Example 3:
Input: s1 = "abcd", s2 = "acbd"
Output: false
Explanation: No rotation of s1 results in s2.

---

## 📌 Constraints

- 1 ≤ `s1.length()`, `s2.length()` ≤ 10⁵  
- All characters are **lowercase English letters**

---

## 🚀 Optimized Approach

### 🔍 Observation:
If `s2` is a rotation of `s1`, then `s2` must be a **substring** of `s1 + s1`.
To efficiently check for substring existence, we use the **Knuth-Morris-Pratt (KMP)** algorithm to avoid time limit exceeded (TLE) errors on large input.

---

## 🧠 Time and Space Complexity

- **Time Complexity:** O(n), where n = length of the strings
- **Space Complexity:** O(n), for the LPS array used in KMP

---

## 💡 Java Code (Optimized using KMP)

```java
class Solution {
    public static boolean areRotations(String s1, String s2) {
        if (s1.length() != s2.length()) {
            return false;
        }

        String combined = s1 + s1;
        return kmpSearch(combined, s2);
    }

    private static boolean kmpSearch(String text, String pattern) {
        int[] lps = computeLPSArray(pattern);
        int i = 0, j = 0;

        while (i < text.length()) {
            if (pattern.charAt(j) == text.charAt(i)) {
                i++;
                j++;
            }

            if (j == pattern.length()) {
                return true;
            } else if (i < text.length() && pattern.charAt(j) != text.charAt(i)) {
                if (j != 0)
                    j = lps[j - 1];
                else
                    i++;
            }
        }

        return false;
    }

    private static int[] computeLPSArray(String pattern) {
        int[] lps = new int[pattern.length()];
        int len = 0;
        int i = 1;

        while (i < pattern.length()) {
            if (pattern.charAt(i) == pattern.charAt(len)) {
                len++;
                lps[i] = len;
                i++;
            } else {
                if (len != 0) {
                    len = lps[len - 1];
                } else {
                    lps[i] = 0;
                    i++;
                }
            }
        }

        return lps;
    }
}

🧪 Test Cases
areRotations("abcd", "cdab");  // true
areRotations("aab", "aba");    // true
areRotations("abcd", "acbd");  // false
areRotations("aaaa", "aaaa");  // true