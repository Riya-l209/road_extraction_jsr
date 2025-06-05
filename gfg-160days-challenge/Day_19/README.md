# 🧩 Min Chars to Add for Palindrome

**Problem Link:**  
[Min Chars to Add for Palindrome – GeeksforGeeks](https://www.geeksforgeeks.org/problems/minimum-characters-to-be-added-at-front-to-make-string-palindrome/1)

---

## 📘 Problem Statement

Given a string `s`, the task is to find the **minimum characters to be added at the front** to make the string a palindrome.

> A palindrome string is a sequence of characters that reads the same forward and backward.

---

## 📌 Examples

### Example 1:
**Input:**  
`s = "abc"`  
**Output:**  
`2`  
**Explanation:**  
Add `'b'` and `'c'` at the front to make it `"cbabc"`.

---

### Example 2:
**Input:**  
`s = "aacecaaa"`  
**Output:**  
`2`  
**Explanation:**  
Add 2 `'a'`s at the front to make it `"aaacecaaa"`.

---

## ✅ Constraints

- `1 ≤ s.length ≤ 10⁶`

---

## 🔍 Approach

We use the concept of **KMP (Knuth-Morris-Pratt)** algorithm's **LPS (Longest Prefix Suffix)** array:

1. **Reverse the input string** and append it to the original string using a special separator (`$`) to avoid overlapping.
2. Compute the **LPS array** for this new combined string.
3. The number of characters to be added in front =  
   `original string length - last value in LPS array`.

---

## 🧠 Algorithm Steps

1. Reverse the original string.
2. Concatenate original + `$` + reversed string.
3. Build the LPS array for this concatenated string.
4. Result = `original.length - LPS[concatenated.length - 1]`.

---

## 🧾 Code (Java)

```java
class Solution {
    public static int minChar(String s) {
        // Reverse the string
        StringBuilder rev = new StringBuilder(s).reverse();
        
        // Combine original + $ + reversed
        String combined = s + "$" + rev;
        
        // Get LPS array
        int[] lps = computeLPS(combined);
        
        // Return the number of characters to add
        return s.length() - lps[combined.length() - 1];
    }

    private static int[] computeLPS(String str) {
        int n = str.length();
        int[] lps = new int[n];
        int len = 0, i = 1;
        
        while (i < n) {
            if (str.charAt(i) == str.charAt(len)) {
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


🧮 Time & Space Complexity
Time Complexity: O(N), where N is the length of the concatenated string.
Space Complexity: O(N), for the LPS array.

🏁 Output
Input	Output	Modified Palindrome
"abc"	2	"cbabc"
"aacecaaa"	2	"aaacecaaa"