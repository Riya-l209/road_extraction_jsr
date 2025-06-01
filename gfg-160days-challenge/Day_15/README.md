# 📅 Day 15: Add Binary Strings

## 📝 Problem Statement

Given two binary strings `s1` and `s2` consisting only of `0`s and `1`s, return their sum as a **binary string**.  
The result must **not contain leading zeroes**.

> ⚠️ Note: Input strings may contain leading zeros, but the result **should not**.

---

## 🔗 Problem Link

[GeeksforGeeks - Add Binary Strings](https://www.geeksforgeeks.org/problems/add-binary-strings3805/1)

---

## 🔐 Constraints

- `1 ≤ |s1|, |s2| ≤ 10^5`
- Strings contain only `'0'` and `'1'`

---

## 🧪 Examples

### Example 1  
**Input:**  
`s1 = "1101"`, `s2 = "111"`  
**Output:**  
`10100`  
**Explanation:**  
1101

111

10100

---

### Example 2  
**Input:**  
`s1 = "00100"`, `s2 = "010"`  
**Output:**  
`110`  
**Explanation:**  
100

10

---

## ✅ Approach: Binary Addition with Carry (Two-Pointer Method)

---

## 🧠 Intuition

Binary addition works like decimal addition — but base 2:

- 0 + 0 = 0  
- 0 + 1 = 1  
- 1 + 1 = 10 (carry = 1)  
- 1 + 1 + 1 = 11 (sum = 1, carry = 1)

We use **two pointers**, starting from the end of both strings and move backward, maintaining a carry.

---

## 🧩 Steps Involved

1. Initialize two pointers `i` and `j` to the last indices of `s1` and `s2`.
2. Initialize `carry = 0` and a `StringBuilder` for the result.
3. Loop while either string has characters left or `carry > 0`:
   - Add digit from `s1` if `i >= 0`
   - Add digit from `s2` if `j >= 0`
   - Add `carry`
   - Calculate result digit: `sum % 2`
   - Update carry: `sum / 2`
   - Append digit to result
4. Reverse the result.
5. Remove leading zeroes (if any).
6. Return final string.

---

## 💻 Java Code

```java
class Solution {
    public String addBinary(String s1, String s2) {
        int n1 = s1.length(), n2 = s2.length();
        StringBuilder result = new StringBuilder();
        int carry = 0;

        int i = n1 - 1, j = n2 - 1;

        while (i >= 0 || j >= 0 || carry == 1) {
            int sum = carry;

            if (i >= 0) sum += s1.charAt(i--) - '0';
            if (j >= 0) sum += s2.charAt(j--) - '0';

            result.append(sum % 2);
            carry = sum / 2;
        }

        result.reverse();

        // Remove leading zeros
        while (result.length() > 1 && result.charAt(0) == '0') {
            result.deleteCharAt(0);
        }

        return result.toString();
    }
}

⏱️ Time and Space Complexity
Time Complexity: O(max(n, m))
(We process each digit from both strings once)

Space Complexity: O(max(n, m))
(To store the result)