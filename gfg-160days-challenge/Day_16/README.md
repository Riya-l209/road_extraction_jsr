# 🔤 Anagram Checker - Java Solution

## 📝 Problem Statement

Given two strings `s1` and `s2` consisting of **lowercase characters**, check whether the two strings are **anagrams** of each other or not.

An **anagram** of a string is another string that contains the **same characters with the same frequency**, but **in a different order**.

> Both `s1` and `s2` are guaranteed to be **non-empty**.

---

### ✅ Examples

#### Example 1:
Input: s1 = "geeks", s2 = "kseeg"
Output: true
Explanation: Both strings have the same characters with the same frequency.

#### Example 2:
Input: s1 = "allergy", s2 = "allergic"
Output: false
Explanation: Characters are not the same.

#### Example 3:
Input: s1 = "g", s2 = "g"
Output: true

---

### 📌 Constraints

- 1 ≤ `s1.length()`, `s2.length()` ≤ 10⁵
- `s1` and `s2` contain only lowercase English letters (a–z)

---

## 💡 Approach

We use a **frequency counting technique** for all 26 lowercase letters. This method avoids sorting (which is O(n log n)) and works in **linear time** O(n).

### Steps Involved:

1. **Edge Case Check**: If lengths of `s1` and `s2` are different → return `false`.
2. **Create a Frequency Array**: Initialize an array `count[26]` for letters a–z.
3. **Update Frequencies**:
   - Traverse both strings simultaneously:
     - Increment count for `s1.charAt(i)`
     - Decrement count for `s2.charAt(i)`
4. **Final Check**: If any index in `count[]` is not zero → return `false`. Else, return `true`.

---

## 🧠 Intuition

If two strings are anagrams:
- Every character should occur the same number of times in both.
- Counting and balancing characters while traversing both strings is optimal.

---

## 🧮 Time and Space Complexity

| Complexity | Value       |
|------------|-------------|
| Time       | O(n)        |
| Space      | O(1) (constant 26 letters) |

---

## 👨‍💻 Java Code

```java
class Solution {
    // Function is to check whether two strings are anagram of each other or not.
    public static boolean areAnagrams(String s1, String s2) {
        // Step 1: Length check
        if (s1.length() != s2.length()) {
            return false;
        }

        // Step 2: Frequency array for 26 lowercase characters
        int[] count = new int[26];

        // Step 3: Count characters
        for (int i = 0; i < s1.length(); i++) {
            count[s1.charAt(i) - 'a']++;
            count[s2.charAt(i) - 'a']--;
        }

        // Step 4: Verify all counts are zero
        for (int i = 0; i < 26; i++) {
            if (count[i] != 0) {
                return false;
            }
        }

        return true;
    }

    // Sample usage
    public static void main(String[] args) {
        System.out.println(areAnagrams("geeks", "kseeg"));      // true
        System.out.println(areAnagrams("allergy", "allergic")); // false
        System.out.println(areAnagrams("g", "g"));              // true
    }
}
✅ Output
true
false
true

Compare sorted versions

Time Complexity: O(n log n)

Less optimal for large inputs compared to frequency counting.

🔚 Conclusion
This solution provides an efficient and scalable way to check for anagrams using constant extra space and linear time, making it ideal for large inputs (up to 10⁵ characters).