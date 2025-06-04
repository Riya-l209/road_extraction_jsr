# 🔍 Search Pattern (KMP Algorithm)

## 🧠 Problem Statement

Given two strings, one is a **text string `txt`** and the other is a **pattern string `pat`**. The task is to **find all occurrences of the pattern in the text** using **KMP Algorithm** and return their starting indices using **0-based indexing**.

If no occurrence exists, return an **empty list**.

---

## 🧪 Examples

### Example 1:
Input:
txt = "abcab", pat = "ab"

Output:
[0, 3]

Explanation:
"ab" occurs at indices 0 and 3.

### Example 2:
Input:
txt = "abesdu", pat = "edu"

Output:
[]
Explanation:
Pattern not present in text.


### Example 3:
Input:
txt = "aabaacaadaabaaba", pat = "aaba"

Output:
[0, 9, 12]

Explanation:
Pattern "aaba" occurs at indices 0, 9 and 12.

---

## ✅ Constraints
- 1 ≤ `txt.length()` ≤ 10⁶  
- 1 ≤ `pat.length()` < `txt.length()`  
- All characters are lowercase English alphabets

---

## 💡 Approach: KMP Algorithm (Knuth-Morris-Pratt)

### 🔹 Step 1: Preprocessing – Compute LPS Array

The **LPS (Longest Prefix which is also Suffix)** array helps in skipping unnecessary comparisons.  
It tells us the longest prefix of the pattern that is also a suffix at every position.

### 🔹 Step 2: Pattern Search Using LPS

Traverse the text:
- If characters match, move both pointers.
- If a complete match is found, record the index and reset `j` using the LPS array.
- If mismatch occurs:
  - If `j != 0`, update `j` to `lps[j-1]`
  - Else, just move `i`

---

## 🧾 Java Code

```java
import java.util.ArrayList;

class Solution {

    ArrayList<Integer> search(String pat, String txt) {
        ArrayList<Integer> result = new ArrayList<>();
        int n = txt.length();
        int m = pat.length();

        // Step 1: Create LPS array
        int[] lps = computeLPSArray(pat);

        // Step 2: KMP pattern search
        int i = 0, j = 0;
        while (i < n) {
            if (txt.charAt(i) == pat.charAt(j)) {
                i++;
                j++;
            }

            if (j == m) {
                result.add(i - j); // pattern found
                j = lps[j - 1];    // continue search
            } else if (i < n && txt.charAt(i) != pat.charAt(j)) {
                if (j != 0) {
                    j = lps[j - 1];
                } else {
                    i++;
                }
            }
        }

        return result;
    }

    private int[] computeLPSArray(String pat) {
        int m = pat.length();
        int[] lps = new int[m];
        int len = 0;
        int i = 1;
        lps[0] = 0;

        while (i < m) {
            if (pat.charAt(i) == pat.charAt(len)) {
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
Metric	Complexity
Time (Preprocessing)	O(m)
Time (Searching)	O(n)
Total Time	O(n + m)
Space (LPS Array)	O(m)
Auxiliary Space	O(1) (excluding result list)